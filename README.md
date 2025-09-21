# 🐳 SQL Server com Docker

Este projeto configura um container com **SQL Server 2019** (versão gratuita) usando Docker Compose, com persistência de dados via volume Docker.

---

## ✅ Requisitos

- [Docker](https://www.docker.com/get-started)
- Docker Compose (já incluído no Docker Desktop)

---

## 🚀 Como subir o container

No terminal, execute:

```bash
docker-compose up -d
```

Isso fará o download da imagem oficial do SQL Server 2019 e iniciará o serviço na porta 1433.

## 📂 Persistência

Os dados do banco de dados são armazenados em um volume Docker nomeado chamado sqlserver-data.

* Isso garante que os dados permaneçam mesmo após parar ou remover o container.

* Para apagar os dados junto com o container, use:

```bash
docker-compose down -v
```

## 🔐 Acesso ao banco

* **Servidor:** localhost

* **Porta:** 1433

* **Usuário:** sa

* **Senha:** Sql!23456 ⚠️ (não utilize essa senha em produção)


## 🛠️ Como se conectar

Você pode usar qualquer ferramenta cliente SQL, como:

* [Azure Data Studio](https://learn.microsoft.com/pt-br/sql/azure-data-studio/download)

* [DBeaver](https://dbeaver.io/)

* [DataGrip](https://www.jetbrains.com/datagrip/)

* sqlcmd *(linha de comando)*

▶️ Conectar via terminal com sqlcmd:

```bash
docker exec -it sqlserver /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'Sql!23456'
```

## 🧱 Criando a primeira tabela

Dentro do sqlcmd, execute os comandos abaixo para criar um banco de dados e uma tabela:

```sql
-- Criar banco de dados
CREATE DATABASE MeuBanco;
GO

-- Usar o banco
USE MeuBanco;
GO

-- Criar tabela
CREATE TABLE Cadastro (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Nome NVARCHAR(100),
    Email NVARCHAR(100),
    DataCadastro DATETIME DEFAULT GETDATE()
);
GO
```

## 🧼 Parar e remover os containers

* Parar e remover apenas os containers:

```bash
docker-compose down
```

* Parar, remover containers e apagar os dados:

```bash
docker-compose down -v
```

## 📄 Licença

Distribuído gratuitamente para fins de desenvolvimento e testes com base na [licença da Microsoft](https://hub.docker.com/_/microsoft-mssql-server)

⚠️ Não recomendado para ambientes de produção.

