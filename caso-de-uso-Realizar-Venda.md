# Casos de Uso

## UC01: Realizar Venda

### Ator(es):

- **Cliente**: Pessoa que adquire produtos na mercearia.
- **Funcionário do caixa**: Funcionário responsável por registrar a venda e processar o pagamento.
- **Operadora de pagamento**: Entidade que processa os pagamentos via cartão de débito, crédito, Pix e vale refeição.

### Interessado(s) e interesse(s):

- **Cliente**: Deseja pagar pelos produtos de maneira rápida, segura e eficiente, preferindo opções de pagamento convenientes.
- **Funcionário do caixa**: Busca registrar a venda e processar o pagamento de forma ágil e correta, evitando erros e garantindo a satisfação do cliente.
- **Gerente da loja**: Precisa garantir que as vendas sejam registradas corretamente, com controle de estoque e geração de relatórios financeiros e operacionais.
- **Operadora de pagamento**: Tem o interesse de processar as transações financeiras de forma segura, garantindo a autorização e liquidação dos pagamentos.

### Pré-condições:

- O cliente já selecionou os produtos desejados e se encontra na fila de pagamento.
- O sistema da mercearia está em pleno funcionamento, com acesso a um banco de dados atualizado de produtos e preços.
- O funcionário do caixa está devidamente autenticado no sistema, com permissões para registrar vendas e processar pagamentos.
- A infraestrutura de pagamento (máquinas de cartão, QR code para Pix, etc.) está funcionando adequadamente.
- As formas de pagamento aceitas (dinheiro, cartão de débito, cartão de crédito, Pix, vale refeição) estão configuradas no sistema.

### Pós-condições:

- A venda é registrada no sistema de ponto de venda (PDV).
- O estoque dos produtos comprados é automaticamente atualizado, refletindo a quantidade vendida.
- Um comprovante de venda é gerado e entregue ao cliente, seja em formato impresso ou digital.
- O pagamento é confirmado e registrado no sistema, com o valor apropriado transferido para a conta da mercearia.
- O histórico de vendas é atualizado, permitindo que o gerente tenha acesso a relatórios financeiros e operacionais precisos.
- O cliente deixa a loja com a certeza de que a compra foi completada com sucesso.

### Questões em aberto:

- **Programa de fidelidade**: O sistema deve permitir a integração de programas de fidelidade, onde o cliente pode acumular pontos ou obter descontos com base em suas compras?
- **Cupom de desconto**: Será possível aplicar cupons de desconto antes de finalizar a venda? E como o sistema lidará com múltiplos cupons?
- **Pagamentos parciais**: Como o sistema deve lidar com pagamentos que envolvam mais de uma forma de pagamento, como metade em dinheiro e metade no cartão?
- **Devolução de produtos**: Como o sistema deve tratar a devolução de produtos, seja após a finalização da compra ou dentro de um período estipulado?

### Fluxo Principal:

1. **Cliente seleciona os produtos**  
   O cliente escolhe os produtos desejados e os leva ao caixa da mercearia.

2. **Funcionário registra os itens**  
   [IN] O funcionário escaneia os códigos de barra dos produtos ou os insere manualmente no sistema, um a um. O sistema confirma o registro de cada item e atualiza a lista de produtos na tela.

3. **Sistema exibe o valor total**  
   [OUT] O sistema calcula o valor total da compra, somando os preços dos produtos e aplicando eventuais descontos ou impostos. Esse valor total é exibido na tela do sistema e para o cliente.

4. **Funcionário pergunta a forma de pagamento**  
   [IN] O funcionário confirma o valor total com o cliente e pergunta qual a forma de pagamento preferida.

5. **Sistema exibe opções de pagamento**  
   [OUT] O sistema exibe as formas de pagamento disponíveis:  
   5.1. Dinheiro  
   5.2. Cartão de débito  
   5.3. Cartão de crédito  
   5.4. Pix  
   5.5. Vale refeição  

