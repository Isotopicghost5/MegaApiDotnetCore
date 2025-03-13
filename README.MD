
# Megaman API

Este projeto é um backend desenvolvido em .NET Core, criado para listar os dados dos bosses de *Mega Man* no formato JSON. O objetivo principal é fornecer uma API RESTful que retorne os dados dos robôs através de endpoints específicos.

## Endpoints da API

A API possui os seguintes endpoints:

### 1. **GET /api/v1/robots**
Retorna uma lista de todos os robôs (bosses de MegaMan).

**Exemplo de resposta:**
```json
[
  {
    "Id": 1,
    "Code": "DLN/DRN-003",
    "Name": "Cutman",
    "HP": 150,
    "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
  },
  {
    "Id": 2,
    "Code": "DLN/DRN-004",
    "Name": "Gutsman",
    "HP": 200,
    "Picture": "https://vignette.wikia.nocookie.net/megaman/images/a/a6/GutsMan.png"
  }
]
```

### 2. **GET /api/v1/robots/{id}**
Retorna os dados de um robô específico com base no ID.

**Exemplo de resposta:**
```json
{
  "Id": 1,
  "Code": "DLN/DRN-003",
  "Name": "Cutman",
  "HP": 150,
  "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
}
```

Se o robô não for encontrado, retorna:
```json
{
  "message": "Nenhum robô encontrado"
}
```

### 3. **POST /api/v1/robots**
Este endpoint é utilizado para enviar dados de um robô, mas ainda não possui implementação completa. Atualmente, responde com um status 200 OK.

---

## Dependências

O projeto faz uso das seguintes dependências:

| Dependência                        | Descrição                                      |
|-------------------------------------|------------------------------------------------|
| [Microsoft.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore) | Framework para ORM (Object-Relational Mapper) para interagir com o banco de dados. |
| [Microsoft.EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer) | Provedor do Entity Framework Core para bancos de dados SQL Server. |
| [Microsoft.EntityFrameworkCore.Design](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Design) | Ferramentas de design para Entity Framework Core, utilizadas para scaffolding de banco de dados. |
| [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json) | Biblioteca popular para manipulação de JSON no .NET. |

---

## Estrutura do Projeto

A estrutura de pastas do projeto é a seguinte:

```
.vs
.vscode
bin
Controllers
  └── RobotsController.cs
Database
  └── RobotContext.cs
middlewares
  └── CustomMiddleware.cs
Models
  └── Robot.cs
obj
Properties
Services
  └── IRobotServices.cs
  └── RobotServices.cs
appsettings.Development.json
appsettings.json
global.json
MegamanApi.csproj
MegamanApi.sln
Program.cs
Startup.cs
```

- **.vs, .vscode**: Arquivos de configuração de ambiente para Visual Studio e Visual Studio Code, respectivamente.
- **bin**: Diretório onde os arquivos binários compilados são gerados.
- **Controllers**: Contém os controladores da API. Exemplo: `RobotsController.cs` define os endpoints da API.
- **Database**: Contém classes relacionadas ao banco de dados. Exemplo: `RobotContext.cs` define o contexto de acesso aos dados.
- **middlewares**: Contém middlewares personalizados. Exemplo: `CustomMiddleware.cs` pode ser utilizado para interceptar requisições.
- **Models**: Contém os modelos de dados. Exemplo: `Robot.cs` define a estrutura de um robô.
- **obj**: Diretório onde arquivos temporários de compilação são armazenados.
- **Properties**: Contém arquivos de configuração do projeto, como `launchSettings.json`.
- **Services**: Contém serviços que implementam a lógica de negócios. Exemplo: `RobotServices.cs` implementa as operações de busca dos robôs.
- **appsettings.Development.json**: Arquivo de configuração para o ambiente de desenvolvimento.
- **appsettings.json**: Arquivo de configuração principal.
- **global.json**: Configuração global para o SDK do .NET.
- **MegamanApi.csproj**: Arquivo de projeto do .NET.
- **MegamanApi.sln**: Arquivo de solução do Visual Studio.
- **Program.cs**: Ponto de entrada do aplicativo.
- **Startup.cs**: Contém configurações de inicialização e middleware do aplicativo.

---

## Técnicas Utilizadas

- **API RESTful**: O projeto segue a arquitetura RESTful para fornecer acesso aos dados dos robôs.
- **Entity Framework Core**: Utilizado para interagir com o banco de dados.
- **Dependency Injection**: O serviço `IRobotServices` é injetado no controlador para promover uma melhor separação de responsabilidades.
- **DTO (Data Transfer Object)**: A API retorna objetos DTO para representar os dados dos robôs de forma mais simples e estruturada.
- **Middleware Personalizado**: Embora não implementado neste momento, há um diretório `middlewares` onde middlewares personalizados podem ser adicionados para tratamento de requisições.

---
