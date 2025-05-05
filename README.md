# Squadron - NestJS API + Go Worker

## 📦 Estrutura

- **API (NestJS)**: `/api`
- **Worker (Go)**: `/worker`
- **PostgreSQL** e **Redis** gerenciados via Docker

---

## 🚀 Subindo o Projeto com Docker

### Pré-requisitos

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### Instruções

```bash
docker-compose up --build
```
Isso irá:

- Buildar a imagem da API (NestJS)
- Buildar a imagem do Worker (Go)
- Subir containers para:
  - API (`localhost:3000`)
  - Worker (executando em segundo plano)
  - PostgreSQL (`localhost:5432`)
  - Redis (`localhost:6379`)

### Para parar os containers:

```bash
docker-compose down
```
## 🧑‍💻 Rodando Localmente (sem Docker)

Você pode rodar a API e o Worker em sua máquina, desde que tenha PostgreSQL e Redis rodando localmente.

### Pré-requisitos

- Node.js (v18+)
- Go (v1.20+)
- PostgreSQL e Redis rodando localmente
- Instalar as dependências com o gerenciador de pacotes da sua escolha (npm ou yarn)

### Banco de Dados Esperado

- **PostgreSQL**
  - Host: `localhost`
  - Porta: `5432`
  - Usuário: `user`
  - Senha: `password`
  - Database: `mydatabase`

- **Redis**
  - Host: `localhost`
  - Porta: `6379`

### 🔧 Rodar API (NestJS)

```bash
cd api
npm install
npm run start:dev
```
A API estará disponível em [http://localhost:3000](http://localhost:3000).

Certifique-se de que a variável `DATABASE_URL` está correta no `.env`:

```ini
DATABASE_URL=postgresql://user:password@localhost:5432/mydatabase
REDIS_URL=redis://localhost:6379
```
### ⚙️ Rodar Worker (Go)

```bash
cd worker
go run main.go
```
O Worker irá se conectar ao Redis para escutar/processar tarefas.

## 📂 Volumes e Dados Persistentes

Os dados do PostgreSQL são armazenados no volume Docker `postgres-data`.

Para inspecionar o volume:

```bash
docker volume inspect postgres-data
```