# 23 - Finalizando Inserção

Precisamos:

- Ao inserir nova transação
    - Fechar modal.
    - Carregar na transação na lista.

# 1. Fechar Modal

- Chamar onRequestClose após criar.
- Só chamar se a transação der certo
    - Ela precisa aguardar a transação acontecer
    - Usando **await (Função assíncrona)**

    ```tsx
    async function handleCreateNewTransaction(event:React.FormEvent){
      event.preventDefault();

      await createTransaction({
          title,
          amount,
          category,
          type,
      })

      setTitle('');
      setAmount(0);
      setCategory('');
      setType('depoist');
      onRequestClose();
    }
    ```

- Transformar a createTransactions em função assíncrona

    ```tsx
    async function createTransaction(transactionInput:TransactionInput){   
      api.post('/transactions',transactionInput);
    }
    ```

- Ajustar o formato a função (Interface)
    - Toda função assíncrona retorna uma *promise*

    ```tsx
    interface TransactionContextData{
    	transactions: Transaction[]; //Array de Transactions
    	createTransaction: (transaction:TransactionInput) => Promise<void>;
    }
    ```

## Resetar os valores do Modal

```tsx
	setTitle('');
  setAmount(0);
  setCategory('');
  setType('depoist');
  onRequestClose();
```

# 2. Mostrar novo Item

- Quando o Mirage faz a inserção na api, a api nos retorna o os dados inseridos.
- Na resposta da inserção, temos acesso ao dado que foi inserido.
- Na função de createTransaction
- Acessar a response da inserção
    - Colocar dentro do state de transactions

```tsx
async function createTransaction(transactionInput:TransactionInput){   
  const response = await api.post('/transactions',transactionInput);
  const { transaction } = response.data;
  
  setTransactions([
      ...transactions,
      transaction,
  ])
}
```

- O createdAt não estava inclusivo no input da transaction, mas está na tabela.
- Vamos criar a Date na hora de incluir no Estado das transactions.

```tsx
async function createTransaction(transactionInput:TransactionInput){   
        const response = await api.post('/transactions',{
            ...transactionInput, // ... -> Pegar todos os dados 
            createdAt: new Date(),
        });
        const { transaction } = response.data;
        
        setTransactions([
            ...transactions,
            transaction,
        ])
        
    }
```