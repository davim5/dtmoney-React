# 09 - Configurando criação de modal

- Vamos usar uma lib externa chama **react-modal**
    - Do reactjs

# Porque usar e não criar do zero?

- Traz funcionalidades prontas padrão de modal
    - Apertar esc e fechar
    - Clicar fora e fechar
    - ...
- Não tem problema, melhor que perder tempo.
- É bem completa

# Instalação

```tsx
yarn add react-modal
yarn add @types/react-modal
```

- Qual botão vamos clicar?
    - Nova transação
    - Que fica no header.

# Criando o Modal no Header

## O que ela pede?

- Criar estado que anota se modal está aberto ou fechado.
    - Inicia como false.
- Função OpenModal
    - Seta estado como true
- Função CloseModal
    - Seta estado como false
- Botão que executa abertura
- Componente
- Propriedade isOpen
- onRequestClose → O que deve acontecer quando usuário pedir pra fechar o modal? Ex: Executar função close modal
- Resto é visual.

# Criando função

- Quando se cria uma função que é **executada a partir de ação do usuário.**
    - É legal iniciar função com **handle**!

```tsx
const [isNewTransactionModalOpen,setIsNewTransactionModalOpen] = useState(false);

  function handleOpenNewTransactionModal(){
      setIsNewTransactionModalOpen(true);
  }

  function handleCloseNewTransactionModal(){
      setIsNewTransactionModalOpen(false);
  }
```

# Componente

- Pode colocar a tag do componente em qualquer lugar.
- Colocar as propriedades
    - isOpen={função OpenModal}
    - onRequestClose={função CloseModal}

# Repasse de propriedades nos Componentes

- Modal faz parte da aplicação, mas não do cabeçalho.
- Migrar todo o <Modal> para App.tsx.
    - Importar modal
    - colar as funções e estado.

### **A função de abrir o modal, que está no botão do Header, foi para o App, que não "enxerga" a função.. E agora, como ter acesso à ela?**

- O header pode receber a **função** como uma **propriedade** do Componente.
    - Sempre bom criar um interface para definir essas propriedades
    - Quando é um componente que recebe uma função, é bom começar a função com "**on**"
    - Função que retorna vazio
- Definir as propriedades do Header
    - Desestruturar
    - Passar no onClick

```tsx
interface HeaderProps {
	onOpenNewTransactionModal: () => void;
}

export function Header({ onOpenNewTransaction }: HeaderProps){
    return(
        <Container>
            <Content>
                <img src={logoImg} alt="dt money" />
                <button type="button" onClick={onOpenNewTransaction}>
                    Nova transação
                </button>
            </Content>
        </Container>
    )
};
```

- Agora, no App, o componente Header vai estar "pedindo" essa propriedade!
    - Passar a função que queremos que seja executada!

### Quando precisamos que um estado seja controlado por um componente filho, podemos passar uma função para esse componente filho para alterar essa informação.

- **Header(Filho) está alterando uma informação do componente App(Pai)**

# Melhorando conteúdo do Modal

- Importante para acessibilidade.
- Informar qual o elemento "root" do modal
    - Vai jogar o modal no elemento root, e não no body.

```tsx
Modal.setAppElement('#root');
```