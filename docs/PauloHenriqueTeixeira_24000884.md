# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Paulo Henrique Teixeira
RA: 24000884
Data: 26/03/2026  

---

# 1. Definição do MVP
Meu MVP inclui o processo de venda, da identificação ou cadastro do cliente até emissão de comprovante,
cadastro de estoque e tratamento de estoque insuficiente,
cadastros de vendas e compras à prazo e registros de contas à pagar e à receber. 

# 2. Regras de Negócio (mínimo: 5)

**RN01 —**  Não é permitida a venda de produtos cuja quantidade ultrapasse o estoque disponível;
**RN02 —**  Vendas de medicamentos controlados exigem validação de um farmacêutico com apresentação de receita médica;
**RN03 —**  Toda venda à prazo deve gerar uma conta à receber de maneira automática;
**RN04 —**  Toda compra à prazo deve gerar uma conta à pagar de maneira automática;
**RN05 —**  O estoque deve ser atualizado de maneira automática;
**RN06 —**  Uma venda à prazo não pode ter data de pagamento que ultrapasse 30 dias após a data da venda. 

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 —**  O sistema deve incluir cadastro, exclusão e atualização de produtos;
**RF02 —**  O sistema deve incluir cadastro, exclusão e atualização de clientes;
**RF03 —**  O cadastro de produtos deve exigir nome, descrição, código de barras e foto;
**RF04 —**  O sistema de busca de produtos deve ser dinâmico de forma que encontre produtos que contenham as palavras pesquisadas em qualquer coluna;
**RF05 —**  Vendas à prazo devem gerar notificações de necessidade a partir de 3 dias antes da data limite do pagamento;
**RF06 —**  Compras à prazo devem gerar notificações de necessidade a partir de 3 dias antes da data limite do pagamento;
**RF07 —**  A tabela de produtos também deve ter a funcionalidade de ordenação alfabética e alfabética inversa por qualquer coluna clicada 
**RF08 —**  A tela de vendas deve amostrar uma imagem do produto incluído na lista ao lado de cada linha de produto da lista de inclusos na compra

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —** O sistema deve levar no máximo 2 segundos por consulta de qualquer item, produto, fornecedor, cliente ou qualquer outro registro;   
**RNF02 —** O sistema deve manter cache de informações recentemente utilizadas;
**RNF03 —** O sistema deve recuperar dados de tela de vendas, cadastros ou registros após recuperação de conexão com a internet após queda, mantendo somente um ícone de carregamento rodando na tela da funcionalidade no meio tempo;
**RNF04 —** O sistema deve suportar a utilização de múltiplos por gerentes na atualização de estoque e registro de produtos sem conflitos.

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso
---

## **UC01 — Realizar Venda**
**Ator(es):** Atendente  
**Descrição:**  Realização de venda
**Pré-condições:**  Usuário autenticado e produtos cadastrados
**Pós-condições:**  Estoque atualizado, venda registrada e comprovante emitido

### Fluxo Principal
1.  Atendente inicia a venda
2.  Sistema solicita a identificação do cliente
3.  Atendente informa cliente
4.  Sistema permite consulta de produtos
5.  Atendente seleciona produto e quantidade
6.  Sistema verifica estoque
7.  Sistema calcula valor total
8.  Atendente finaliza venda
9.  Sistema registra venda e atualiza estoque
10.  Sistema emite comprovante

### Fluxos Alternativos / Exceções
- FA01 —  Cliente não cadastrado: sistema permite cadastro
- FA02 —  Estoque insuficiente: sistema bloqueia venda

### Relacionamentos
- **Include:** Identificar cliente, Consultar produto, Verificar estoque
- **Extend:** Validar receita, Registrar conta a receber

## DIAGRAMA:



## **UC02 — Identificar Cliente**
**Ator(es):** Atendente  
**Descrição:**  Identificação ou cadastro de cliente
**Pré-condições:**  Sistema ativo e conectado
**Pós-condições:**  Dados de cliente validados.

### Fluxo Principal
1.  Atendente informa dados do cliente no sistema;
2.  Sistema busca cliente
3.  Sistema exibe todos os dados do cliente 

### Fluxos Alternativos / Exceções
- FA01 —  Cliente não encontrado: permite cadastro

## DIAGRAMA:



## **UC03 — Consultar Produto**
**Ator(es):** Atendente  
**Descrição:**  Busca de produto no sistema
**Pré-condições:**  Produtos cadastrados
**Pós-condições:**  Produto é exibido

### Fluxo Principal
1.  Sistema abre tela de produtos
2.  Atendente insere no sistema na barra de busca os dados do produto
3.  Sistema exibe produtos que possuem atributos que batem com a busca

### Fluxos Alternativos / Exceções
- FA01 —  Produto não cadastrado: sistema informa "Produto não encontrado" e exibe botão de cadastro de produtos em destaque

## DIAGRAMA:



