# ////////// EM CONSTRUÇÃO //////////////


- 
# Ball Breaker
 **felipe gabriel rossetto / jônatas levi inacio orica
 
 **sistema para um biblioteca *Virtual*
 
 **inicialmente estamos pensando em usar o que foi feito em aula: python, FastApi e MySql

#IDEIAS feitas por jonatas e felipe,foi utilizado IA apenas para corrigir e arrumar de forma agradavel no readM
e;
# O sistema é dividido em três níveis de acesso, garantindo segurança e organização do fluxo de trabalho:
# 1. Cliente 

 **Catálogo Digital:** Visualizar todos os e-books disponíveis na plataforma. // feito
 **Histórico de Leitura:** Registro de todos os e-books já lidos na plataforma. //feito

# 2. Funcionário

 **Gestão de Acervo Digital:** Adicionar novos e-books ao catálogo, atualizar sinopses/capas e excluir livros obsoletos. //feito porem falta

# 5. Banco de dados: MySql

# Requisitos funcionais:

RF01 -  O sistema deve permitir que o Cliente visualize a lista de e-books disponíveis, incluindo título, autor e sinopse.

RF02 -  O sistema deve exibir os e-books com acesso ativo do Cliente.

RF03 -  O sistema deve exibir uma lista de todos os e-books cujo empréstimo já foi finalizado ou expirou para aquele usuário.

RF04 -  O Funcionário deve poder cadastrar novos e-books, atualizar informações existentes (capa, sinopse, link do arquivo) e remover livros do catálogo.

RF05 - o sistema deve permitir que o usuario adicione o livro em seus favoritos.

RF06 - o sistema deve permitir o usuario conseguir acesse o conteudo para a leitura.

RF07 - a

# Requisitos não funcionais:

RNF01 - Todas as senhas dos usuários devem ser armazenadas no banco de dados utilizando algoritmos de hash seguros (ex: bcrypt ou Argon2). O sistema nunca deve armazenar senhas em texto puro.

RNF02 -  O sistema deve garantir estritamente que um Cliente não acesse funções de Funcionário/Admin, e que um Funcionário não acesse funções exclusivas de Admin

RNF03 -  O link do e-book armazenado na tabela Livros não deve ser exposto publicamente. O acesso ao arquivo deve ser validado via token temporário ou assinatura, garantindo que apenas usuários com empréstimo ativo possam abrir o documento.

RNF04 -  O banco de dados deve utilizar chaves estrangeiras (Foreign Keys) bem estruturadas para garantir que a exclusão de um usuário ou livro.

RNF05 - As imagens e pdfs devem ser armazenadas numa URL para não ter fotos dentro do banco de dados.


