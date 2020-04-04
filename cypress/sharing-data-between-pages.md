*Primeiramente, isso não é uma boa prática segundo o guia de boas práticas do Cypress.*

- https://docs.cypress.io/guides/references/best-practices.html#Organizing-Tests-Logging-In-Controlling-State

Porém... o que eu preciso fazer - algo muito comum, por sinal - é utilizar um dado criado durante em passo do teste, em outro.
Mais precisamente em outro arquivo.

A questão é que os comandos do Cypress API executam de forma *assíncrona*, e pode ocorrer de que o dado que estou tentando utilizar ainda não tenha sido populado, mesmo que visualmente no código ele esteja nas linhas seguintes.

Dito isso, uma alternativa plausível é: 
1. criar um arquivo usando o `cy.writeFile`
2. passar os dados para este arquivo
3. capturar o conteúdo deste arquivo com o `cy.readFile`
4. atribuir o conteúdo deste arquivo a um alias `...as()`
5. capturar o conteúdo do alias `cy.get()`
6. analisar, validar, anyway, usando o `.then` a partir do conteúdo do alias.

O trecho vai ficar mais ou menos assim:

**ArquivoGeraDado.js:**

```
  cy.writeFile('cypress/fixtures/data.json', { info: 'oi' });
```

**ArquivoLeDado.js:**

```
    cy.readFile('cypress/fixtures/data.json').as('data');

    cy.get('@data').then((data) => {
        cy.log(`Data: ${data.info}`);
    });
    
    // resultado: oi
```

Fontes:
- https://github.com/cypress-io/cypress/issues/1392#issuecomment-369560205
- https://docs.cypress.io/api/commands/readfile.html#Syntax
- https://docs.cypress.io/api/commands/writefile.html#Syntax
