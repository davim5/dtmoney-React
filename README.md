# 21 - Carregando Transações

- Carregar lista de transações dentro do contexto.
- A informação que queremos está em um componente só.
- Devemos repassar para o contexto.

# **Uma forma**

- Mover para o App.tsx, e passar no value do context.

```tsx
<TransactionsContext.Provider value={transactions}>
```

- Vai funcionar assim, mas não é muito bom.
    - Se tivermos mais contextos, o código do App vai ficar muito e cheio e cada vez mais complexos.

# Forma melhor

- No TransactionsContext.ts
- Exportar componente TransactionsProvider
    - dentro dele, colocar o código função de GET das informações
    - do estado das informações
    - da interface
- retornar
    - <TransactionContext.Provider>
        - Substituir o que estava no App, por esse que está sendo criado.
        - Toda a logica do carregamento de dados vai estar dentro desse Provider específico.
    - Colocar value={transactions}
- Atualizar o tipo de informação do Contexto
    - Lista de transaction

```tsx
export function TransactionsProvider({children}:TransactionProviderProps){
    const [transactions, setTransactions] = useState<Transaction[]>([]);

    useEffect(()=>{
        api.get('/transactions')
        .then(response => setTransactions(response.data.transactions))
    },[]);

    return(
        <TransactionsContext.Provider value={transactions}>
            {children}
        </TransactionsContext.Provider>
    );
}
```

# No App

- Trocar o Transaction.Provider pelo que foi criado

```tsx
<TransactionsProvider>
      <Header onOpenNewTransactionModal={handleOpenNewTransactionModal}/>

      <Dashboard/>

      <NewTransactionModal
        isOpen={isNewTransactionModalOpen}
        onRequestClose={handleCloseNewTransactionModal}
      />
      
      <GlobalStyle/>
</TransactionsProvider>
```

# Children

- Falar que o componente recebe children dentro dele
- Criar interface TransactionProviderProps
- children: ReactNode
    - importar ReactNode de 'react'
    - Aceita qualquer tipo de conteúdo válido para React.

```tsx
interface TransactionProviderProps {
    children:ReactNode;
}
```

- Pegar o children das props e passar no retorno