https://github.com/echoulen/storybook-addon-styled-component-theme/issues/37#issuecomment-595266806

O storybook 5.3 tem uma issue de compatibilidade com o `storybook-addon-styled-component-theme`, que faz com que ao utilizar a funcionalidade de abrir o canvas em uma nova aba, os componentes não sejam renderizados, resultando em uma tela branca e sem elementos ou erros.

Isso impacta por exemplo no uso do Percy para testes de regressão visual com o storybook, já que o Percy também renderiza os elementos de forma externa.

A solução basicamente foi migrar do `storybook-addon-styled-component-theme` para o `themeprovider-storybook`.

- https://github.com/semoal/themeprovider-storybook
