https://github.com/cypress-io/cypress-example-todomvc#custom-commands

Criar custom commands para facilitar a escrita dos testes com comandos comuns é uma prática recomendada pelo Cypress.
Porém, estes comandos não trazem Intellisense de forma nativa. Para adicionar:

1. Criar um arquivo `cypress/support/index.d.ts`
2. Adicionar a assinatura de seus comandos criados


```
/// <reference types="cypress" />

declare namespace Cypress {
  interface Chainable<Subject> {
    /**
     * Create several Todo items via UI
     * @example
     * cy.createDefaultTodos()
     */
    createDefaultTodos(): Chainable<any>
    /**
     * Creates one Todo using UI
     * @example
     * cy.createTodo('new item')
     */
    createTodo(title: string): Chainable<any>
  }
}
```
