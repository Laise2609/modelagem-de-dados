#Comandos SQL para modelagem física

##Criar banco de dados
CREATE DATABASE vendas_laise CHARACTER SET utf8mb4;

##Entrar no banco de dados criado
USE DATABASE vendas_laise;

##Criar tabela fabricantes
CREATE TABLE fabricantes(
    id INT <!--número inteiro--> NOT NULL<!--não está nulo--> AUTO_INCREMENT<!--incrementar sozinho--> PRIMARY KEY<!--chave primária: primeiro "comando"-->, 
    nome VARCHAR(45)<!--texto com limite de 45 palavras--> NOT NULL
);

CREATE TABLE produtos(
    id PRIMARY KEY NOT NULL AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    preco DECIMAL(8,2) NOT NULL,
    quantidade INT,
    descricao TEXT(1000) NOT NULL,
    fabricante_id INT NOT NULL
);

##Alterando a tabela para criar um relacionamento por meio da chave estrangeira
ALTER TABLE produtos 
    ADD CONSTRAINT fk_produtos_fabricantes 
    FOREING KEY(fabricante_id) REFERENCES fabricantes(id);  