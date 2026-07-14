# Ball Breaker
# felipe gabriel rossetto / jônatas levi inacio orica
# sistema para um biblioteca *Digital*
# inicialmente estamos pensando em usar o que foi feito em aula: python, FastApi e MySql

#IDEIAS feitas por jonatas e felipe,foi utilizado IA apenas para corrigir e arrumar de forma agradavel no readMe;
# O sistema é dividido em três níveis de acesso, garantindo segurança e organização do fluxo de trabalho:
# 1. Cliente (Leitor)
Focado na exploração do acervo e no consumo do conteúdo digital.
 **Catálogo Digital:** Visualizar todos os e-books disponíveis na plataforma.
 **Solicitação de Empréstimo:** Enviar um pedido formal ao sistema solicitando o acesso a um livro específico.
 **Minha Estante (Dashboard):** Visualizar os livros com acesso atualmente aprovado, mostrando a data de retirada e o tempo restante (data de devolução).
 **Devolução Antecipada:** Botão para "devolver" o livro antes do prazo, liberando o limite do usuário.
 **Histórico de Leitura:** Registro de todos os e-books já lidos na plataforma.

# 2. Funcionário (Curador / Atendimento)
Responsável por mediar o acesso dos clientes e manter o acervo digital atualizado.
 **Painel de Solicitações:** Visualizar, aprovar ou rejeitar pedidos de empréstimos feitos pelos clientes.
 **Definição de Prazos:** Ao aprovar um pedido, o funcionário estipula a "data de devolução" (fim do período de acesso ao arquivo digital).
 **Gestão de Acervo Digital:** Adicionar novos e-books ao catálogo, atualizar sinopses/capas e excluir livros obsoletos.
 **Revogação Manual:** Poder remover o acesso de um cliente a um e-book antes do prazo, em caso de necessidade.

# 3. Administrador (Gestor do Sistema)
Possui controle total sobre a infraestrutura, usuários e regras de negócio.
 **Gestão de Usuários (CRUD completo):** Criar, visualizar, editar ou excluir perfis tanto de **Clientes** quanto de **Funcionários**.
 **Gestão Avançada de Catálogo:** Mesmas permissões de acervo dos funcionários, mas com poder de auditar alterações.
 **Painel de Controle (Logs):** Visualizar o registro de atividades (ex: qual funcionário aprovou qual empréstimo).

# 4. Automações do Sistema (Back-end)
 **Devolução Automática:** Um script que roda diariamente (ou em tempo real) verificando as datas de devolução. Se o prazo de um empréstimo estourou, o sistema altera o status para "Devolvido" e bloqueia o acesso do cliente ao e-book automaticamente.

# 5. Banco de dados
1. `Usuarios`: Armazena apenas os dados cadastrais essenciais de Clientes, Funcionários e Admins (ex: nome, email, senha criptografada e a coluna de `nivel_acesso`).
2. `Livros`: Armazena os metadados do acervo de e-books (Título, Autor, Caminho do Arquivo/Link, Status de disponibilidade).
3. `Emprestimos`: Tabela transacional que conecta `Usuarios` e `Livros` (gerenciando o acesso digital temporário). Contém `data_solicitacao`, `data_aprovacao`, `data_devolucao` e `status` (Pendente, Ativo, Expirado/Devolvido).
4. `Historico_Mudancas` (Atas/Logs): Tabela de auditoria isolada. Registra exclusivamente as ações gerenciais feitas por Funcionários e Admins. Armazena o ID do funcionário, a ação realizada (ex: "Aprovou empréstimo X", "Deletou livro Y", "Criou novo funcionário"), a tabela afetada e a data/hora exata do evento.

/////////////////////////////////////////////////// EM CONTRUÇÃO /////////////////////////////////////////////////////////
