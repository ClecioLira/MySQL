# MySQL
- DDL = Definição = CREATE TABLE, CREATE DATABASE, ALTER TABLE, DROP TABLE
- DML = Manipulação = INSERT INTO, UPDATE, DELETE, TRUNCATE
- DQL = Solicitações

Banco de dados tem Tabelas
Tabelas tem Registros
Registros tem Campos

Registros, Linhas e Tuplas são a mesma coisa.

# Tipos primitivos
Numérico = 
    inteiro = TinyInt, SmallInt, Int, MediumInt, BigInt.
    real = Decimal, Float, Double, Real
    lógico = Bit, Boolean

Data/ Tempo = Date, DateTime, Timestamp, Time, Year

Literal = 
    caractere = Char, VarChar
    texto = TinyText, Text, MediumText, LongText
    binario = TinyBlob, Blob, MediumBlob, LongBlob
    coleção = Enum, Set

Espacial = Geomatry, Point, Polygon, MultiPolygon

# Comandos
create database "nome do banco de dados" = criar um novo banco de dados
    EX: CREATE DATABASE cadastro;

create table "nome da tabela" ("aqui fica todas as colunas e tipos da tabela"); = criar tabela
    EX: CREATE TABLE pessoas;

CREATE TABLE IF NOT EXISTS "nome da tabela" ("aqui fica todas as colunas e tipos da tabela"); = criar uma tabela se ela não existir
    EX: CREATE TABLE IF NOT EXISTS cursos (
    nome VARCHAR(30) NOT NULL UNIQUE,
    descricao TEXT,
    carga INT UNSIGNED,
    totaulas INT UNSIGNED,
    ano YEAR DEFAULT '2024'
    );

describe "nome da tabela" = mostrar a tabela
    EX: DESC pessoas;

drop database "nome do banco de dados" = apaga o banco de dados selecionado
    EX: DROP DATABASE cadastro;

default character set utf8 
default collate utf8_general_ci; = conjunto de caracteres padrão que vão ser suportados

INSERT INTO "nome da tabela"
(id, nome, nascimento, sexo, peso, altura, nacionalidade)
VALUES
('1', 'Clécio', '2002-01-03', 'M', '60.4', '1.70', 'Brasil');

ou 

INSERT INTO PESSOAS VALUES
(DEFAULT, 'Clécio', '2002-01-03', 'M', '60.4', '1.70', 'Brasil');
também pode adicionar varios valores seguidos adicionando uma , ao final de cada parênteses

SELECT * FROM "nome da tabela" = para ver os dados inseridos na tabela
    EX: SELECT * FROM pessoas;

ALTER TABLE "nome da tabela" = alterar algo da tabela
    EX: ALTER TABLE pessoas;

ADD COLUMN "nome da nova coluna" = adicionar uma nova coluna a tabela
    EX: ADD COLUMN profissao;

DROP COLUMN "nome da nova coluna" = remover uma coluna da tabela
    EX: DROP COLUMN profissao;

ADD COLUMN "nome da nova coluna" AFTER "nome de alguma coluna" = para colocar a nova coluna após alguma coluna na tabela
    EX: ADD COLUMN profissao VARCHAR(10) AFTER nome;

ADD COLUMN "nome da nova coluna" FIRST = adicionar a coluna na primeira posição da tabela
    EX: ADD COLUMN codigo FIRST;

MODIFY COLUMN "nome da coluna" = modifica os tipos e constrains da coluna
    EX: MODIFY COLUMN profissao VARCHAR(20)

CHANGE COLUMN "nome da coluna que deseja mudar o nome" "novo nome" = quando quiser alterar o nome de uma coluna
    EX: CHANGE COLUMN profissao prof VARCHAR(20);

RENAME TO "nome da tabela" = alterar o nome da tabela
    EX: RENAME TO populacao;

ADD PRIMARY KEY("nome da coluna para ser a chave"); = adicionar uma KEY na coluna
    EX: ADD PRIMARY KEY(idcurso);

DROP TABLE "nome da tabela" = apagar toda a tabela
    EX: DROP TABLE cursos;

UPDATE "nome da tabela"
SET "nome do campo" = "novo nome do item do campo"
WHERE "nome da chave primaria do campo" = 'valor da chave';
    EX: UPDATE cursos
        SET nome = 'HTML5'
        WHERE idcurso = '1';

Caso você queira mudar apenass uma linha da tabela porém não tem a chave primária use o comando:
    "LIMIT 1;"

DELETE FROM "nome da tabela"
WHERE "nome da chave" = "valor da chave"; = remover um item da tabela
    EX: DELETE FROM cursos
        WHERE idcurso = '8';

TRUNCATE TABLE "nome da tabela"; = deletar toda a tabela
    EX: TRUNCATE TABLE cursos;