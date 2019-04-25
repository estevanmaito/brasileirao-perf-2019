# Fluminense

[Site](http://www.fluminense.com.br/site/). [WebPageTest](https://www.webpagetest.org/result/190422_NV_dca79f2f1c56c66a6b018d464f437278/).

## Primeiro tempo

![](imgs/filmstrip-first-view-run-1.png)

**5.7s de tela branca**, seguidos por uma rápida renderização, porém, **o conteúdo útil depende do JavaScript** e só aos 13.4s o slider do cabeçalho aparece.

![](imgs/first-view-run-1.png)

Este site só carrega um arquivo de script do próprio servidor, mas aparentemente é uma condensação de vários outros scripts, afinal são 210 KB **sem gzip nem cache**. Além disso, **64.2% nem é usado, assim como 90.2% do CSS**.

Como o servidor serve esses recursos em HTTP/1, até é bom que venha tudo num arquivo só, porém isso se reflete depois em tempo de download, execução e renderização, como dá pra ver pelas linhas 2 e 4, como nossos arquivos gigantes, porém únicos.

Bem breve, o script já está no `head` e poderia se beneficiar do `defer`, contato que houvesse uma solução para o banner que depende dele para renderizar (apresentar o primeiro slide fixo até carregar o script que dá interação e tudo mais). O CSS carregando o necessário, e o `preload` da fonte adiantaria o render.

## Segundo tempo

![](imgs/filmstrip-second-view-run-2.png)

**Em 1.2s a tela branca some** e já temos o começo da renderização. Aqui fica muito claro o que eu disse há pouco sobre o script que comando o slider do cabeçalho. Veja como as imagens dele estão empilhadas. Elas **só se reorganizam aos 1.9s, quando a thread é desbloqueada.**

![](imgs/second-view-run-2.png)

Com tão poucos recursos, o navegador que se deu ao trabalho de cachear tudo, já que não temos cache por parte do site (ainda que praticamente tudo pareça ter uma versão/timestamp), agora só precisa renderizar tudo. Ainda que a thread tenha ficado 0.6s travada, temos o site mais rápido a carregar até agora na segunda visita.

## Custo

São 1.9 MB baixados (1.4 MB de imagens). Num plano de 100 MB a R$ 1,49/dia, acessar este site uma vez por dia custaria R$ 0,85 por mês, praticamente meio dia de internet.

## Imagens

Um banner medindo 900x485px com 207 KB, teria, após a compressão, 120 KB em JPEG (42% menor) ou 88.8 KB em WebP.

O logo de um patrocinador tinha originalmente 144x119px e 13.9 KB, comprimido teria 2 KB em JPEG (86% menor) ou 1.16 KB em WebP, **sem redimensionamento**.

[Veja os resultados](imgs/squoosh).

## Resultado

1. Flamengo - 11.5s
1. Cruzeiro - 13.4s
1. Ceará - 14.9s *
1. Atlético - 15.3s
1. Fluminense - 15.3s
1. Athletico - 17.4s
1. Chapecoense - 18.4s
1. Corinthians - 25.9s
1. CSA - 27.9s
1. Botafogo - 28s *
1. Bahia - 56.8s
1. Avaí - 61.6s

* Não é responsivo

Como eu não estou aqui para avaliar conteúdo, vamos ao que interessa. O Fluminense empata com o Atlético e fica atrás pelo fato de ter menos itens na categoria "Bom". Ainda assim, marca um tempo baixo, que poderia ser melhor com a redução dos códigos não utilizados no CSS e JS, além do carregamento que não atrapalharia a renderização. Este passa a ser o site mais leve, o que poderia ser melhor também, houvesse gzip e compressão de imagens.

Bom
- Minificação

Ruim
- Sem gzip
- Sem cache
- HTTP
- HTTP/1
- Compressão de imagens
- JS desnecessário
- CSS desnecessário
- Download atrasado de JS
- Download atrasado de fontes
- Scripts bloqueiam renderização