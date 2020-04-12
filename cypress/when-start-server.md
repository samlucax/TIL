https://docs.cypress.io/api/commands/server.html#State-between-tests

O Cypress permite o uso de routing e requests para monitorar requisições, criar mocks, preparar os dados antes de executar o teste, etc.

Para utilizar estes comandos, precisamos do `cy.server()`, mais ou menos assim:

```
// nao funciona
cy.route('alguma coisa')

// funciona
cy.server();
cy.route('alguma coisa')
```

Fica a pergunta: quando iniciar o server?

Segundo a documentação, o `cy.server não mantém estado entre os testes`.

Ou seja, se iniciarmos em um hook que executa uma vez antes de todos os testes, ele funcionará apenas no primeiro teste da suite.

```
// before all hook
cy.server()

// tests
test1 - route funciona normalmente
test2 - server ja "morreu", route nao irá funcionar.
```

Uma alternativa, é iniciar o `cy.server` antes de cada teste, utilizando um hook para tal (ex.: `beforeEach`, do Mocha).

```
// before all hook
cy.server()

// tests
test1 - route funciona normalmente
test2 - server antigo morre, nasce outro, route funciona normalmente
```




