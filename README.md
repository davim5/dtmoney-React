# 08 - Configurando cliente do Axios

- Cliente HTTP
    - pra não precisar fazer requisições utilizando fetch.

# Por que não utilizar fetch?

- Fetch precisa que coloque todo o endereço da aplicação em cada requisição
    - Mas tem uma parte que se repete sempre.
- Precisa ficar transformando o resultado da resposta em JSON sempre.
    - Poderia criar uma função, mas melhor usar um lib

# Axios

- É possível interceptar resposta antes e fazer alterações.

## Instalação

```tsx
yarn add axios
```

- Criar pasta **services**.→ Seviços de dados. Api externa ou qualquer coisa assim.
    - Criar arquivo api.ts

## Configurando

- No api.ts
- importar axios from axios
- Criar uma constante **api.**
    - criar instância do axios.
        - setar informações padrão para todas as requisições
            - baseURL → endereço que se repete em todas as requisições
            - headers → cabeçalhos (token de autenticação

    ```tsx
    const api = axios.create({
    	baseURL:'http://localhost:3000/api',
    })
    ```

# Atualizar onde tem fetch

- Onde tem fetch
- trocar com api.get('/transactions')
    - "/" no começo é opcional
- Agora os dados não vão estar exatamente na resposta, mas em "**resposta.data**"

```tsx
useEffect(()=>{
        api.get('/transactions')
        .then(response => console.log(response.data))
    },[]);
```