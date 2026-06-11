# Catálogo Pokémon - Modelagem de Banco de Dados Relacional

Este projeto consiste na modelagem e implementação de um banco de dados relacional (PostgreSQL) focado na catalogação de entidades do universo Pokémon, suas habilidades e tipagens. O ambiente foi estruturado utilizando Docker para garantir uma configuração padronizada e de fácil reprodução.

## 🚀 Tecnologias Utilizadas

- **PostgreSQL:** Sistema Gerenciador de Banco de Dados Relacional (SGBD).
- **Docker & Docker Compose:** Containerização do ambiente de banco de dados.
- **SQL (DDL e DML):** Criação das tabelas e inserção de dados iniciais.
- **VS Code:** IDE utilizada para desenvolvimento e manipulação dos scripts via extensões de banco de dados.

## 🗂️ Estrutura do Banco de Dados

O banco de dados, nomeado `sctec` (esquema `public`), possui tabelas relacionais projetadas para evitar redundâncias e garantir a integridade dos dados. Algumas das principais entidades incluem:

- `pokemon`: Tabela principal contendo identificador, número da Pokédex, nome, dimensões (altura e peso) e estatísticas base (HP, ataque, defesa).
- `habilidade`: Cadastro das habilidades disponíveis.
- `pokemon_habilidade`: Tabela associativa (N:N) que relaciona os Pokémon às suas respectivas habilidades.
- `pokemon_tipo`: Tabela para armazenar as tipagens dos Pokémon.

## ⚙️ Como Executar o Projeto

Para testar ou rodar este projeto na sua máquina, você precisará do [Docker](https://www.docker.com/) e do [Docker Compose](https://docs.docker.com/compose/) instalados.

### 1. Preparando o Ambiente

Clone este repositório para a sua máquina:

```bash
git clone https://github.com/dariph/projeto-banco-de-dados.git
cd projeto-banco-de-dados
```

Crie o arquivo de variáveis de ambiente. Você pode usar o arquivo de exemplo como base:

```bash
# No Windows (PowerShell):
cp .env.example .env

```

_Observação: Abra o arquivo `.env` gerado e preencha com o usuário e senha desejados para o banco de dados._

### 2. Subindo o Banco de Dados

Com o Docker em execução na sua máquina, levante o contêiner do PostgreSQL executando o seguinte comando na raiz do projeto:

```bash
docker-compose up -d

```

O banco de dados estará rodando e acessível na porta `5432`.

### 3. Importando a Estrutura (Schema)

Para criar as tabelas e inserir os dados iniciais, você deve executar o script SQL fornecido (`schema.sql`). Caso esteja utilizando o terminal, você pode injetar o script diretamente no contêiner com o comando:

```bash
docker exec -i sctec-db psql -U admin -d sctec < schema.sql

```

_(Se preferir, você também pode abrir a sua ferramenta de banco de dados favorita, como DBeaver, pgAdmin ou a extensão do VS Code, conectar-se usando as credenciais do `.env` e rodar o script manualmente)._
