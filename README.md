# 03 - Fontes no Google Fonts

# Encontrar fonte

- Pesquisar pelo nome
- Google fonts
- "Poppins"
- Selecionar os tamanhos
    - 400
    - 600
- Utilizar via **Link**
    - Usado no React

# Importando

- No index.html
    - Colar os links no head
    - Colocar link preconnected antes de tudo.
        - Abre conexão com o cdn que entrega os arquivos da fontes para nós. Pré carregamento.
        - Deixa mais rápido que abrir uma conexão.
        - 25% mais rápido

# No arquivo Global

- Definir fonte poppins nos desejados

```tsx
body, input, textarea, button {
	font-family: 'Poppins', sans-serif;
	font-weight: 400;
}

h1,h2,h3,h4,h5,h6,strong{
	font-weight: 600;
}
```

- **Por que não só no body?**
    - Inpute, TextArea e Button por padrão não importam a fonte do **body.**