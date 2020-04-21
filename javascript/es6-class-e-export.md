https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes

Uma forma de usar classes (e no meu caso, aplicar isto a testes) é usando a seguinte sintaxe:

```
class NomeDaClasse {
  // algum conteúdo aqui

}

export default new NomeDaClasse();
```

Isso facilita pois não há a necessidade de instanciar um novo objeto da classe onde ela for importada, basta sair usando.

Pra centralizar importações, é possível seguir algo assim:

```
// arquivo responsavel por centralizar as importacoes

import nomeDaClasse1       from './Diretorio1';
import nomeDaClass2   from './Diretorio2';

export { 
  nomeDaClasse1,
  nomeDaClass2
}
```
