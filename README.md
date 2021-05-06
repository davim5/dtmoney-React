# Estrutura com create-react-app

# O que é?

- Estrutura pré-configurada de um projeto react
    - Se preocupar somente com o código e menos com as configurações

# Criando Projeto

- Comando
    - nome projeto
    - template → Normalmente instalaria com javascript, mas existem templates como o com **typescript.**
        - Dá pra criar o próprio template também

```bash
yarn create react-app nomedoprojeto --template typescript
```

- Pode demorar um pouquinho na primeira vez

# Dicas

- Já vem com um README padrão, pode deletar ou alterar se quiser
- Pode apagar alguns arquivos que não serão utilizados

## Index.html

- Deletar comentários
- deixar do <meta> só o charset e name
- mudar o título

## Public

- Deletar tudo da pasta public menos index.html

## Src

- Deletar
    - Arquivos css
    - Imagens
    - Tests
- Deixar só App, index e react-app-env

### No index.tsx

- Apagar
    - importação do css
    - importação do webvitals
    - Tirar comentários

### No App.tsx

- Apagar
    - Importação do react
    - svg
    - css
- Deixar apenas div class name app.
    - Colocar h1 hello world
- Exportar App sem utilizar o **export default App;**

# Por que utilizar exportações *export* e não *export default?*

## Export Default

```tsx
function App() {
 return (
		<div className="App">
			<h1>Hello World</h1>
		</div>
	);
}

export default App;
```

- Quem define nome do componente não é quem está exportando o componente, mas quem está importando.
    - **Exemplo:**
        - Se outro arquivo, eu quiser mudar o nome da exportação para qualquer outro, eu posso.

        **Posso importar com o nome que quiser**

        ```tsx
        // import App from './App'
        import batata from './App'
        ```

## Export

```tsx
export function App() {
 return (
		<div className="App">
			<h1>Hello World</h1>
		</div>
	);
}
```

- Quem está importando não consegue definir o nome.
    - Ele daria erro
- Tem que importar, obrigatoriamente, o App que está lá dentro.
- Dá segurança maior para não esquecer de mudar o nome.
- A exportação automática fica mais fácil e inteligente.

```tsx
// import App from './App'
import { App }from './App'
```

# Outras configurações

- Toda a configuração de webpack e babel não ficam no projeto, não conseguimos ver.
    - Ficam dentro de um pacote instalado pelo create-react-app chama react-scripts.

## Script Eject

- Serve para mudar alguma configuração se necessário
- **Não tem mais volta, se excutar.**
- Traz todas as configurações para a raiz do projeto.

# Mudar dependências "desnecessárias" para devDependencies