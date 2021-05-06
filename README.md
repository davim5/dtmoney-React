# 07 - Configurando MirageJS

- Quando estamos desenvolvendo uma aplicação como essa
- É interessante deixar o frontend "conectado" como se houvesse um backend para imaginar como seriam as rotas.

```tsx
// TransactionsTable
useEffect(()=> {
	fetch('http://localhost:3000/api/transactions')
	.then(response => reponse.json())
	.then(data => console.log(data))
},[]);
```

# Instalar

```bash
yarn add miragejs
```

# Importar Server

- No index.tsx
    - Importar server ou createServer de miragejs

    ```tsx
    import { createServer } from 'miragejs'
    ```

# Chamar função createServer

- Definir
    - routes → Quais as rotas que terei na api fictícia.
        - namespace → Todas as chamadas vão ser partir desse endereço. Chamadas direcionadas ao miragejs.
        - get→ Quando houver uma requisição tipo GET.
            - Colocar rota e o que for deve ser devolvido.

```tsx
import { createServer } from 'miragejs'

createServer({
  routes(){
    this.namespace = 'api';
    this.get('/transactions', () =>{
      return [
        {
          id:1,
          title:'Transaction 1',
          amount: 400,
          type: 'deposit',
          category: 'food',
          createdAt: new Date()
        }
      ]
    })
  }
})
```