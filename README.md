# 02 - Criando Estilos Globais

- Estilizações que não são de um só componente, mas de toda aplicação.
    - Fonte
    - Background

# Criando

- No src
- Criar pasta **styles**
    - Dentro criar arquivo **global.ts**
    - Importar createGlobalStyle de styled-components

## GlobalStyle

- Criar variável GlobalStyle
    - Com letra maiúscula, pois será convertido em um componente React
- = createGlobalStyle
- aspas ` `
    - **Template Literals**
        - Permite depois fazer novas variáveis dentro e executar funções ${}

```tsx
export const GlobalStyle = createGlobalStyle`
	* {

		}

	body
`;
```

### Utilizando variáveis do CSS para as cores da aplicação

- :root

```tsx
:root {
	--background: #f8f2f5
}

body {
	background: var(--background);
}
```

# Tamanho de fonte

- Por padrão vem 16px.
    - Tamanho ideal para desktop.
- Na tag html
    - quando o usuário estiver com uma tela até 1080px de largura.
        - font-size: 93.75% (15px)
    - quando o usuário estiver com uma tela até 720px de largura.
        - font-size: 87.5% (14px)

    ## Porque diminuir a fonte?

    1. **Em dispositivos menores, faz sentido que seja menor.**
    2. **Vamos usar uma medida REM.**
        - 1 REM = tamanho do font-size da página
        - Se font-size da página =16px → 1 REM = 16px
    3. **Se estou dimuindo font-size conforme a tela fica menor.**
        - Utilizando REM, toda aplicação vai se adaptar à tela do usuário.
    4. **Caso o usuário esteja com configuração de aumentar ou diminuir fonte (em seu dispositivo).**
        - O % vai aumentar e diminuir da acordo com a preferência do usuário.

```tsx
html {
	@media (max-width: 1080px){
		font-size:93.75%;
	}
	@media (max-width: 720px){
		font-size:87.5%;
	}
}
```

# Importar arquivo

- Importar arquivo no App.tsx
- Colocar dentro de um tag.

```tsx
import { GlobalStyle } from "./styles/global";

export function App() {
  return (
    <div className="App">
      <h1>Hello Mundo</h1>
			<GlobalStyle />
    </div>
  );
}
```

# Botão desabilitado

```tsx
[disabled] {
	opacity: 0.6;
	cursos: not-allowed;
}
```