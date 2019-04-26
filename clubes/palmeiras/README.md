# Palmeiras

[Site](http://www.palmeiras.com.br/home/). [WebPageTest](https://www.webpagetest.org/result/190422_B3_5bf545f43ebcd29db33a020dc16bd2cf/).

## Primeiro tempo

![](imgs/filmstrip-first-view-run-1.png)

**Após 3.6s de tela branca** a renderização começa, porém, o **site não é responsivo**. Como interativo vou considerar **o primeiro estado em que o texto é legível, em 8.2s**.

![](imgs/first-view-run-1.png)

O WebPageTest registrou 376 requisições, que é o que eu vou considerar, porém **o CDT no desktop capturou 479, 139 delas scripts**.

![](imgs/ads.png)

Em determinado ponto, 10 **scripts de anúncios** são carregados e executados. Iguais a estes existem outros entre as requisições.

A maioria dos scripts e CSS **não estão minificados**, porém o conteúdo vem comprimido pelo gzip. Os arquivo de JavaScript estão posicionados no `head`, porém sem `defer`, o que atrapalha a renderização, além do fato de que alguns geram outras requisições, que baixam e executam outros scripts.

Em determinado momento (linha 205 com um script imenso), até o player da Globo é baixado, contendo 425.6 KB comprimido e 1.4 MB no final das contas.

As fontes (10 variações de Open Sans) são requisitadas por um `link` a parte e poderiam se beneficiar do `preload`.

Ao todo, são 91 conexões e reconexões entre navegador e servidores.

## Segundo tempo

![](imgs/filmstrip-second-view-run-2.png)

Ainda que, aparentemente, o site pareça completo aos 6.6s, **a thread principal está bloqueada até os 25.3s**.

![](imgs/second-view-run-2.png)

Ainda que o cache do site seja simbólico (2 horas), os arquivos próprios estão sendo servidos a partir dele, só que ainda tem 127 conexões a serem feitas, em sua **maioria para servidores de anúncio**.

Os quase 140 scripts baixados anteriormente, agora bloqueiam a thread por praticamente 22s.

A estratégia que o Palmeiras adotou para promover o próprio conteúdo é usar ferramentas de terceiros (Google Ads), o que cobra um preço exorbitante.

Praticamente todos os outros clubes promovem planos de associação ou produtos de suas lojas, porém o fazem usando banners e sliders próprios, o que permite que a imagem seja veiculada mesmo com ad blockers.

## Custo

São 21.1 MB baixados (17.2 MB de imagens). Num plano de 100 MB a R$ 1,49/dia, acessar este site uma vez por dia custaria R$ 9,43 por mês, mais de 6 dias de internet.

## Imagens

A imagem de um dos jogadores do carousel mede 581x760px pesando 617 KB em PNG. **Comprimida teria 294 KB em PNG (52% menor) ou 33.7 KB em WebP.**

Uma imagem de uma notícia mede1498x843px pesando 691 KB. Após a compressão fica com 68.4 KB em JPEG (90% menor) ou 42.1 KB em WebP.

[Veja os resultados](imgs/squoosh).

Compressão, carregamento atrasado (lazy load) e um possível carregamento de imagens em tamanhos específicos para mobile ajudariam a diminuir a carga das imagens neste site.

## Resultado

1. Grêmio - 9.9s
1. Flamengo - 11.5s
1. Fortaleza - 13.2s
1. Cruzeiro - 13.4s
1. Ceará - 14.9s *
1. Atlético - 15.3s
1. Fluminense - 15.3s
1. Athletico - 17.4s
1. Chapecoense - 18.4s
1. Corinthians - 25.9s
1. CSA - 27.9s
1. Botafogo - 28s *
1. Internacional - 29.5s
1. Goiás - 30.3s
1. Palmeiras - 33.5s *
1. Bahia - 56.8s
1. Avaí - 61.6s

Não é responsivo *

No desktop, com Ad Blocker, foram 190 requisições a menos. Então minha dica de otimização para o site do Palmeiras é essa, usem bloqueador de anúncios ao visitar.

Bom
- gzip

Ruim
- Cache muito curto
- HTTP
- Compressão de imagens
- sem minificação
- HTTP/1
- JS desnecessário
- CSS desnecessário
- Download atrasado de JS
- Download atrasado de fontes
- Fontes de ícones
- Scripts bloqueiam renderização
- Muitas imagens
- Excesso de requisições