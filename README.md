# 24 - Calculando Resumo

# Reduce

## Forma com várias variáveis.

- Criar variável.
- Fazer um reduce das variáveis.
    - Percorre transactions
        - acc → acumulador
        - transaction.
    - Se depósito, somar no acumulador
    - retorna acumulador
    - iniciar com valor 0

```tsx
const totalDeposits = transactions.reduce((acc, transaction) => {
	if(transaction.type === 'deposit') {
		return acc + transaction.amount;
	}

	return acc;
},0);
```

## Forma com uma variável só

- Criar variável summary
- Fazer um reduce das variáveis.
    - Percorre transactions
        - acc → acumulador
        - transaction.
    - iniciar os três valores com 0 com:
        - deposits: 0
        - withdraw: 0
        - total: 0
- Na função

```tsx
const summary = transactions.reduce((acc,transaction)=>{
        if(transaction.type === 'deposit') {
            acc.deposits += transaction.amount;
            acc.total += transaction.amount;
        } else {
            acc.withdraws += transaction.amount;
            acc.total -= transaction.amount;
        }

        return acc;
    },{
        deposits:0,
        withdraws:0,
        total:0,
    })
```

# Formatando Respostas

```tsx
<strong>
    {new Intl.NumberFormat('pt-BR',{
        style: 'currency',
        currency: 'BRL'
    }).format(summary.deposits)}
</strong>
```