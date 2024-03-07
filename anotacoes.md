# MySQL
- DDL = Definição
- DML = Manipulação
- DQL = Solicitações

Banco de dados tem Tabelas
Tabelas tem Registros
Registros tem Campos

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
create database "nome do banco de dados" = criar banco de dados

create table "nome da tabela" = criar tabela

describe "nome da tabela" = descrever a tabela

drop database "nome do banco de dados" = apaga o banco de dados

default character set utf8 
default collate utf8_general_ci; = conjunto de caracteres padrão que vão ser suportados