--- TwiDIO API
API desenvolvida para o desafio TDD: Entendendo e Praticando em um Backend com Node e Typescript da DIO.
O objetivo é aplicar Test Driven Development (TDD) em um backend com Node.js e TypeScript, criando testes antes da implementação e garantindo qualidade em todas as camadas.

--- Tecnologias utilizadas
- Node.js
- TypeScript
- Express
- TypeORM
- SQLite
- Jest (unitários, integração e e2e)
- Swagger (documentação da API)

--- Arquitetura
- Controllers → Validam requisições e retornam respostas.
- Services → Regras de negócio.
- Repositories → Persistência no banco.
- Entities → Estrutura das tabelas.
- Database → Configuração e migrations.
- Mocks → Simulações para testes.
- Tests → Unitários, integração e e2e.

--- Como rodar
bash
yarn install
yarn run dev
Servidor disponível em:

Código
http://localhost:5000/v1
Swagger:

Código
http://localhost:5000/doc

--- Testes
-- Repository (PostRepository.test.ts)
Garante que o método getAll chama o find do TypeORM.

- Retorna a lista mockada de posts.

-- Service (GetAllPostService.test.ts)
Garante que o service chama o repositório.

- Retorna a lista mockada de posts.

-- Controller (GetAllPostController.test.ts)
Retorna 200 e lista vazia quando não há posts.

- Retorna 200 e lista de posts quando existem.

- Retorna 500 quando ocorre erro interno.

-- Endpoint (tests/posts.test.ts)
Faz requisição real via axios para /v1/posts.

Valida que o status é 200 e que os dados retornados batem com o esperado.

--- Edições realizadas
-- Durante a conclusão do desafio, foram feitos dois ajustes importantes para garantir consistência:

- index.ts

Antes:
ts
console.log(Server on port ${process.env.PORT} \nhttp://localhost:${process.env.PORT})
→ mostrava undefined quando PORT não estava definido.

Depois:
ts
const PORT = process.env.PORT || 5000;
console.log( Server running on http://localhost:${PORT}/v1);
→ agora sempre mostra a porta correta.

- tests/posts.test.ts
Antes: apontava para http://localhost:5001.
Depois: ajustado para http://localhost:5000/v1, consistente com o servidor.

--- Endpoints
GET /v1/posts → Retorna todos os posts.
POST /v1/posts → Cria um novo post (em desenvolvimento).

---Exemplo de resposta:
json
[
  {
    "id": 1,
    "author": "author@email.com",
    "content": "Tuite de exemplo"
  }
]

--- Nota
Ajustes finais para consistência (index.ts e posts.test.ts).
