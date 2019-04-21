## Clubes

- [Athletico](/clubes/athletico.md)
- [Atlético](/clubes/atletico.md)
- [Avaí](/clubes/avai.md)
- [Bahia](/clubes/bahia.md)
- [Botafogo](/clubes/botafogo.md)
- [CSA](/clubes/csa.md)
- [Ceará](/clubes/ceara.md)
- [Chapecoense](/clubes/chapecoense.md)
- [Corinthians](/clubes/corinthians.md)
- [Cruzeiro](/clubes/cruzeiro.md)
- [Flamengo](/clubes/flamengo.md)
- [Fluminense](/clubes/fluminense.md)
- [Fortaleza](/clubes/fortaleza.md)
- [Goiás](/clubes/goias.md)
- [Grêmio](/clubes/gremio.md)
- [Internacional](/clubes/internacional.md)
- [Palmeiras](/clubes/palmeiras.md)
- [Santos](/clubes/santos.md)
- [São Paulo](/clubes/sao-paulo.md)
- [Vasco](/clubes/vasco.md)

## Especificações dos testes

- Conexão 3G
- Moto G4 (emulado)
- [WebPageTest](https://www.webpagetest.org/)
- Relatórios do Chrome Dev Tools Network e Coverage
- 1 visita "crua"
- 2 visita cacheada

## Critérios

- A pontuação/classificação se baseia unicamente no tempo de carregamento da página, calculada da seguinte forma:

Tr1 = Tempo até o começo da renderização na primeira visita
Tr2 = Tempo até o começo da renderização na segunda visita (cacheada)

Resultado = Tr1 - Tr2

## Itens avaliados

O resultado, medido pelo tempo até a renderização, isoladamente não ajuda a entender todo contexto e ambiente que resulta em determinado tempo de carregamento. Para ajudar tanto o leitor quanto os desenvolvedores interessados a melhorar os resultados, cada site terá, pelo menos, os seguintes itens avaliados:

- [ ] HTTPS
- [ ] HTTP/2
- [ ] Preloading fonts
- [ ] Gzip
- [ ] Minification
- [ ] Image compression
- [ ] Render-blocking scripts
- [ ] Late-loading fonts
- [ ] Late-loading CSS
- [ ] Late-loading JS
- [ ] Cache control
- [ ] Unnecessary CSS
- [ ] Unnecessary JS
- [ ] Badly compressed fonts
- [ ] Poor image Compression
- [ ] Main thread lock-up
- [ ] Unstable render
- [ ] Icons fonts
- [ ] Too many HTTP connections
- [ ] Unstable layout
