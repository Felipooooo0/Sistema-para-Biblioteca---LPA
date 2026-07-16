# Descrição do Banco De Dados
create database BallBreaker_Biblioteca;
 
use BallBreaker_Biblioteca;
 
-- Tabela usuario

CREATE TABLE Usuario (
    id_usuario INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    senha VARCHAR(255) NOT NULL,
    nivel_acesso VARCHAR(20) NOT NULL DEFAULT 'cliente',
    data_cadastro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
 
-- Tabela livro

CREATE TABLE Livro (
    id_livro INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    caminho_arquivo VARCHAR(255),
    status_disponibilidade VARCHAR(20) NOT NULL DEFAULT 'disponivel'
);
 
-- Tabela emprestimo

CREATE TABLE Emprestimo (
    id_emprestimo INT AUTO_INCREMENT PRIMARY KEY,
    id_usuario INT NOT NULL,
    id_livro INT NOT NULL,
    data_solicitacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    data_aprovacao TIMESTAMP NULL,
    data_devolucao TIMESTAMP NULL,
    status VARCHAR(20) NOT NULL DEFAULT 'pendente',
    FOREIGN KEY (id_usuario) REFERENCES Usuario(id_usuario) ON DELETE CASCADE,
    FOREIGN KEY (id_livro) REFERENCES Livro(id_livro) ON DELETE CASCADE
);
 
-- Tabela historico

CREATE TABLE Historico_Mudancas (
    id_historico INT AUTO_INCREMENT PRIMARY KEY,
    id_usuario_autor INT NOT NULL,
    acao_realizada VARCHAR(255) NOT NULL,
    tabela_afetada VARCHAR(50) NOT NULL,
    data_hora TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_usuario_autor) REFERENCES Usuario(id_usuario) ON DELETE RESTRICT
);
 
 
 
-- Criando as restrições (check)
 
-- O nivel de acesso

ALTER TABLE Usuario
ADD CONSTRAINT chk_nivel_acesso 
CHECK (nivel_acesso IN ('cliente', 'funcio', 'admin'));
 
-- Emprestimo com data menor ou igual

ALTER TABLE Emprestimo
ADD CONSTRAINT chk_datas_emprestimo 
CHECK (data_devolucao >= data_solicitacao);


