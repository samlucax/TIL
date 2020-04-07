https://docs.cypress.io/api/commands/stub.html

Em alguns casos, pode ser necessário validar ou interagir com conteúdos presentes apenas em **alerts** da aplicação.

Um alternativa é usar o `cy.stub` e o `cy.on`. 

O `cy.stub` serve para "injetar" uma escuta em alguma parte da aplicação. Como se fosse um debugger privilegiado.
O `cy.on` permite indicar funções do sistema operacional, browser ou aplicação para serem "auditadas", pelo stub por exemplo.

```
    const stub = cy.stub();
    cy.on('window:alert', stub);

    cy.server();
    cy.route('POST', '**/ongs').as('postOng');

    cy.get(registerEl.BUTTON_SUBMIT).click()
    .then(() => {
    
        // stub - alert
        // getCall(0) - instancia do alert
        // args - conteúdo textual do alert.
        // toString, converte o conteúdo para string
        // split(':')[1] - divide o texto "seu id: d8a9823" em duas partes, e pega só a segunda, que é o id
        // replace(" ", "") - remove os espaços sobrando, caso houver.
        
        let idAccess = stub.getCall(0).args.toString().split(':')[1];        
        idAccess = idAccess.replace(" ", "");
        
        //asserções no conteúdo extraído do alert
        expect(idAccess).not.to.be.empty;
        expect(idAccess).not.to.be.null;
        
        // uma vez que o conteúdo foi capturado, é possível utilizar esse dado, por exemplo, salvando em algum arquivo.
        cy.writeFile('cypress/fixtures/data.json', { id: `${idAccess}` });
    });
```

Obs.: no meu caso essa mesma informação vinha na resposta da requisição.. então optei por validar a resposta com cy.route / cy.wait.
