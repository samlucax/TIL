https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/from

O Array.from é um recurso do ES6, que como o próprio nome diz, serve para criar uma instância de um array quando recebe um argumento do tipo array ou iterable.

No meu caso foi para um uso simples, limpar uma lista de produtos de um carrinho, reaproveitando um método que excluia item a item por id.

```
  Array.from(cart).forEach(product => {
      dispatch(CartActions.removeFromCart(product.id));
  });

```
