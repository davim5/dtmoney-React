# 19 - Formatando Valores

- Usando API nativa do próprio browser.

# INTL

## Dinheiro

- Formatar valores
    - pt-br → Região
    - style: currency,
    - currency: 'BRL'
    - .format(variável pra formatar)

```tsx
<td className={transaction.type}>
    { new Intl.NumberFormat('pt-BR',{
        style: 'currency',
        currency: 'BRL'
    }).format(transaction.amount)}
</td>
```

## Data

- pt-br
- .format(new Date(variável) )

```tsx
	<td>
	    { new Intl.DateTimeFormat('pt-BR').format(new Date(transaction.createdAt))}
	</td>
```