Imersão Alura - Guilherme Lima

📘 API de Gestão Escolar
Esta API, desenvolvida com FastAPI, permite gerenciar informações de alunos, cursos e matrículas em uma instituição de ensino.

📦 Estrutura
A aplicação está dividida em:

routers/ — Endpoints organizados por entidade (alunos, cursos, matriculas)

models.py — Modelos SQLAlchemy das tabelas

schemas.py — Schemas Pydantic para validação

database.py — Configuração do SQLite

🚀 Como rodar com Docker Compose
📁 Estrutura esperada:
pgsql
Copiar
Editar
.
├── app/
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   ├── schemas.py
│   ├── routers/
│   │   ├── alunos.py
│   │   ├── cursos.py
│   │   └── matriculas.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
🐳 Dockerfile (exemplo)
Dockerfile
Copiar
Editar
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
🧩 docker-compose.yml
yaml
Copiar
Editar
version: '3.9'

services:
  api:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
📦 requirements.txt (exemplo)
nginx
Copiar
Editar
fastapi
uvicorn
sqlalchemy
pydantic
▶️ Subindo a aplicação
No terminal, execute:

bash
Copiar
Editar
docker-compose up --build
A API estará disponível em:
📍 http://localhost:8000
📚 Documentação interativa: http://localhost:8000/docs

🧪 Endpoints disponíveis
/alunos – Gerencia alunos

/cursos – Gerencia cursos

/matriculas – Gerencia matrícula de alunos em cursos

🗃️ Banco de Dados
Utiliza SQLite local (escola.db)

Criado automaticamente na primeira execução.

