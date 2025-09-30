# ADVANCED BUSINESS DEVELOPMENT WITH .NET - Mottu RFID API

Este projeto consiste em uma API RESTful desenvolvida em .NET para rastreamento de motos via RFID, com foco em boas práticas de desenvolvimento e Machine Learning para predição de localização e análise de padrões de movimento.

## 📋 Sobre o Projeto

Sistema de rastreamento de motos via RFID desenvolvido em .NET 9.0, implementando uma API RESTful completa com funcionalidades avançadas de monitoramento, machine learning e segurança.

## 👥 Integrantes da Equipe

- Lucas Miranda Leite RM:555161
- Gusthavo Daniel De Souza RM:554681
- Guilherme Damasio Roselli RM:555873

## 🏗️ Arquitetura do Sistema

O projeto segue a arquitetura Clean Architecture com as seguintes camadas:

- **MottuRFID.API**: Camada de apresentação (Controllers, Middleware)
- **MottuRFID.Application**: Camada de aplicação (DTOs, Services)
- **MottuRFID.Domain**: Camada de domínio (Entities, Interfaces)
- **MottuRFID.Infrastructure**: Camada de infraestrutura (Data, Repositories)
- **MottuRFID.Tests**: Camada de testes (Unitários e Integração)

## 🚀 Funcionalidades Implementadas

### ✅ 3º Sprint - Requisitos Básicos
- **API RESTful completa** com 3 entidades principais (Motos, Filiais, Pontos de Leitura)
- **Endpoints CRUD** com paginação, filtros e boas práticas REST
- **Documentação Swagger/OpenAPI** completa com exemplos e modelos
- **Repositório GitHub** com README detalhado

### ✅ 4º Sprint - Funcionalidades Avançadas
- **Health Checks** - Monitoramento da saúde da API (`/api/health`)
- **Versionamento da API** - Suporte a múltiplas versões (v1, v2)
- **Segurança com API Key** - Autenticação via header `X-API-Key`
- **Integração ML.NET** - Predição de localização e análise de padrões
- **Testes Unitários e de Integração** - Cobertura completa com xUnit

## 🔧 Tecnologias Utilizadas

- **.NET 9.0** - Framework principal
- **Entity Framework Core** - ORM para acesso a dados
- **Oracle Database** - Banco de dados principal (configuração comentada)
- **Swagger/OpenAPI** - Documentação da API
- **ML.NET** - Machine Learning
- **xUnit** - Framework de testes
- **Moq** - Mock para testes unitários

## 📊 Endpoints da API

### Motos
- `GET /api/motos` - Listar motos com filtros
- `GET /api/motos/{id}` - Buscar moto por ID
- `GET /api/motos/tag/{tagRFID}` - Buscar moto por tag RFID
- `POST /api/motos` - Criar nova moto
- `PUT /api/motos/{id}` - Atualizar moto
- `DELETE /api/motos/{id}` - Excluir moto

### Filiais
- `GET /api/filiais` - Listar filiais
- `GET /api/filiais/{id}` - Buscar filial por ID
- `GET /api/filiais/{id}/motos` - Listar motos da filial
- `POST /api/filiais` - Criar nova filial
- `PUT /api/filiais/{id}` - Atualizar filial
- `DELETE /api/filiais/{id}` - Excluir filial

### Pontos de Leitura
- `GET /api/pontosleitura` - Listar pontos de leitura
- `GET /api/pontosleitura/{id}` - Buscar ponto por ID
- `POST /api/pontosleitura` - Criar novo ponto
- `PUT /api/pontosleitura/{id}` - Atualizar ponto
- `DELETE /api/pontosleitura/{id}` - Excluir ponto

### RFID
- `POST /api/rfid/registrar` - Registrar leitura RFID
- `GET /api/rfid/historico/moto/{id}` - Histórico da moto
- `GET /api/rfid/localizacao/filial/{id}` - Localização das motos

### Machine Learning
- `GET /api/ml/PredictNextLocation/{motoId}` - Predizer próxima localização
- `GET /api/ml/AnalyzeMovementPatterns/{filialId}` - Analisar padrões de movimento

### Health Checks
- `GET /api/health` - Status completo da aplicação
- `GET /api/health/ping` - Verificação básica

## 🔐 Autenticação

A API utiliza autenticação via API Key. Para acessar os endpoints protegidos, inclua o header:

```
X-API-Key: mottu-rfid-api-key-2024
```

## 🗄️ Configuração do Banco de Dados

Configure a string de conexão no `appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=HOST:PORT/SID;User Id=USER;Password=PASS;"
  }
}
```

**Observação**: A configuração do banco de dados Oracle está comentada no `Program.cs`. Para utilizá-la, descomente as linhas e configure a string de conexão no `appsettings.json`.

## 🚀 Como Executar

### Pré-requisitos
- .NET 9.0 SDK
- Oracle Database (opcional, se descomentar a configuração)

### Passos para Execução

1.  **Navegue até o diretório `Mottu.NET`:**

    ```bash
    cd /home/ubuntu/project/ADVANCEDBUSINESSDEVELOPMENTWITH.NET/Mottu.NET
    ```

2.  **Restaure as dependências:**

    ```bash
    dotnet restore
    ```

3.  **Compile o projeto:**

    ```bash
    dotnet build
    ```

4.  **Publique o projeto (opcional, para criar um executável autônomo):**

    ```bash
    dotnet publish MottuRFID.API/MottuRFID.API.csproj -c Release -o ../publish
    ```

5.  **Execute a API:**

    ```bash
    dotnet run --project MottuRFID.API/MottuRFID.API.csproj
    ```
    Ou, se publicou:
    ```bash
    ./publish/MottuRFID.API
    ```

    A API será iniciada e estará disponível em `http://localhost:5193` (ou outra porta configurada, verifique o console).

## Acessando o Swagger/OpenAPI

Após iniciar a API, você pode acessar a documentação interativa do Swagger/OpenAPI através do seguinte URL:

[http://localhost:5193/swagger](http://localhost:5193/swagger)

O Swagger UI fornece:

-   **Descrição de endpoints e parâmetros**: Detalhes sobre cada rota da API, métodos HTTP, parâmetros de entrada e saída.
-   **Exemplos de payloads**: Modelos de dados para requisições e respostas.
-   **Modelos de dados descritos**: Definições dos objetos utilizados na API.

## 🧪 Executar Testes

Para rodar os testes unitários e de integração:

```bash
dotnet test MottuRFID.Tests/MottuRFID.Tests.csproj
```

