Para executar scripts que estão em subpastas, exemplo:

```
root
  package.json
  /app1
    package.json
  /app2
    package.json
    
```

Basta navegarmos até o diretório e executar o script com npm. Deve funcionar para o yarn da mesma forma.

```
  "scripts": {
    "start:app1": "cd app1 && npm start",
```

`npm run start:app1`
