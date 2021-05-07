# 12 - Estilizando Modal

- Estilização geral do modal

# Botão de fechar

- importar o asset do ícone no componente
- colocar dentro do modal
    - Antes do Container.
    - Button type=button
        - img src={asset} alt="fechar modal"
    - onclick={onRequestClose}
    - className="react-modal-close"

```tsx
<button 
  type="button" 
  onClick={onRequestClose} 
  className="react-modal-close"
  >
      <img src={closeImg} alt="Fechar Modal" />
</button>
```

### Estilizar nos globais

- Provavelmente vai ter em todo modal.
- position absolute.

```tsx
.react-modal-close{
        position:absolute;
        right:1.5rem;
        top:1.5rem;
        border:0;
        background: transparent;

        transition: filter .2s;

        &:hover{
            filter:brightness(0.8);
        }
    }
```