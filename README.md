# OFICINA-EER-DIAGRAM


<h2>Modelo EER (Extended-Entity Relationship)</h2>


![DIAGRAMA OFICINA FINAL](https://github.com/user-attachments/assets/815df665-bb25-401c-928d-4f3f2fb504cd)

<p>

<h3>RESUMO:</h3>

O diagrama representa um banco de dados relacional para um sistema de gerenciamento de oficina mecânica. Ele contém diversas tabelas interligadas por relacionamentos, modelando clientes, carros, serviços, ordens de serviço, mecânicos e peças.<br>



<b>Tabelas e Relacionamentos</b>

<b>1. CLIENTE</b>

- Chave Primária: CPF
- Contém dados do cliente, como nome, sobrenome, endereço e data de nascimento.
- Relacionamento: Um cliente pode possuir múltiplos carros (1:N com a tabela CARRO).
 
<b>2. CARRO</b>

- Chave Primária: PLACA
- Contém informações sobre os carros, incluindo marca, modelo, cor e ano do veículo.
- Possui uma chave estrangeira CLIENTE_CPF referenciando a tabela CLIENTE.
- Relacionamento: Um cliente pode ter vários carros (1:N), mas um carro pertence a um único cliente.

<b>3. SERVIÇO</b>

- Chave Primária: ID_SERVICO
- Contém descrição do serviço e tipo do serviço.
- Possui uma chave estrangeira CARRO_PLACA para indicar a qual carro o serviço pertence.
- Também contém EQUIPE_MECANICOS_ID_EQUIPE, que vincula o serviço a uma equipe de mecânicos.

Relacionamento:
- Um carro pode passar por vários serviços (1:N com CARRO).
- Um serviço é realizado por uma equipe de mecânicos (N:1 com EQUIPE_MECANICOS).

<b>4. EQUIPE_MECANICOS</b>

- Chave Primária: ID_EQUIPE
- Contém o número de integrantes da equipe.

Relacionamento:
- Uma equipe pode executar vários serviços (1:N com SERVIÇO).
- Uma equipe pode ter múltiplos mecânicos (1:N com MECANICO).

<b>5. MECANICO</b>

- Chave Primária: COD_MECANICO
- Contém informações pessoais do mecânico e sua especialidade.
- Possui uma chave estrangeira EQUIPE_MECANICOS_ID_EQUIPE para indicar a qual equipe pertence.
- 
Relacionamento:
- Um mecânico pertence a apenas uma equipe (N:1 com EQUIPE_MECANICOS).
- Uma equipe pode ter vários mecânicos (1:N).

<b>6. ORDEM_SERVICO</b>
 
- Chave Primária: NUMERO_ORDEM
- Contém informações como data de emissão, valor das peças, valor da mão de obra, status e data de entrega.

Relacionamento:
- Uma ordem de serviço pode incluir vários serviços (1:N com SERVICOS_INCLUSOS).
- Uma ordem de serviço pode conter várias peças (1:N com PECAS_INCLUSAS).
- Uma ordem de serviço pode incluir múltiplas tarefas de mão de obra (1:N com MAO_DE_OBRA_OS).

<b>9. SERVICOS_INCLUSOS</b>
   
- Chave Estrangeira: ORDEM_SERVICO_NUMERO_ORDEM e SERVICO_ID_SERVICO

Relacionamento:
- Ligação N:M entre ORDEM_SERVICO e SERVICO, pois uma ordem pode conter vários serviços, e um serviço pode estar em várias ordens.

11. PECAS_INCLUSAS

- Chave Estrangeira: ORDEM_SERVICO_NUMERO_ORDEM e PECAS_VEICULO_ID_PECA

Relacionamento:
- Ligação N:M entre ORDEM_SERVICO e PECAS_VEICULO, pois uma ordem pode incluir várias peças, e uma peça pode estar em várias ordens.

13. PECAS_VEICULO

- Chave Primária: ID_PECA
- Contém informações como tipo, preço e modelo do veículo compatível.

Relacionamento:
- Uma peça pode estar em várias ordens (1:N com PECAS_INCLUSAS).

<b>15. MAO_DE_OBRA</b>

- Chave Primária: COD_PROCEDIMENTO
- Contém descrição e preço do procedimento.
  
Relacionamento:
- Uma tarefa de mão de obra pode ser usada em várias ordens de serviço (1:N com MAO_DE_OBRA_OS).
  
<b>17. MAO_DE_OBRA_OS</b>

- Chave Estrangeira: ORDEM_SERVICO_NUMERO_ORDEM e MAO_DE_OBRA_COD_PROCEDIMENTO
  
Relacionamento:
- Ligação N:M entre ORDEM_SERVICO e MAO_DE_OBRA, pois uma ordem pode conter vários procedimentos de mão de obra.


<b>Resumo das Cardinalidades</b>

<b>1:N</b>
- CLIENTE → CARRO
- CARRO → SERVICO
- EQUIPE_MECANICOS → SERVICO
- EQUIPE_MECANICOS → MECANICO
- ORDEM_SERVICO → SERVICOS_INCLUSOS
- ORDEM_SERVICO → PECAS_INCLUSAS
- ORDEM_SERVICO → MAO_DE_OBRA_OS
  
<b>N:M</b>

- ORDEM_SERVICO ↔ SERVICO (via SERVICOS_INCLUSOS)
- ORDEM_SERVICO ↔ PECAS_VEICULO (via PECAS_INCLUSAS)
- ORDEM_SERVICO ↔ MAO_DE_OBRA (via MAO_DE_OBRA_OS)
  
</p>
