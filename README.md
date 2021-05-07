# 14 - Funcionamento dos Botões

- Criar estado para armazenar tipo do botão selecionado.

# Função para alterar a seleção

- Poderia ser feita uma função simples ❌

```tsx
function handleSetTypeDeposit(){
	setType('deposit')
}
```

- Mas a função é tão simples que pode ser passada com arrow function na propria proriedade *onClick* do botão. ✅

```tsx
onClick={()=>setType('deposit')}
```

# Componente RadioBox

- styled.button
- Trocar button por radiobox
- **Usando styled components, podemos estilizar o componente de acordo com uma propriedade, não só com uma className.**
    - Usamos pouco className.
    - Agora ele pode receber novas propriedades
        - Podem ter o nome que quisermos.

```tsx
isActive ={type==='deposit'}
```

# Propriedade do Componente Estilizado

- Interface RadioBoxProps
    - Falar que recebe propriedade isActive:boolean.
- Passar através de *generic*

```tsx
interface RadioBoxProps {
	isActive:boolean
}

export const RadioBox = styled.button<RadioBoxProps>`
`
```

# Alterar de acordo com a propriedade

- No styled componentes
    - **Toda vez que se passar uma função dentro de uma interpolação( ${ } ), essa função será chamada automaticamente pelo styled components passando todas as propriedades do componente. (props)**

```tsx
background: ${(props) => props.isActive ? '#eee' : 'transparent'}
```

- O conteúdo dentro da função é JavaScript, então o CSS deve estar entre aspas.