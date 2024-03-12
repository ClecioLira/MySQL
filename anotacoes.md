# MySQL
- DDL = Definição = CREATE TABLE, CREATE DATABASE, ALTER TABLE, DROP TABLE
- DML = Manipulação = INSERT INTO, UPDATE, DELETE, TRUNCATE
- DQL = Solicitações = SELECT

Banco de dados tem Tabelas
Tabelas tem Registros
Registros tem Campos

Registros, Linhas e Tuplas são a mesma coisa.

Quando quiser exportar o banco de dados vá em, SERVER, DATA EXPORT, selecione o banco de dados, marque EXPORT TO SELF-CONTAINED FILE, marque a opção INCLUDE CREATE SCHEMA e clique em START EXPORT.

Quando quiser importar o banco de dados vá em, SERVER, DATA IMPORT, marque e selecione o arquivo em IMPORT FROM SELF-CONTAINED FILE e clique em START IMPORT.

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

TRUNCATE TABLE "nome da tabela"; = deletar todos dados da tabela
    EX: TRUNCATE TABLE cursos;

SELECT * FROM "nome da tabela" = para ver os dados inseridos na tabela
    EX: SELECT * FROM pessoas;

SELECT * FROM "nome da tabela" ORDER BY "nome do campo"; = para deixar os dados em ordem crescente
    EX: SELECT * FROM pessoas ORDER BY nome;

SELECT * FROM "nome da tabela" ORDER BY "nome do campo" DESC; = para deixar os dados em ordem decrescente
    EX: SELECT * FROM pessoas ORDER BY nome DESC;

SELECT "nome do campo" FROM "nome da tabela"; = caso queira ver apenas os dados do campo selecionado
    EX: SELECT nome, ano FROM cursos ORDER BY ano, nome;

SELECT "nome do campo" FROM "nome da tabela" WHERE "nome do campo + o valor"; = caso queira ver apenas as linhas do campo selecionado
    EX: SELECT nome, ano FROM cursos WHERE ano = '2016' ORDER BY ano, nome;

SELECT "nome do campo" FROM "nome da tabela"
WHERE "nome do campo" BETWEEN "valor do ano" AND "valor do ano"; = caso queira ver apenas os dados entre os valores selecionados
    EX: SELECT nome, ano FROM cursos
        WHERE ano BETWEEN 2014 AND 2016
        ORDER BY ano, nome;

SELECT "nome dos campos" FROM "nome da tabela"
WHERE "nome do campo" IN ("valore dos campos"); = o comando IN serve para colocar varios valores diferentes dentro dos parenteses e ver apenas os dados dos valores selecionados.
    EX: SELECT nome, ano FROM cursos
        WHERE ano IN (2014, 2016, 2020)
        ORDER BY ano, nome;

SELECT "nome dos campos" FROM "nome da tabela"
WHERE "nome do campo" LIKE "valor desejado do campo"; = serve para caso você queira ver os dados com o valor parecido apos o LIKE
    EX: SELECT nome FROM cursos
        WHERE nome LIKE 'P%';
O simbolo % tem grande importancia nesse caso, pois ele complementa o resto da palavra e o local onde ele for inserido trará diferentes resultados
    EX: '%P', 'P%', '%P%'
tambem tem o complemento _ que exige que tenha algo após ou antes o valor.
    EX: '%P_', '_P%', '_%P%_'

SELECT DISTINCT "nome do campo" FROM "nome da tabela"; = quando quiser saber os dados de algum campo só que sem se repetir valores iguais
    EX: SELECT DISTINCT nacionalidade FROM pessoas;

SELECT COUNT("valor do campo") FROM "nome da tabela"; = contar quantos cadastros tem essa tabela
    EX: SELECT COUNT(*) FROM cursos;

SELECT MAX("valor do campo") FROM "nome da tabela"; = saber o maior valor de um determinado campo da tabela
    EX: SELECT MAX(carga) FROM cursos;

SELECT MIN("valor do campo") FROM "nome da tabela"; = saber o menor valor de um determinado campo da tabela
    EX: SELECT MIN(carga) FROM cursos;

SELECT SUM("valor do campo") FROM "nome da tabela"; = saber a soma dos valores de um determinado campo da tabela
    EX: SELECT SUM(carga) FROM cursos;

SELECT AVG("valor do campo") FROM "nome da tabela"; = saber a media dos valores de um determinado campo da tabela
    EX: SELECT AVG(carga) FROM cursos;

# Operadores
< = MENOR QUE
> = MAIOR QUE
<= MENOR OU IGUAL QUE
=> MAIOR OU IGUAL QUE
= IGUAL
!=/ <> DIFERENTE
BETWEEN = ENTRE
AND = E
OR = OU
IN () = DENTRO DE
LIKE = PARECIDO
NOT LIKE = NÃO PARECIDO

# EXERCICIOS
1°  SELECT nome, sexo FROM gafanhotos 
    WHERE sexo = 'F';

2°  SELECT * FROM gafanhotos 
    WHERE nascimento BETWEEN '2000-01-01' AND '2015-12-31';
    
3°  SELECT * FROM gafanhotos 
    WHERE sexo = 'M' AND profissao = 'Programador';

4°  SELECT * FROM gafanhotos 
    WHERE sexo = 'F' AND nacionalidade = 'Brasil' AND nome LIKE 'J%';

5°  SELECT * FROM gafanhotos 
    WHERE sexo = 'M' AND nacionalidade != 'Brasil' AND peso < 100 AND nome LIKE '%silva%';

6°  SELECT MAX(altura) FROM gafanhotos 
    WHERE sexo = 'M' AND nacionalidade = 'Brasil';

7°  SELECT AVG(peso) FROM gafanhotos;

8°  SELECT MIN(peso) FROM gafanhotos 
    WHERE sexo = 'F' AND nacionalidade != 'Brasil' 
    AND nascimento BETWEEN '1990-01-01' AND '2000-12-31';

9°  SELECT COUNT(*) FROM gafanhotos 
    WHERE sexo = 'F' AND altura > '1.90';