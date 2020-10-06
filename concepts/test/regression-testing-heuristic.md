Fonte: http://karennicolejohnson.com/2009/11/a-heuristic-for-regression-testing/

Em 2009, foi publicada a seguinte heurística para testes de regressão: RCRCRC

- Recent
- Core
- Risk
- Configuration
- Repaired
- Chronic

Basicamente, cada item significa (original, sem tradução):

- Recent: new features, new areas of code are more vulnerable
- Core: essential functions must continue to work
- Risk: some areas of an application pose more risk
- Configuration sensitive: code that’s dependent on environment settings can be vulnerable
- Repaired: bug fixes can introduce new issues
- Chronic: some areas in an application may be perpetually sensitive to breaking

Acredito que todos itens ainda fazem sentido, sendo automatizado ou não.

**Versão traduzida/adaptada**:

- Recentes: novas funcionalidades e partes do código são mais vulneráveis
- Core (preferi manter): funções essenciais devem continuar funcionando
- Risco: algumas área da aplicação possuem maior risco
- Sensível a configuração: o código que depende de configurações do ambiente pode ser vulnerável
- Reparos: correções de bugs podem introduzir novos problemas
- Crônico: áreas da aplicação que possuem histórico de serem sensíveis à quebra
