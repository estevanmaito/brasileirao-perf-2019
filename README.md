## Brasileirão de performance web 2019

Todo começo de campeonato brasileiro de futebol surgem diversas comparações entre elencos, caixa, títulos e até o momento dos clubes. Mas ninguém nunca pensou em comparar o site de cada time (não sei porquê...).

Meu objetivo, além de criar uma competição descontraída e inovadora, é mostrar erros e acertos nos sites dos times que amamos e que podem nos ajudar em nossas escolhas diárias. Se a melhor forma de aprender é errando, com o erro dos outros deve ser melhor ainda.

Já deixo avisado que **não estou julgando o trabalho dos desenvolvedores** envolvidos com cada site nem com suas escolhas. Só quem está inserido num projeto sabe o motivo de cada escolha, os pedidos do cliente para colocar 350 plugins inúteis ou o prazo para entrega.

Por fim, dei o meu melhor possível analisando 20 sites em 5 dias. Em alguns dias foram até 7 análises. Foi só o que eu fiz. Evidentemente que algum erro pode ter ocorrido (nesse caso você pode propor a correção [no GitHub](https://github.com/estevanmaito/brasileirao-perf-2019)) ou algum item pode ter sido deixado de fora. Fiz isso por hobby, me diverti, aprendi muita coisa e espero que possa te ajudar de alguma forma também.

## TL;DR

- Se você pretende ler apenas a análise de um clube ou do seu clube do coração, leia pelo menos a do Athletico, que é a primeira análise e eu expliquei melhor os meus métodos nela;

## Clubes

- [Athletico](/clubes/athletico)
- [Atlético](/clubes/atletico)
- [Avaí](/clubes/avai)
- [Bahia](/clubes/bahia)
- [Botafogo](/clubes/botafogo)
- [Ceará](/clubes/ceara)
- [Chapecoense](/clubes/chapecoense)
- [Corinthians](/clubes/corinthians)
- [Cruzeiro](/clubes/cruzeiro)
- [CSA](/clubes/csa)
- [Flamengo](/clubes/flamengo)
- [Fluminense](/clubes/fluminense)
- [Fortaleza](/clubes/fortaleza)
- [Goiás](/clubes/goias)
- [Grêmio](/clubes/gremio)
- [Internacional](/clubes/internacional)
- [Palmeiras](/clubes/palmeiras)
- [Santos](/clubes/santos)
- [São Paulo](/clubes/sao-paulo)
- [Vasco](/clubes/vasco)

## Especificações dos testes

A fim de tornar o ambiente de teste o mais parecido possível, utilizei o [WebPageTest](https://www.webpagetest.org) para a geração dos relatórios em uma **conexão 3G de um Moto G4** emulado. Se o resultado seria o mesmo em um Moto G4 real é outro assunto, pois o que importa é que todos os sites foram testados da mesma forma. Os relatórios de coverage e a seção de custos se baseiam em resultados do Chrome Dev Tools, executado no desktop, portanto, ainda que seja outro ambiente, todos foram analizados da mesma forma. Se houver alguma distorção, todos estão sujeitos a ela.

**Todos os testes foram executados 3 vezes** e apenas a mediana de cada um foi considerada, tanto para a primeira visita (primeiro tempo) quanto para a segunda (segundo tempo).

## Critérios

A pontuação/classificação se baseia **unicamente no tempo de carregamento da página**, calculada da seguinte forma:

Tr1 = Tempo até o carregamento na primeira visita

Tr2 = Tempo até o carregamento na segunda visita (cacheada)

Resultado = Tr1 + Tr2

Simples, **quanto menores os tempos de renderização em cada visita, menor o total, melhor a classificação do site**. Como carregamento considero a partir do momento que a página foi renderizada ou que pelos menos o conteúdo útil dela já possa ser consumido e a thread principal esteja desbloqueada.

## Itens avaliados

O resultado, medido pelo tempo até a renderização, isoladamente não ajuda a entender todo contexto e ambiente que resulta em determinado tempo de carregamento. Para ajudar, tanto o leitor quanto os desenvolvedores interessados, a melhorar os resultados, cada site será avaliado a partir dos seguintes itens, mas não exclusivamente:

- [ ] HTTPS
- [ ] HTTP/2
- [ ] Preload de fontes
- [ ] Gzip
- [ ] Minificação
- [ ] Compressão de imagens
- [ ] Renderização bloqueada por scripts
- [ ] Download atrasado de fontes
- [ ] Download atrasado de CSS
- [ ] Download atrasado de JS
- [ ] Cache
- [ ] CSS desnecessário
- [ ] JS desnecessário
- [ ] Fontes com baixa compressão
- [ ] Fontes de ícones
- [ ] Excesso de conexões

## Bônus

Como veremos, grande parte do peso dos sites se deve ao mau tratamento de imagens. Afim de tornar os benefícios da compressão de imagens mais óbvios, escolhi duas imagens de cada site para comprimir. As que eram maiores que 1000px foram redimensionadas, já que estamos falando de um ambiente mobile. Fiz isso usando o [Squoosh](https://squoosh.app), uma ferramenta online para compressão.

Além disso, como estamos falando de conexão 3G, calculei o custo de acessar cada site, uma vez por dia, durante um mês, num plano de 100 MB diários, com custo de R$ 1,49, da Vivo. Por que da Vivo? Foi o valor que eu encontrei mais rapidamente acessando várias operadoras. Levei em conta também o pior cenário possível, que seria sem cache.