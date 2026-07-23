# Ball Breaker

> **Projeto em construção**

## Integrantes

- Felipe Gabriel Rossetto
- Jônatas Levi Inacio Orica

## Sobre o Projeto

O **Ball Breaker** é um sistema para gerenciamento de uma **biblioteca virtual**, permitindo que usuários acessem um catálogo digital de e-books e que funcionários realizem o gerenciamento do acervo.

Inicialmente, o projeto será desenvolvido utilizando as tecnologias apresentadas em aula:

- Python
- FastAPI
- MySQL

> As ideias do projeto foram desenvolvidas por Felipe e Jônatas. A Inteligência Artificial foi utilizada apenas para revisão e organização deste README.

---

# Estrutura do Sistema

O sistema será dividido em diferentes níveis de acesso, garantindo segurança e organização.

## Cliente

### Funcionalidades

- Visualizar o catálogo de e-books disponíveis. 
- Consultar o histórico de leitura. 
- Adicionar livros aos favoritos.
- Acessar o conteúdo dos e-books para leitura.

---

## Funcionário

### Funcionalidades

- Adicionar novos e-books ao catálogo.
- Atualizar informações dos livros (sinopse, capa e arquivo).
- Remover livros do catálogo.

**Status:** Implementação iniciada.

---

# Requisitos Funcionais

| Código | Descrição | Status |
|--------|-----------|--------|
| RF01 | O sistema deve permitir que o cliente visualize os e-books disponíveis, incluindo título, autor e sinopse. 
| RF02 | O sistema deve exibir os e-books com acesso ativo do cliente. 
| RF03 | O sistema deve exibir o histórico de livros já lidos pelo usuário.
| RF04 | O funcionário deve cadastrar, editar e remover e-books do catálogo. 
| RF05 | O sistema deve permitir que o usuário adicione livros aos favoritos. 
| RF06 | O sistema deve permitir que o usuário acesse o conteúdo do e-book para leitura. 
| RF07 | O sistema deve permitir que o usuário avalie os livros lidos.
| RF08 | O sistema deve permitir que o usuário consiga mudar sua senha.
| RF09 | O sistema deve impedir o download dos e-books pelos usuários.
| RF10 | O sistema deve garantir que os funcionários possuam todas as permissões disponíveis para os clientes.

---

# Requisitos Não Funcionais

| Código | Descrição |
|--------|-----------|
| RNF01 | As senhas dos usuários devem ser armazenadas utilizando algoritmos seguros de hash, como **bcrypt** ou **Argon2**, nunca em texto puro. |
| RNF02 | O sistema deve garantir controle de acesso por níveis de permissão, impedindo que clientes acessem funcionalidades de funcionários ou administradores. |
| RNF03 | O link do e-book não deve ser exposto publicamente. O acesso deverá ocorrer por meio de token temporário ou assinatura válida. |
| RNF04 | O banco de dados deverá utilizar **Foreign Keys** para garantir integridade referencial entre as tabelas. |
| RNF05 | As imagens de capas e os arquivos PDF deverão ser armazenados externamente (URL ou serviço de armazenamento), evitando armazená-los diretamente no banco de dados. |

---

# Tecnologias

- Python
- FastAPI
- MySQL
- HTML
  

---

# Status do Projeto

Atualmente o projeto encontra-se em desenvolvimento e novas funcionalidades serão adicionadas conforme o andamento da disciplina.
