https://docs.cypress.io/guides/guides/command-line.html#cypress-run-config-file-lt-config-file-gt
https://docs.cypress.io/guides/guides/command-line.html#cypress-open-config-file-lt-config-file-gt

Configurar a execução para multi-ambientes em um projeto é algo comum.
Com cypress, é possível fazer isso da seguinte forma:
1. criando arquivos de configuração por ambiente
2. setando o arquivo de configuração customizado no momento da execução. Serve para o open e para o run.

Cypress Open

`cypress open --config-file tests/cypress-config.json`

Cypress Run

`cypress run --config-file tests/cypress-config.json`

O padrão é o cypress.json. É possível abreviar o comando para `-C` .



Obs.: por algum motivo, em algum momento alguém sugeriu essa outra abordagem na documentação:
https://docs.cypress.io/api/plugins/configuration-api.html#Switch-between-multiple-configuration-files

Acredito que esta sugestão tenha vindo antes da option `--config-file` .
