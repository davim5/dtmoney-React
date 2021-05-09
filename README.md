# 25 - Criando Hook

# Por que?

- Toda vez que precisamos usar o TransactionsContext em qualquer lugar da aplicação.
- Preciso importar tanto o useContext quanto o TransactionsContext
- Vamos reduzir isso em uma unica importação.

# Como?

- Criar uma pasta **hooks** no src.
- Renomear o TransactionsContext para useTransactionsContext.
    - Pois será um hook.
    - **Todo hook começa o nome com "use"**
- Colocar o useTransactionsContext na pasta hooks.

- exportar uma função useTransactions
- **Um hook no React sempre pode se utilizar de outros hooks.**

```tsx
export function useTransactions() {
    const context = useContext(TransactionsContext);

    return context; 
}
```

- Trocar em todos os locais que usavam useContext por useTransactions