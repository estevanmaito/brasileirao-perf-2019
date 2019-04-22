## Clubes

- [Athletico](/clubes/athletico)
- [Atlético](/clubes/atletico)
- [Avaí](/clubes/avai)
- [Bahia](/clubes/bahia)
- [Botafogo](/clubes/botafogo)
- [CSA](/clubes/csa)
- [Ceará](/clubes/ceara)
- [Chapecoense](/clubes/chapecoense)
- [Corinthians](/clubes/corinthians)
- [Cruzeiro](/clubes/cruzeiro) (timeout - repetir)
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

- Conexão 3G
- Moto G4 (emulado)
- [WebPageTest](https://www.webpagetest.org/)
- Relatórios do Chrome Dev Tools Network e Coverage
- 1 visita "crua"
- 2 visita cacheada

## Critérios

A pontuação/classificação se baseia unicamente no tempo de carregamento da página, calculada da seguinte forma:

Tr1 = Tempo até o começo da renderização na primeira visita

Tr2 = Tempo até o começo da renderização na segunda visita (cacheada)

Resultado = Tr1 - Tr2

## Itens avaliados

O resultado, medido pelo tempo até a renderização, isoladamente não ajuda a entender todo contexto e ambiente que resulta em determinado tempo de carregamento. Para ajudar, tanto o leitor quanto os desenvolvedores interessados, a melhorar os resultados, cada site terá, pelo menos, os seguintes itens avaliados:

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
- [ ] Main thread lock-up
- [ ] Unstable render
- [ ] Icons fonts
- [ ] Too many HTTP connections
- [ ] Unstable layout