## **UC04 — Verificar Estoque**
**Ator(es):** Sistema
**Descrição:**  Verificação de estoque disponível
**Pré-condições:**  Produto selecionado
**Pós-condições:**  Quantidade validada

### Fluxo Principal
1.  Sistema recebe produto e quantidade informada;
2.  Sistema busca estoque
3.  Sistema retorna se há disponíveis

### Fluxos Alternativos / Exceções
- FA02 —  Estoque insuficiente: sistema informa indisponibilidade

## DIAGRAMA:



## **UC05 — Realizar Venda**
**Ator(es):** Farmacêutico  
**Descrição:**  Validar receita
**Pré-condições:**  Produto controlado selecionado
**Pós-condições:**  Validade da receita verificada

### Fluxo Principal
1.  Sistema solicita validação;
2.  Farmacêutico analisa receita
3.  Farmaceutico aprova ou reprova

### Fluxos Alternativos / Exceções
- FA01 —  Recentia inválida: venda bloqueada
  
### Relacionamentos
- **Extend:** Realizar venda

## DIAGRAMA:



 ## **UC06 — Registro de conta à receber**
**Ator(es):** Sistema
**Descrição:**  Registra venda à prazo
**Pré-condições:**  Venda à prazo
**Pós-condições:**  Registro de conta à receber

### Fluxo Principal
1.  Sistema identifica venda à prazo
2.  Sistema gera conta
3.  Sistema registra vencimento

### Fluxos Alternativos / Exceções
- FA01 —  Pagamento com data que ultrapassa 30 dias após a venda: Sistema bloqueia a  venda
 
### Relacionamentos
- **Extend:** Realizar Venda

## DIAGRAMA



## **UC07 — Notificar estoque baixo**
**Ator(es):** Sistema
**Descrição:**  Notificação de estoque baixo
**Pré-condições:**  Estoque abaixo do nível mínimo
**Pós-condições:**  Notificação gerada

### Fluxo Principal
1.  Sistema identifica estoque baixo
2.  Sistema gera alerta
3.  Sistema notifica gerente

### Fluxos Alternativos / Exceções
- FA01 —  Falha na notificação: Sistema registra erro

### Relacionamentos
- **Extend:** Atualizar estoque

## DIAGRAMA:



 ## **UC08 — Gerenciar Usuários**
**Ator(es):** Adaministrador
**Descrição:**  Cadastro, remoção e atualização de usuários
**Pré-condições:**  Administrador autenticado
**Pós-condições:**  Tabela de usuários alterada

### Fluxo Principal
1.  Administrador acessa o gerenciamento
2.  Sistema exibe usuários cadastrados
3.  Administrador atualiza/remove/cadastra usuário
4.  Sistema salva alterações.

### Fluxos Alternativos / Exceções
- FA01 —  Dados não válidos: sistema solicita correção

## **UC09 — Registrar  Compra**
**Ator(es):** Gerente
**Descrição:**  Realização de compra e registro
**Pré-condições:**  Fornecedor cadastrado
**Pós-condições:**  Compra registrada, estoque atualizado, conta a pagar registrada

### Fluxo Principal
1.  Gerente informa compta
2.  Sistema registra itens
3.  Sistema atualiza estoque
4.  Sistema registra conta à pagar

### Fluxos Alternativos / Exceções
- FA01 —  Erro nos dados: sistema bloqueia registro

### Relacionamentos
- **Include:** Atualizar estoque, Registrar conta a pagar

## DIAGRAMA



## **UC10 — Consultar contas a pagar e receber**
**Ator(es):** Financeiro
**Descrição:**  Consulta lançamento de contas e vendas à prazo
**Pré-condições:**  Usuário com Perfil financeiro autenticado, contas existentes
**Pós-condições:**  Contas cadastradas exibidas e com status atualizados

### Fluxo Principal
1.  Financeiro autentica no sistema
2.  Financeiro acessa contas
3.  Sistema exibe filtros de consulta (Por unidade, tipo, data, fornecedor, cliente e etc.)
4.  Financeiro escolhe filtros 
5.  Sistema exibe contas

### Fluxos Alternativos / Exceções
- FA01 —  Sem dados: sistema informa que não há contas a prazo
- FA02 - Filtro inválido: sistema solicita ajuste

### Relacionamentos
- **Include:** Gerar relatórios

## **UC11 — Gerar relatórios**
**Ator(es):** Financeiro, Gerente
**Descrição:**  geração de relatórios
**Pré-condições:**  Dados registrados e sistema ativo
**Pós-condições:**  Exibição de relatório e de botão de imprimir/exportar

### Fluxo Principal
1.  Financeiro/Gerente autentica no sistema
2.  Financeiro/Gerente seleciona tipo de relatório
3.  Sistema processa dados
4.  Sistema exibe relatório

### Fluxos Alternativos / Exceções
- FA01 —  Sem dados: sistema informa que não há dados solicitados

## DIAGRAMA:



### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).
