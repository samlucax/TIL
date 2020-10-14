O Cypress é uma ferramenta um pouco grande e, acaba tomando bastante tempo de um build para baixar e instalar.

Usar uma estratégia de cache para salvar o binário que é baixado com certeza ajuda a reduzir o tempo de execução dos builds.

No meu caso, reduziu em 60% a etapa de instalar dependências.

Uma boa fonte para entender sobre Cache na Azure: https://github.com/cypress-io/cypress-example-kitchensink/issues/132

Exemplo para máquinas Windows:

```yaml
- task: CacheBeta@2
  inputs:
    key: 'cypress | $(Agent.OS) | package-lock.json'
    path: 'C:\Users\VssAdministrator\AppData\Local\Cypress'
    restoreKeys: 'cypress | $(Agent.OS) | package-lock.json'
  displayName: Cache Cypress
```

Importante destacar duas partes dessa config:

- O **CacheBeta@2** é uma ferramenta de cache disponibilizada pela Microsoft.
- O **path** recebeu um valor específico para Windows. Em máquinas linux, este valor pode mudar.