6. **Cliente realiza o pagamento**  
   [IN] O cliente escolhe a forma de pagamento preferida. O sistema processa o pagamento com base na escolha do cliente.

   6.1. **Pagamento com dinheiro**  
   O cliente entrega o dinheiro ao funcionário, que registra o valor no sistema.

   6.2. **Pagamento com cartão de débito**  
   O cliente insere o cartão na máquina ou utiliza pagamento por aproximação (NFC). O sistema envia os dados à operadora de cartões, que processa a transação.

   6.3. **Pagamento com cartão de crédito**  
   O cliente insere o cartão ou aproxima para pagamento por NFC. O sistema oferece a opção de parcelamento (se aplicável). Após a escolha do cliente, o sistema envia os dados à operadora de cartões para autorização.

   6.4. **Pagamento com Pix**  
   O sistema gera um QR code ou chave Pix. O cliente faz o pagamento via aplicativo bancário e o sistema confirma o recebimento.

   6.5. **Pagamento com vale refeição**  
   O cliente usa o cartão de vale refeição na máquina ou aproxima para pagamento por NFC. O sistema envia os dados à operadora de pagamentos.

7. **Funcionário confirma o pagamento**  
   [OUT] O sistema confirma a transação e finaliza a venda. Um comprovante é gerado.

8. **Entrega do comprovante**  
   [IN] O funcionário entrega o comprovante de pagamento ao cliente, junto com o troco, se aplicável.

### Variantes:

#### 6.1 Pagamento com dinheiro

1. O cliente entrega o valor em dinheiro ao funcionário.
2. O funcionário insere o valor recebido no sistema.
3. O sistema calcula e exibe o troco, se houver.
4. O funcionário entrega o troco ao cliente.
5. O sistema finaliza a venda e gera o comprovante.

#### 6.2 Pagamento com cartão de débito

1. O cliente insere o cartão na máquina ou aproxima para pagamento por NFC.
2. O sistema envia os dados do cartão para a operadora de pagamentos.
3. A operadora autoriza o pagamento.
4. O sistema registra o pagamento e finaliza a venda.

#### 6.3 Pagamento com cartão de crédito

1. O cliente insere o cartão ou aproxima para pagamento por NFC.
2. O sistema exibe as opções de parcelamento (se aplicável).
3. O cliente escolhe a opção de parcelamento.
4. O sistema envia os dados à operadora de cartões.
5. A operadora autoriza o pagamento.
6. O sistema registra o pagamento e finaliza a venda.

#### 6.4 Pagamento com Pix

1. O sistema gera um QR code ou chave Pix.
2. O cliente realiza o pagamento via aplicativo bancário.
3. A operadora de pagamento confirma o recebimento.
4. O sistema registra o pagamento e finaliza a venda.

#### 6.5 Pagamento com vale refeição

1. O cliente insere o cartão de vale refeição na máquina ou aproxima para pagamento por NFC.
2. O sistema envia os dados do cartão para a operadora de pagamentos.
3. A operadora autoriza o pagamento.
4. O sistema registra o pagamento e finaliza a venda.

### Exceções:

#### E1. Produto não registrado no sistema

- O funcionário tenta registrar um item que não está cadastrado no sistema.
- [OUT] O sistema exibe uma mensagem de erro.
- O funcionário comunica ao cliente e segue as políticas da loja, como verificar o cadastro ou cancelar a venda.

#### E2. Falha na autorização do pagamento (qualquer método de pagamento)

- O sistema não recebe autorização da operadora de pagamento.
- [OUT] O sistema exibe uma mensagem de erro.
- O funcionário informa o cliente e pede que escolha outra forma de pagamento.

#### E3. Falta de troco para pagamento em dinheiro

- O sistema avisa ao funcionário que não há troco suficiente.
- O funcionário informa o cliente e sugere uma alternativa, como pagar o restante com outra forma de pagamento.
