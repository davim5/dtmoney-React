# 10 - Componente: NewTransactionModal

- Pasta
    - index.tsx
    - styles.ts
- Retornar o conteúdo que estava em <Modal>
- Importar Modal
    - Criar interface
    - New transactionModalProps
        - Receber isOpen:boolean e onRequestClose:()⇒void

- Passar no App no lugar do Modal.
    - Passar os parâmetros

# Porque manter estado no App em vez de colocar no novo Componente?

- A informação de abrir o modal.

**Sempre que precisar que uma informação seja compartilhada entre mais de um componente**

- R**epassar a informação para um componente que está por volta desses componentes**
    - **Assim a informação pode ser acessada por eles.**