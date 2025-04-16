# 🧠 Resumo Conceitual – Modelo Relacional: Sistema de Ordem de Serviço (Oficina Mecânica)

Este modelo representa um sistema de gerenciamento de ordens de serviço em uma oficina mecânica, voltado para o registro, controle e execução de serviços automotivos (consertos ou revisões), incluindo mão de obra e peças utilizadas.

---

## 📌 Principais Entidades e Relacionamentos

### 🔸 Cliente
- Representa os clientes que levam veículos à oficina.
- Um cliente pode possuir múltiplos veículos.

### 🔸 Veículo
- Contém informações do carro (modelo, placa, ano).
- Cada veículo pertence a um cliente e pode gerar várias ordens de serviço.

### 🔸 Ordem de Serviço (OS)
- Documento que registra a execução de um ou mais serviços em um veículo.
- Contém status, datas, valor total, autorização e associação a uma equipe de mecânicos.

### 🔸 Serviço
- Define a natureza da OS: Conserto ou Revisão.
- Descreve serviços específicos realizados na OS (ex: troca de óleo, alinhamento).
- Serve como base para determinar o custo da mão de obra, vinculado à tabela de referência.

### 🔸 Tabela de Mão de Obra
- Armazena os valores da mão de obra referentes a cada tipo de serviço, considerando vigência.
- Permite histórico e flexibilidade de atualização de preços.
- Associada ao `Tipo de Serviço` .
- Consultada no momento da emissão da OS.

### 🔸 Peça
- Representa os componentes utilizados em consertos.
- Cada OS pode conter várias peças e cada peça pode aparecer em várias OS.
- A tabela associativa registra quantidade e valor total por peça na OS.

### 🔸 Equipe
- Grupo de mecânicos responsáveis por avaliar e executar os serviços.
- Cada equipe pode estar em várias OS e é composta por vários mecânicos.

### 🔸 Mecânico
- Profissionais que atuam na execução de serviços.
- Podem participar de múltiplas equipes e ordens de serviço, com especialidades distintas.

---

## ⚙️ Lógicas de Negócio

- Uma **OS** só pode ser autorizada após ser avaliada por uma **equipe**.
- O valor total da OS é composto pelo **valor da mão de obra** (consultado na tabela de referência) somado ao **valor das peças utilizadas**.
- O **tipo de serviço** define se peças serão necessárias (apenas em caso de consertos).


---
