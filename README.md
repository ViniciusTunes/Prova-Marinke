# 🍴 Projeto Banco de Dados - Gerenciador de Restaurante 📊

👋 Olá, Professor Marinke!
Este projeto foi desenvolvido como parte da avaliação prática.

---

# 📖 Sobre o Projeto
O objetivo principal foi criar um sistema de banco de dados funcional para o gerenciamento de um restaurante. Este projeto inclui funcionalidades voltadas para a gestão de mesas, pedidos, produtos e vendas.

Principais características:
Controle de mesas: Status atualizado em tempo real (Livre, Ocupada, Finalizando).
Gestão de pedidos: Associação de produtos com mesas e cálculo automático de valores.
Cadastro de clientes e funcionários: Facilita o acompanhamento detalhado do fluxo de trabalho.
Registro de pagamentos e vendas: Métodos e valores registrados com precisão.

---

# 🔗 Estrutura e Tabelas
O banco de dados foi projetado para ser eficiente e modular, utilizando as seguintes tabelas principais:

Funcionários: Registra os responsáveis pelo atendimento.
Mesas: Monitora ocupação e status.
Clientes: Mantém dados básicos dos clientes.
Produtos: Gerencia estoque e preços.
Pedidos: Relaciona mesas com produtos solicitados.
Produtos_Pedidos: Relacionamento entre pedidos e itens.
Pagamentos: Detalha métodos e valores recebidos.
Vendas: Consolidado das transações por mesa.

---

🔍 Consultas e Procedimentos Implementados
Este sistema permite consultas que facilitam a operação do restaurante.

Exemplo de consulta personalizada:
Total de vendas por funcionário e mesa:

```mysql SELECT 
    f.nome AS Funcionario,
    m.id AS Mesa,
    SUM(p.preco * pp.quantidade) AS Total
FROM 
    funcionarios f
JOIN 
    mesas m ON f.id = m.funcionario_id
JOIN 
    pedidos ped ON m.id = ped.mesa_id
JOIN 
    produtos_pedidos pp ON ped.id = pp.pedido_id
JOIN 
    produtos p ON pp.produto_id = p.id
GROUP BY 
    f.nome, m.id
ORDER BY 
    Total DESC;```
