Eventualmente é necessário criar dados que serão utilizados durante os testes.

No Cypress, podemos utilizar os comandos do `cy.request` por exemplo, para criar dados via api, para utilizar durante os testes de front.

Um exemplo de uso pode ser criando um usuário antes de um teste. Para isso, podemos fazer:
1. no arquivo `support/commands.js` criar uma `custom command`, que cria um usuário
2. no arquivo `support/index.js`, no método `before` ou no `beforeEach` dentro das specs, chamamos nosso método que cria os dados
3. para evitar o uso de `return`, `let` e `const` (má prática no cypress) podemos utilizar o Cypress.env, e salvar os dados que queremos.
4. para capturar o dado posteriormente, podemos usar o Cypress.env também.

Abaixo alguns trechos:

*commands.js*
```
// comando para criar dados antes dos testes
Cypress.Commands.add("createData", () => {

    cy.request({
        method: 'POST',
        url: `${BACKEND_HOST}/data`,
        headers: { Accept: 'application/json' },
        body: {
            name: 'Meu registro',
        }
    }).then(response => {
        Cypress.env('savedData', response.body.data);
    });
})
```

*index.js*

```
before(() => {
    cy.createData();
});
```

*spec.js* 

```
    cy.log(Cypress.env('savedData'));
```

...
