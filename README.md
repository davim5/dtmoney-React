# 16 - Tendo Acesso aos Dados do Input

- Tendo acesso ao valor digitado nos inputs para inserir a informação à API.

# Função

- handleCreateNewTransaction
- Vai ser disparada através do submit no formulário
    - Form vai ter um *onSubmit* chamando a função.
- Toda vez que der enter no input, a função será executada.

```tsx
<Container
onSubmit={handleCreateNewTransaction}
>
...
<Container/>
```

- No HTML, por padrão, todo formulário quando ´da submit, recarrega a tela

    ## Prevenindo esse padrão do HTML

    - Quando passamos a função no onSubmit.
        - Recebe as informações
        - Envia como parâmetro um *event.*
            - Tipo React.FormEvent
    - Dar um formato para o event.
        - ReactForm
- Dessa forma, teremos todos os dados desse evento.
- event.PreventDefault( )

```tsx
function handleCreateNewTransaction(event: FormEvent) {
	event.PreventDefault( )
}
```

- Agora não vai fechar.

# Tendo Acesso aos Dados do Input

## Forma mais tradicional

- Anotar as formas dos inputs
- Criar valor no state para cada input

```tsx
const [title, setTitle] = useState('');
const [value, setValue] = useState(0);
const [category, setCategory] = useState('');
```

- Em cada <input>
    - Colocar propriedades
        - Value={} → apontando para o estado
        - onChange
            - Executa toda vez que um novo texto for editado no input.
            - devolve um evento
            - setar o valor do estado com o novo valor digitado

        ```tsx
        value={title}
        onChange = (event) => setTitle(event.target.value)
        ```

    - No caso do input number precisa converter pra algo numérico
        - pode ser colocando um '+' (gambiarra)
        - colocando um Number()
- Agora podemos cadastrar dados e armazenar na API.