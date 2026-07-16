# Descrição do Banco De Dados
1. Usuarios: Armazena apenas os dados cadastrais essenciais de Clientes, Funcionários e Admins (ex: nome, email, senha criptografada e a coluna de nivel_acesso).
2. Livros: Armazena os metadados do acervo de e-books (Título, Autor, Caminho do Arquivo/Link, Status de disponibilidade).
3. Emprestimos: Tabela transacional que conecta Usuarios e Livros (gerenciando o acesso digital temporário). Contém data_solicitacao, data_aprovacao, data_devolucao e status (Pendente, Ativo, Expirado/Devolvido).
4. Historico_Mudancas): Tabela de auditoria isolada. Registra exclusivamente as ações gerenciais feitas por Funcionários e Admins. Armazena o ID do funcionário, a ação realizada (ex: "Aprovou empréstimo X", "Deletou livro Y", "Criou novo funcionário"), a tabela afetada e a data/hora exata do evento.

# Representação do DER da biblioteca
![Página Inicial - Parte 1](https://github.com/Felipooooo0/Sistema-para-Biblioteca---LPA/blob/main/DocumentoProjeto/assets/WhatsApp%20Image%202026-07-15%20at%2020.06.35.jpeg)

# Reprensentação do Diagrama de Caso de Uso
![Página Inicial - Parte 1](https://github.com/Felipooooo0/Sistema-para-Biblioteca---LPA/blob/main/DocumentoProjeto/assets/WhatsApp%20Image%202026-07-15%20at%2019.53.59.jpeg)



