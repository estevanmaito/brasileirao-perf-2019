# Botafogo

[Site](https://www.botafogo.com.br/). [WebPageTest](https://www.webpagetest.org/result/190422_JD_1a258ae4286bec75f4d0f74ba1b14b15/).

## Primeiro tempo

![](imgs/filmstrip-first-view-run-1.png)

**13.2s sem nada na tela**, e o conteúdo vai carregando até que a página fica **interativa a partir de 17.7s**. Esse tempo é baseado no que tanto o Lighthouse quanto o WebPageTest informam, já que **a página não é responsiva** e não tem como ver se o conteúdo realmente está ali. Em 2019.

![](imgs/first-view-run-1.png)

O primeiro ponto que você percebe quando bate o olho nesse relatório é que todas as requisições têm um traçado colorido, ausente nos relatórios anteriores. É o mesmo efeito do site do Avaí, que não tem o cabeçalho `keep alive` que faz com que o servidor "apague" a conexão a cada recurso e cada um precisa refazer todo o processo. Aliado a isso, **o HTTP/1 usado não deixa mais de uma conexão acontecer simultaneamente**, aí entra tudo numa fila.

De modo geral, **os arquivos CSS e JS não estão minificados e o servidor os serve sem gzip**. Os dois primeiros, e principais arquivos **CSS têm 45% e 64.8% não utilizados**, respectivamente.

*Only 90s kids will remember*: este site é compatível com RealPlayer e IE8-.

A renderização ainda sofre com o bloqueia de scripts no `head` sem `defer`.

## Segundo tempo

![](imgs/filmstrip-second-view-run-1.png)

Na segunda etapa são **5s sem nada na tela**, até que **aos 10.3s temos interatividade**, de acordo com o relatório, já que temos aqui o mesmo problema com a **falta de responsividade** da página.

![](imgs/second-view-run-1.png)

Mais uma vez o navegador salva o dia cacheando o conteúdo por conta própria, já que não temos cache aqui. É possíve ver ainda que a partir do momento que temos conteúdo na tela, a thread principal fica travada dos 5 aos 8.2s aproximadamente.

## Custo

São 7.7 MB baixados (6 MB de imagens). Num plano de 100 MB a R$ 1,49/dia, acessar este site uma vez por dia custaria R$ 3,44 por mês, pouco mais de 2 dias de internet.

## Imagens

A imagem do treinador, usada no slider do header mede **1800x891px e tem 1.2 MB, teria 78 KB em JPEG (93% menor) ou 46.9 KB em WebP** se fosse comprimida.

A imagem do estádio mede 644x226px e pesa 180 KB, **teria 66.7 KB em JPEG (63% menor) ou 50.1 KB em WebP, tendo escalado a largura para 1000px**. [Veja os resultados](imgs/squoosh).

A *compressão das imagens* aliada ao *carregamento atrasado* delas (lazy loading) ajudaria no tamanho da página. A redução de requisições também é uma opção.

## Resultado

1. Atlético - 15.3s
1. Athletico - 17.4s
1. Botafogo - 28s *
1. Bahia - 56.8s
1. Avaí - 61.6s

Não é responsivo *

Muito tempo é perdido com configurações do servidor: HTTP/1 atrasa o download e a falta de um simples cabeçalho como `keep alive` adiciona tempo de conexão desnecessário a cada requisição. Carregamento adiantado das fontes, compressão de CSS e scripts, além destes últimos carregados com `defer`, ajudariam um pouco, mas não resolveriam o fato do site não ser responsivo.

Bom
- HTTPS

Ruim
- Sem keep alive
- Sem cache
- Sem gzip
- HTTP/1
- Sem minificação
- Compressão de imagens
- JS desnecessário
- CSS desnecessário
- Download atrasado de fontes
- Scripts bloqueiam renderização
- Muitas imagens
- Não é responsivo