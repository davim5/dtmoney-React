# 15 - Cores dos Botões

- Cada botão tem uma cor quando selecionado.
- Criar uma propriedade activeColor para a tag

```tsx
activeColor="green"
```

## Adicionar a propriedade na intercace do RadioBox

- Colocar que aceita apenas as cores usadas na aplicação;

```tsx
interface RadioBoxProps{
    isActive:boolean;
    activeColor: 'green' | 'red';
}
```

## Criar constante com os valores das cores.

```tsx
	const colors = {
    green: '#33cc95',
    red: '#e52e40'
}
```

- Porque não usar variáveis css lá dentro?
- Ao usar cores dentro do JS, ele não "enxerga" as variáveis CSS.
- Usar o transparentize do polished para diminuir intensidade da cor.

```tsx
background: ${(props)=> props.isActive 
    ? [transparentize(0.9,colors[props.activeColor])] : 'transparent'};
```