# Desafio "Cadê meu Médico?" 

## Descrição do Projeto

Desenvolver uma API REST para um sistema de busca de médicos por especialidade e localização. O sistema deve permitir que usuários encontrem profissionais de saúde em suas cidades, com informações sobre especialidades, avaliações e disponibilidade.

## Requisitos Técnicos

### Obrigatórios
- ✅ API REST completa (GET, POST, PUT, PATCH, DELETE)
- ✅ Autenticação via JWT
- ✅ Documentação da API (Padrão Postman ou SWAGGER)
- ✅ Dockerização completa
- ✅ Versionamento no Git

### Stack Tecnológica
- **Linguagem**: Livre escolha
- **Banco de Dados**: Relacional (PostgreSQL, mariabd, sqllite)
- **Containerização**: Docker + Docker Compose
- **Autenticação**: JWT

## Endpoints Obrigatórios

### 🔐 Autenticação
```
POST   /api/v1/auth/register    - Cadastro de novo usuário (Return 201 CREATED)
POST   /api/v1/auth/login       - Login (retorna JWT) (200 sucess)

```

### 👤 Usuários (endpoint autenticados deve exijir JWT (caso contrario return 401 not authorized) )
```
GET    /api/v1/users/me         - Dados do usuário autenticado
PUT    /api/v1/users/me         - Atualizar perfil
```

### 👨‍⚕️ Médicos (Endpoints abertos)
```
GET    /api/v1/doctors          - Listar todos médicos (paginado)
GET    /api/v1/doctors/{id}     - Detalhes de um médico
```
### 👨‍⚕️ Médicos (Endpoints admin)
```
POST   /api/v1/doctors          - Cadastrar médico (admin/médico)
PUT    /api/v1/doctors/{id}     - Atualizar médico
DELETE /api/v1/doctors/{id}     - Remover médico (admin)
```

### 🔍 Busca
```
GET    /api/v1/search/doctors   - Busca avançada de médicos
  Query params:
    - specialty: Filtrar por especialidade
    - city: Filtrar por cidade
    - name: Buscar por nome
```

### 📋 Dados Auxiliares
```
GET    /api/v1/specialties      - Listar especialidades disponíveis
GET    /api/v1/cities           - Listar cidades cadastradas
GET    /api/v1/health          - Health check da aplicação
```

## Regras de Negócio

### Usuários
- Dois tipos: `user`, `admin`
- Senha mínima: 8 caracteres com complexidade

### Médicos
- CRM único e obrigatório
- Mínimo 1 especialidade
- Mínimo 1 cidade de atendimento
- Campos obrigatórios: nome, CRM, especialidade, cidade



## Restrições de Recursos (Docker)

```yaml
# Limites máximos por container
API:
  CPU: 0.5 cores
  Memória: 512MB

Database:
  CPU: 0.5 cores
  Memória: 512MB

Total do Sistema:
  CPU: 1.5 cores
  Memória: 1.5GB
```

## Métricas de Performance Esperadas


### Especialidades (seed inicial)
- Cardiologia
- Dermatologia
- Pediatria
- Clínica Geral


### Cidades (seed inicial)
- São Paulo/SP
- Apucarana/PR
- Rio de Janeiro/RJ


## Códigos HTTP

- `200` - Sucesso (GET, PUT, PATCH)
- `201` - Criado (POST)
- `204` - Sem conteúdo (DELETE)
- `400` - Requisição inválida
- `401` - Não autorizado
- `404` - Não encontrado
- `422` - Entidade não processável
- `500` - Erro interno


### Distribuição de Notas

- **Fase 1** (20%): Documentação da da Arquitetura (13/10 entrega por email)
        - Desenho da arquitura, definição da linguagem, banco de dados, link do repo
- **Fase 2** (30%): Demonstração Funcional (24/11)
- **Fase 3** (50%): Entrega Final + Performance (01/12 projeto completo no github)




## Links Úteis

- [Docker Documentation](https://docs.docker.com/)
- [JWT.io](https://jwt.io/)
- [REST API Best Practices](https://restfulapi.net/)
- [K6 Documentation](https://k6.io/docs/)
- [Postman Learning Center](https://learning.postman.com/)

---