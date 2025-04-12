# 🛒 Resumo Conceitual do Modelo E-COMMERCE

Este modelo representa a estrutura de um sistema de e-commerce com suporte a **clientes, vendedores terceiros, fornecedores, estoque distribuído, pedidos, pagamentos e entregas**.

---

## 👤 Cliente
- Pode ser pessoa física ou jurídica (CPF/CNPJ).
- Possui múltiplos endereços e formas de pagamento salvas.
- Pode definir uma forma de pagamento como preferencial.

---

## 🛍️ Produto
- Cadastrado por fornecedores ou vendedores terceiros.
- Contém informações como nome, descrição, valor, marca e categoria.
- Associado a múltiplos estoques via relação intermediária.

---

## 🏬 Estoque
- Controla a quantidade disponível por local físico.
- Relacionado a produtos por meio de `Produto_has_Estoque`.

---

## 📦 Pedido
- Realizado por um cliente.
- Contém múltiplos produtos com suas quantidades.
- Associado a uma ou mais formas de pagamento.

---

## 💳 Pagamento
- Armazena os dados de pagamento de cada pedido.
- Usa uma forma de pagamento previamente cadastrada pelo cliente.

---

## 🚚 Entrega
- Relacionada ao pedido e a um endereço.
- Registra código de rastreamento, status e datas de envio/entrega.

---

## 🧾 Fornecedores e Vendedores
- **Fornecedores** disponibilizam produtos ao sistema.
- **Vendedores terceiros** cadastram e vendem seus próprios produtos com controle de preço e descrição.
