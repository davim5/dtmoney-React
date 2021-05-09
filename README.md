# 22 - Movendo a Criação para o Context

- Usar o useContext na newTransactionsModal
- Chamar a transactions.
- Adicionar dados da nova transação na transactions
    - Não pode ser alterado diretamente, tem que usar o setTransactions

```tsx
const transactions = useContext(TransactionsContext)
```

# Atualizar Lista de Transações

- Usando o contexto

## Como?

- Importar o useContext no NewTransactionModal.
- Pegar o contexto das transactions.

- **Para colocar um nova transaction adicionar dados da nova transação na transactions, não pode ser alterado diretamente, tem que usar o setTransactions. (Imutabilidade)**

- Pegar toda a lógica de criar nova transaction e colocar dentro do contexto.
- Criar uma função createTransaction.

```tsx
function createTransaction(transaction:TransactionInput){   
        api.post('/transactions',transaction)
    }
```

## Criando um novo Tipo

- Criar uma interface propria para os dados que devem ser passados para criar uma transaction.

    ```tsx
    interface TransactionInput {
    	title: string;
    	amount: number;
    	type: string;
    	category: string;
    }
    ```

- Ou criar usando um ***Omit*** da outra interface.
    - Passar a interface e os campos que queremos omitir

```tsx
		type TransactionInput = Omit<Transaction, 'id' | 'createdAt'>;
```

- Ou criar usando um ***Pick*** da outra interface.
    - O contrário do Omit.
    - Passar interface e as que queremos que fiquem.

```tsx
		type TransactionInput = Pick<Transaction, 'title' | 'amount' | 'type' | 'category'>;
```

## Retornar a função no contexto junto com as Transactions

- Retornar um objeto
    - Listagem de transactions
    - Função

```tsx
return(
  <TransactionsContext.Provider value={{transactions, createTransaction}}>
      {children}
  </TransactionsContext.Provider>
);
```

### Criar um formato para o contexto para conseguir passar.

- No createContext, tinhamos ditos que dentro teria apenas uma lista de Transaction.

```tsx
export const TransactionsContext = createContext<Transaction[]>([]);
```

- Mas agora temos tanto a lista quanto a função.

### E agora?

- Criar uma interface TransactionsContextData
- Falar qual o formato do Contexto

```tsx
interface TransactionContextData {
  transactions: Transaction[]; //Array de Transactions
  createTransaction: (transaction:TransactionInput) => void;
}
```

- Para não dar erro, o valor padrão tem que ter o formato que dissemos que ele tinha, mas está sendo passado como vazio [ ].
    - Passamos um objeto vazio.
    - Forçamos tipagem
        - as *Formato*

    ```tsx
    export const TransactionsContext = createContext<TransactionContextData>(
        {} as TransactionContextData
        );
    ```

# Ajustes

- Agora nas outros arquivos, temos/podemos que fazer desestruturação para pegar as transactions (Onde usamos useContext).

```tsx
export function NewTransactionModal({ isOpen,onRequestClose }:NewTransactionModelProps){
  const { createTransaction } = useContext(TransactionsContext)
  // Armazenar qual botão o usuário clicou
  const [type,setType] = useState('deposit');
  const [title,setTitle] = useState('');
  const [amount,setAmount] = useState(0);
  const [category,setCategory] = useState('');

  function handleCreateNewTransaction(event:React.FormEvent){
    event.preventDefault();

    createTransaction({
        title,
        amount,
        category,
        type,
    })
  }
```