# 04 - Component Header

# Criando primeiro componente

- No src
- Criar pasta components
    - Nela criar pasta Header.
        - Criar arquivo index.tsx

# Criando

- Criar função Header
    - Retornando componente qualquer.
- Importar no App.tsx
- Colocar junto com o GlobalStyle em um fragment

```tsx
<>
	<Header/>
	<GlobalStyle/>
</>
```

# Estilizando

## 1. Começar criando estrutura

- Estrutura antes do css.
- Colocar todos os elementos em tela e depois ir estilizando eles.
- **Logo**
    - importar o arquivo da logo.
        - Pode usar o import como qualquer outro arquivo.
        - Dar um nome.

        ```tsx
        import logoImg from '../../assets/logo.svg';

        export function Header() {
        	return (
        		<header>
        			<img src={logoImg} alt="dt money"/>
        			<button type="button">
        				Nova transação
        			</button>
        		</header>
        	)
        }
        ```

## 2. Utilizar Styled Components para Estilização.

- **Poderia fazer no mesmo arquivo do index.tsx , mas os estilos podem ficar muito grandes e o arquivo ficar muito cheio.**
    - Por isso o componente foi criado como uma pasta.
        - Assim dentro da pasta teremos:
            - O index.tsx → Componente
            - O styles.ts → Estilizações do componente

### Hover no botão (com filter)

- filtro no botão com css.

```tsx
transition: filter 0.2

&:hover{
	filter: brighteness(0.9);
}
```