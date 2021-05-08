# 18 - Listando transações e seeds

- Buscar todas as transactions da API
- Mostrar em tela

# Deixando dados pré-cadastrados

- Para não iniciar sozinho
- Função seeds
    - recebe propriedade server
    - Executar server.db.loadData({})
        - Passar nome da tabela (do Model no plural)
        - Devolver as transactions

```tsx
transactions: [
	{
		id:1,
		title:'',
		type:'',
		category:'',
		amount: 0
		createdAt: new Date()
	},
	{
		id:2,
		title:'',
		type:'',
		category:'',
		amount: 0
		createdAt: new Date()
	},
]
```

# Mostrar em tela

- Criar um estado array.
- setar os dados recebidos no array
- response.data.transactions

```tsx
const [transactions, setTransactions] = useState<Transaction[]>([]);
```

- Listar um <tr> para cada transactions

```tsx
<tbody>
  {transactions.map(transaction =>{
      return (
          <tr key={transaction.id}>
              <td>{transaction.title}</td>
              <td className={transaction.type} >{transaction.amount}</td>
              <td>{transaction.category}</td>
              <td>{transaction.createdAt}</td>
          </tr>
      );
  })}
</tbody>
```

# Definir o Formato da Transaction

- Criar interface

```tsx
interface Transaction {
    id: number;
    title: string;
    amount: number;
    type: string;
    category: string;
    createdAt: string;
}
```

- Converter createdAt para data.

## Repetindo

- Lembrar da Key

```tsx
          <tr key={transaction.id}>
```