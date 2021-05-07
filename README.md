# 17 - Inserindo Transação na API

- Pegar dados do formulário
- Comunicar com API.
- Colocar dados em variável **data.**

# Inserindo com MirageJS

- Método post
- Rota transactions
- Passando data

```tsx
api.post('/transactions', data);
```

# Criar rota de POST

- Inseração de novas transactions
- [this.post](http://this.post) ('/transactions')
- Parâmetros
    - schema
        - Não vamos usar ainda
    - request
        - Dados que vamos enviar para a transaction
        - Obtemos os dados através de request.requestBody
            - Vão vir em forma de text
            - Precisamos "Parsear" para formato JSON

    ```tsx
    this.post('/transactions',(schema,request)=>{
          const data = JSON.parse(request.requestBody)

          return schema.create('transaction',data);
        })
    ```

    - Agora podemos retornar os dados

# Banco de Dados Interno do MirageJS

- Queremos que as rotas estejam 'conectadas'.
- Os dados passados no POST devem ser pegues na rota GET

## Criando models

- Declara o nome da primeira tabela
    - Nome da entedidade → transactions
    - Declarar que é do tipo Model

```tsx
models:{
    transaction: Model,
  },
```

### Na rota POST

- return schema.create → Banco de Dados
    - Model que estou inserindo
    - Dados que devem ser passados para o model

```tsx
return schema.create('transactions', data)
```

### Na rota GET

- Retornar todas as informações dentro do banco de dados

```tsx
return this.schema.all('transactions')
```