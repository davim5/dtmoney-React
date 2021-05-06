# Instalando Styled Components

- Uma das estratégias mais comuns de várias bibliotecas de FrontEnd

# CSS in JS

- CSS no JavaScript

# Instalar Styled-Component

- Biblioteca mais utilizada pra isso.

```bash
yarn add styled-components
yarn add @types/styled-components
```

# Estilização tradicional

- Cria arquivo css.
- Coloca estilização.
    - Estilizar propriedade
- Importa arquivo a onde a estilização é usada.

```css
.title {
		font-size:64px;
		color: #8227e6
}
```

- Colocar className="nomeDaPropriedade" na tag

```tsx
<div>
	<h1 className="title"> Hello World</h1>
</div>
```

# Estilização CSS in JS

- Diferença: não vamos usar diretamente className's nos componentes.
- Vamos criar componentes previamente estilizados.
- Importar styled do styled-components.

```tsx
import styled from 'styled-components'
```

- Se quiser fazer a mesma estilização passada.
- Cria-se um componente.
    - Cria como um constante
    - Letra maúscula
    - styled.tag
    - Abrir aspas ``
        - Dentro colocar a estilização.

    ```tsx
    const Title = styled.h1`
    	font-size: 64px;
    	color: #8257e6;
    `
    ```

- Coloca o componente como tag.

```tsx
<div>
	<Title> Hello World</Title>
</div>
```

# Vantagens

## Encadeamento

- Pode estilizar os filhos com chaves.
- Árvore

## Escoped

- Estilização fica dentro do Escopo do componente
- Nunca vai poder ser compartilhada com outros componentes.
- Diferente de uma classe, que pode ser usada em vários.
- CSS sempre vai ficar muito próximo do componente em si