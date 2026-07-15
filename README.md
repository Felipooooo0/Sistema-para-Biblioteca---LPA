# ////////// EM CONSTRUÇÃO //////////////


# Ball Breaker
 **felipe gabriel rossetto / jônatas levi inacio orica
 
 **sistema para um biblioteca *Digital*
 
 **inicialmente estamos pensando em usar o que foi feito em aula: python, FastApi e MySql

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
4. `Historico_Mudancas`): Tabela de auditoria isolada. Registra exclusivamente as ações gerenciais feitas por Funcionários e Admins. Armazena o ID do funcionário, a ação realizada (ex: "Aprovou empréstimo X", "Deletou livro Y", "Criou novo funcionário"), a tabela afetada e a data/hora exata do evento.

/////////////////////////////////////////////////// EM CONTRUÇÃO /////////////////////////////////////////////////////////

# Requisitos funcionais:

# Cliente:
RF01 - Visualização de Catálogo: O sistema deve permitir que o Cliente visualize a lista de e-books disponíveis, incluindo título, autor e sinopse.

RF02 - Solicitação de Empréstimo: O Cliente deve poder solicitar o empréstimo de um e-book disponível no catálogo.

RF03 - Painel do Leitor (Minha Estante): O sistema deve exibir os e-books com acesso ativo do Cliente, detalhando a data de retirada e o prazo limite de devolução.

RF04 - Devolução Antecipada: O Cliente deve poder encerrar o empréstimo de um livro antes do prazo estipulado, liberando seu limite de acessos.

RF05 - Histórico de Leitura: O sistema deve exibir uma lista de todos os e-books cujo empréstimo já foi finalizado ou expirou para aquele usuário.


# Funcionário:

RF06 - Gerenciamento de Solicitações: O Funcionário deve poder visualizar todas as solicitações pendentes e aprová-las ou rejeitá-las.

RF07 - Definição de Prazos de Empréstimo: Ao aprovar uma solicitação, o Funcionário deve obrigatoriamente definir a data limite para a devolução (expiração do acesso).

RF08 - Cadastro de Acervo (CRUD de Livros): O Funcionário deve poder cadastrar novos e-books, atualizar informações existentes (capa, sinopse, link do arquivo) e remover livros obsoletos do catálogo.

RF09 - Revogação Manual de Empréstimo: O Funcionário deve poder encerrar o acesso de um cliente a um e-book ativo de forma manual a qualquer momento.


# Admin:

RF10 - Gestão de Usuários (CRUD de Usuários): O Administrador deve poder criar, visualizar, editar e excluir contas de Clientes, Funcionários e outros Administradores.

RF11 - Auditoria de Catálogo: O Administrador deve poder auditar todas as alterações feitas no catálogo de livros por outros funcionários.

RF12 - Visualização de Logs: O Administrador deve ter acesso exclusivo a uma tela para visualizar a tabela Historico_Mudancas (quem fez o quê, quando e onde).


# Backend:

RF13 - Verificação e Revogação Automática: O sistema deve executar uma rotina diária (ou em tempo real) para identificar empréstimos ativos que ultrapassaram a data de devolução, alterando seu status para "Expirado/Devolvido" e bloqueando o acesso do cliente ao link/arquivo.

RF14 - Registro de Auditoria (Logs automáticos): O sistema deve registrar automaticamente na tabela Historico_Mudancas qualquer ação de criação, edição, exclusão ou alteração de status realizada por Funcionários e Administradores.

# Requisitos não funcionais:

RNF01 - Criptografia de Senhas: Todas as senhas dos usuários devem ser armazenadas no banco de dados utilizando algoritmos de hash seguros (ex: bcrypt ou Argon2). O sistema nunca deve armazenar senhas em texto puro.

RNF02 - Controle de Acesso Baseado em Perfis (RBAC): O sistema deve garantir estritamente que um Cliente não acesse funções de Funcionário/Admin, e que um Funcionário não acesse funções exclusivas de Admin (como logs e gestão de usuários).

RNF03 - Proteção de Arquivos (Links de Acesso): O link do e-book armazenado na tabela Livros não deve ser exposto publicamente. O acesso ao arquivo deve ser validado via token temporário ou assinatura, garantindo que apenas usuários com empréstimo ativo possam abrir o documento.

RNF04 - Integridade Referencial no Banco de Dados: O banco de dados deve utilizar chaves estrangeiras (Foreign Keys) bem estruturadas para garantir que a exclusão de um usuário ou livro trate corretamente os empréstimos ativos (ex: impedir exclusão física de livros que possuem empréstimos ativos).

RNF05 - Imutabilidade dos Logs: A tabela Historico_Mudancas deve ser estritamente de "inserção apenas" (append-only). Nenhum usuário (nem mesmo o Administrador) deve ter permissão dentro da aplicação para editar ou deletar registros dessa tabela.

RNF06 - Disponibilidade da Rotina Back-end: A automação de devolução (cron job / script diário) deve ser tolerante a falhas, gerando alertas para a equipe de TI caso a execução diária falhe.

RNF07 - Design Responsivo: A interface do sistema deve ser adaptável, permitindo que os Clientes leiam ou solicitem livros tanto em computadores quanto em dispositivos móveis (smartphones e tablets).
