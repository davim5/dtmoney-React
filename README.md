# 13 - Criando botões de tipo

- Criar funcionalidade própria de "checkbox" "radiobutton"
- Criar como um componente novo.

- No styles.js
    - **Quando estamos fazendo uma estilização toda dentro de um Container, não é prático criar um novo elemento e estilizar por fora desse container. Se há essa necessidade, pode ser melhor criar um novo componente mesmo.**
    - **Mas a estilização pode ser feita no mesmo arquivo, exportando um componente diferente.**

- Criar o novo Container
    - button type=button
    - img src=incomeImg
    - span entrada

# Funções JS para manipulação de cores

- Instalar lib **polished**

```tsx
yarn add polished
```

- Tem muitas funções para modificar as cores;
- Importar função darken de polished.
- Por o estilo estar entre **` `**, podemos colocar uma função JS lá dentro, utilizando "**${ }**".

```tsx
transition: border-color 0.2s;

&:hover{
	border-color: ${darken(0.1,'#d7d7d7')}
}
```