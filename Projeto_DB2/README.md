# 🧠 Resumo Conceitual – Modelo Relacional: Sistema de Ordem de Serviço (Oficina Mecânica)

Este modelo representa um sistema de gerenciamento de ordens de serviço em uma oficina mecânica, voltado para o registro, controle e execução de serviços automotivos (consertos ou revisões), incluindo mão de obra e peças utilizadas.

---

## 📌 Principais Entidades e Relacionamentos

### 🔸 Cliente
- Representa os clientes que levam veículos à oficina.
- Um cliente pode possuir múltiplos veículos (1:N).

### 🔸 Veículo
- Contém informações do carro (modelo, placa, ano).
- Cada veículo pertence a um cliente e pode gerar várias ordens de serviço.

### 🔸 Ordem de Serviço (OS)
- Documento que registra a execução de um ou mais serviços em um veículo.
- Contém status, datas, valor total, autorização e associação a uma equipe de mecânicos.
- Cada OS está relacionada a:
  - Um veículo (1:N),
  - Um tipo de serviço (1:N),
  - Uma equipe (1:N),
  - Múltiplas peças e serviços (N:N).

### 🔸 Tipo de Serviço
- Define a natureza da OS: Conserto ou Revisão.
- Serve como base para determinar o custo da mão de obra, vinculado à tabela de referência.

### 🔸 Tabela de Mão de Obra
- Armazena os valores da mão de obra referentes a cada tipo de serviço, considerando vigência.
- Permite histórico e flexibilidade de atualização de preços.
- Associada ao `Tipo de Serviço` (1:N).
- Consultada no momento da emissão da OS, conforme a data vigente.

### 🔸 Peça
- Representa os componentes utilizados em consertos.
- Cada OS pode conter várias peças e cada peça pode aparecer em várias OS (N:N).
- A tabela associativa registra quantidade e valor total por peça na OS.

### 🔸 Serviço
- Descreve serviços específicos realizados na OS (ex: troca de óleo, alinhamento).
- Cada serviço pode estar em múltiplas OS (N:N), com controle de quantidade e subtotal.

### 🔸 Equipe
- Grupo de mecânicos responsáveis por avaliar e executar os serviços.
- Cada equipe pode estar em várias OS e é composta por vários mecânicos (N:N).

### 🔸 Mecânico
- Profissionais que atuam na execução de serviços.
- Podem participar de múltiplas equipes e ordens de serviço, com especialidades distintas.

---

## ⚙️ Lógicas de Negócio

- Uma **OS** só pode ser autorizada após ser avaliada por uma **equipe**.
- O valor total da OS é composto pelo **valor da mão de obra** (consultado na tabela de referência) somado ao **valor das peças utilizadas**.
- O **tipo de serviço** define se peças serão necessárias (apenas para consertos).
- O sistema mantém **histórico de preços** da mão de obra por meio da entidade `Tabela_Mao_de_Obra`.

---