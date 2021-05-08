# 20 - Context API no React

# Forma mais simples de criar Context

- Criar na pasta src
    - arquivo TransactionsContext.ts
- importar createContext de react
- Criar várial const TransactionsContext = createContext();

- CreateContext
    - Passar qual o valor default.
    - Iniciar como vetor vazio

```tsx
import { createContext } from 'react';

export const TransactionsContext = createContext([]);
```

- **Quando criamos contexto no react, conseguimos acessa-lo a partir de qualquer componente da aplicação.**
    - **Para que esses componentes tenham acesso ao contexto, precisamos colocar um *Provider* por volta deles.**

# Provider

- Criar por volta de todo o App.tsx
    - Importar o TransactionsContext.ts
    - Colocar TransactionsContext.Provider no fragment <>
- O Provider obrigatoriamente precisa receber um *value.*
    - Passar o valor atual do contexto

```tsx
<TransactionsContext.Provider value={[]}>
```

# Consumir o contexto na aplicação

- Agora qualquer componente do App vai poder consumir o conteúdo do contexto.
    - Têm acesso às informações.

## Como obter os valores?

### Forma antiga

- API do react → renderProps
    - Cria um componente TransactionContext.Consumer>
    - Em vez da passar um componente como filho do consumer, se passa um função.
        - Esta, vai receber os dados do contexto.

```tsx
<TransactionContext.Consumer>
{(data) => {
	console.log(data)
	return <p> ok </p>
}}
</TransactionContext.Consumer>
```

## Forma Nova

- Pós React Hooks
- Mais simples.
- Cria variável data
- useContext passando nome do contexto

```tsx
const data = useContext(TransactionsContext);
```

- **Sempre que a informação do contexto mudar, os dois componentes vão renderizar novamente mostrando as atualizações.**