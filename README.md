# 🐳 SQL Server com Docker

Este projeto configura um container com **SQL Server 2022** (versão gratuita) usando Docker Compose, com persistência de dados.

---

## ✅ Requisitos

- Docker
- Docker Compose

---

## 🚀 Como subir o container

```bash
docker-compose up -d
```

Isso fará o pull da imagem oficial do SQL Server 2022 e iniciará o serviço na porta 1433.

## 📂 Persistência

Os dados do banco ficam salvos no diretório local *./data.* Ao reiniciar o container, os dados permanecerão.

## 🔐 Acesso ao banco

* **Servidor:** localhost

* **Porta:** 1433

* **Usuário:** sa

* **Senha:** MinhaSenha@2025


## 🛠️ Como se conectar

Você pode usar qualquer ferramenta cliente SQL, como:

* [Azure Data Studio](https://learn.microsoft.com/pt-br/sql/azure-data-studio/download)

* [DBeaver](https://dbeaver.io/)

* sqlcmd *(linha de comando)*

**Conectar via** sqlcmd:

```bash
docker exec -it sqlserver_container /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'MinhaSenha@2025'
```

## 🧱 Criando a primeira tabela

Dentro do sqlcmd, execute os comandos abaixo para criar um banco de dados e uma tabela:

```sql
-- Criar banco de dados
CREATE DATABASE MeuBanco;

-- Usar o banco
USE MeuBanco;

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

```bash
docker-compose down
```

Para remover os dados persistidos:

```bash
docker-compose down -v
```

## 📄 Licença

Distribuído gratuitamente para fins de desenvolvimento e testes com base na [licença da Microsoft](https://hub.docker.com/_/microsoft-mssql-server)


