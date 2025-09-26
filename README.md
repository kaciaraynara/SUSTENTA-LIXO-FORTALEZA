# SUSTENTA-LIXO-FORTALEZA
Solução multiplataforma para mapeamento e gestão colaborativa de lixo urbano, conectando cidadãos e o poder público de Fortaleza.
Projeto Aplicado Multiplataforma - Sustenta CE
1. Objetivo do Projeto
O projeto Sustenta CE visa desenvolver uma solução digital para combater o descarte irregular de lixo em áreas urbanas, conectando cidadãos e o poder público em uma plataforma colaborativa. O objetivo é tornar a cidade mais limpa, eficiente e participativa, contribuindo diretamente para o Objetivo de Desenvolvimento Sustentável (ODS) 11: Cidades e Comunidades Sustentáveis.

2. Problema Abordado e Justificativa
Em muitas áreas de Fortaleza, o descarte inadequado de lixo é um problema recorrente, gerando impactos ambientais, sanitários e sociais. A falta de uma comunicação eficaz entre a população e os órgãos de gestão ambiental dificulta a resolução ágil dessas ocorrências. A solução proposta atua como um elo, empoderando os cidadãos a reportar problemas e permitindo que o poder público atue de forma mais organizada e com base em dados.

3. Visão Geral da Arquitetura
O sistema foi projetado com uma arquitetura Cliente-Servidor (Client-Server) e uma abordagem em três camadas, com comunicação via uma API RESTful.

Aplicativo Mobile (Frontend): Interface para o cidadão reportar e acompanhar ocorrências.

Painel Web (Frontend): Interface para os gestores da prefeitura visualizarem, gerenciarem e atribuírem os relatos às equipes de limpeza.

Backend (API): Lógica de negócio, autenticação e gerenciamento de dados.

Banco de Dados: Armazenamento persistente de todas as informações.

graph TD
    subgraph "Camada de Apresentação"
        A[Aplicativo Mobile Cidadão] --> B(API RESTful);
        C[Painel Web Gestor] --> B;
    end

    subgraph "Camada de Aplicação (Backend)"
        B --> D{Lógica de Negócio e Serviços};
        D --> E[Autenticação de Usuários];
        D --> F[Serviços de Mapeamento];
    end

    subgraph "Camada de Dados"
        D --> G[Banco de Dados PostgreSQL];
    end

4. Tecnologias Propostas
A escolha das tecnologias foi baseada na sua eficiência, escalabilidade e na natureza multiplataforma do projeto.

Mobile Frontend: React Native

Web Frontend: ReactJS

Backend: Node.js com framework Express.js

Banco de Dados: PostgreSQL (com extensão PostGIS para geolocalização)

Serviços: Google Maps API para funcionalidades de mapa

5. Cronograma de Desenvolvimento (Etapa 2 - N708)
O desenvolvimento da segunda etapa está planejado para ocorrer em 10 semanas, com a seguinte divisão de tarefas:

Semanas 1-2: Configuração do ambiente de desenvolvimento e integração básica de APIs.

Semanas 3-4: Desenvolvimento do Frontend Mobile e Backend de Autenticação.

Semanas 5-6: Desenvolvimento do Backend (Endpoints de Relatos) e CRUD completo.

Semanas 7-8: Desenvolvimento do Frontend Web (Dashboard e Relatórios) e integração com a API.

Semanas 9-10: Implementação de funcionalidades de detalhes e testes.

6. Integrantes da Equipe e Papéis
[Nome Completo do Membro 1]: Papel

[Nome Completo do Membro 2]: Papel

[Nome Completo do Membro 3]: Papel

[Nome Completo do Membro 4]: Papel


Requisitos e Análise do Sistema Sustenta CE
1. Perfis de Usuários
Cidadão (Usuário Mobile): Pessoa que deseja reportar um ponto de lixo.

Gestor Público (Usuário Web): Funcionário da prefeitura (ou órgão responsável) que gerencia os relatos.

Equipe de Coleta (Usuário Mobile ou de Campo): Equipe responsável pela coleta e limpeza, que recebe as atribuições de tarefas.

2. Requisitos Funcionais (RF)
Os requisitos funcionais descrevem o que o sistema deve fazer.

ID

Requisito

Descrição

RF-01

Cadastro de Usuário

O sistema deve permitir que novos usuários (cidadãos) se cadastrem informando nome, email e senha.

RF-02

Login de Usuário

O sistema deve permitir que usuários autenticados (cidadão e gestor) acessem a plataforma com email e senha.

RF-03

Relatar Ocorrência

O usuário mobile deve poder criar um novo relato, incluindo foto, localização via GPS e uma breve descrição.

RF-04

Visualizar Mapa de Relatos

O usuário deve poder visualizar um mapa com todos os pontos de lixo reportados, usando cores para diferenciar o status.

RF-05

Visualizar Detalhes do Relato

O usuário deve poder clicar em um ponto no mapa ou na lista e ver detalhes da ocorrência, como foto, status atual e histórico de atualizações.

RF-06

Gerenciar Relatos (Gestor)

O gestor deve ter acesso a um painel para visualizar, filtrar e buscar todos os relatos.

RF-07

Atualizar Status

O gestor deve poder alterar o status de um relato (Ex: Pendente, Em Andamento, Resolvido).

RF-08

Atribuir Equipe

O gestor deve poder atribuir um relato a uma equipe de coleta específica.

RF-09

Gestão de Equipes

O gestor deve poder adicionar, editar ou remover equipes de coleta.

RF-10

Histórico de Relatos

O usuário mobile deve poder ver todos os relatos que ele fez em uma lista pessoal.

3. Requisitos Não-Funcionais (RNF)
Os requisitos não-funcionais descrevem como o sistema deve funcionar (qualidade).

ID

Requisito

Descrição

RNF-01

Disponibilidade

O sistema deve estar disponível 99,9% do tempo, 24/7.

RNF-02

Usabilidade (Mobile)

A interface do aplicativo mobile deve ser intuitiva e otimizada para uso em campo (com uma mão), com botões grandes e fluxo simples.

RNF-03

Segurança

As senhas devem ser armazenadas de forma criptografada. A comunicação entre o frontend e o backend deve ser via HTTPS.

RNF-04

Escalabilidade

A arquitetura deve suportar o crescimento do número de usuários e relatos sem comprometer o desempenho.

RNF-05

Tempo de Resposta

O tempo de carregamento das telas e das requisições de API não deve exceder 3 segundos.

RNF-06

Compatibilidade

O aplicativo mobile deve ser compatível com as versões mais recentes dos sistemas operacionais iOS e Android.

RNF-07

Acessibilidade

A interface deve seguir as diretrizes básicas de acessibilidade (WCAG) para cores e contraste.

RNF-08

Manutenibilidade

O código deve ser bem documentado e modular para facilitar futuras atualizações e correções.

4. Regras de Negócio
Somente o gestor pode alterar o status de um relato.

A localização do relato é obrigatória.

A foto do relato é opcional, mas recomendada.

Um relato só pode ser atribuído a uma única equipe de coleta por vez.

O acesso ao painel de gestão é restrito a usuários com perfil "gestor".

5. Histórias de Usuário
Como um Cidadão, eu quero relatar um ponto de lixo rapidamente para que a prefeitura possa resolver o problema.

Como um Cidadão, eu quero ver no mapa os relatos na minha região para saber quais áreas já estão em andamento.

Como um Gestor, eu quero visualizar todos os relatos em um mapa e uma lista para ter uma visão geral dos problemas da cidade.

Como um Gestor, eu quero atribuir um relato a uma equipe para delegar a tarefa de limpeza.

Como uma Equipe de Coleta, eu quero receber a notificação de uma nova tarefa para ir ao local e resolver o problema.
Arquitetura de Software do Sistema Sustenta CE
1. Descrição da Arquitetura
A arquitetura do Sustenta CE é baseada no padrão Cliente-Servidor (Client-Server), com uma abordagem modular. O sistema é dividido em três camadas lógicas que se comunicam via uma API RESTful.

Camada de Apresentação (Frontend): Responsável pela interação com o usuário. Terá duas interfaces: uma para o cidadão (mobile) e outra para o gestor (web).

Camada de Aplicação (Backend): Contém a lógica de negócio, processamento de dados e autenticação. Atua como o intermediário entre o frontend e o banco de dados.

Camada de Dados (Banco de Dados): Armazenamento e gerenciamento persistente das informações.

2. Diagrama de Arquitetura
O diagrama abaixo ilustra a comunicação entre as diferentes camadas da arquitetura do sistema.

graph TD
    subgraph "Camada de Apresentação"
        A[Aplicativo Mobile Cidadão] --> B(API RESTful);
        C[Painel Web Gestor] --> B;
    end

    subgraph "Camada de Aplicação (Backend)"
        B --> D{Lógica de Negócio e Serviços};
        D --> E[Autenticação de Usuários];
        D --> F[Serviços de Mapeamento];
        D --> G[Serviços de Notificação];
    end

    subgraph "Camada de Dados"
        D --> H[Banco de Dados PostgreSQL];
    end

3. Padrões Arquiteturais Utilizados
Padrão Cliente-Servidor: A arquitetura se baseia na separação entre cliente (frontend) e servidor (backend), permitindo o desenvolvimento independente das partes.

Padrão MVC (Model-View-Controller): Será aplicado no backend para separar a lógica de negócio (Model), a interface de dados (Controller) e a apresentação (simulada pelo frontend).

Arquitetura RESTful: A API de comunicação entre o frontend e o backend seguirá os princípios REST, utilizando endpoints claros e métodos HTTP padrão.

4. Decisões Técnicas e Justificativas
Componente

Tecnologia

Justificativa

Mobile

React Native

Multiplataforma: Um único código para iOS e Android. Performance: Rápido e com uma boa experiência de usuário. Comunidade: Grande comunidade e ecossistema de bibliotecas.

Web

ReactJS

Ecossistema unificado: Mesma lógica do React Native, facilitando a troca de desenvolvedores entre as equipes. Componentização: Facilita a reutilização de código e a manutenção.

Backend

Node.js (Express.js)

JavaScript: Permite que a mesma linguagem seja usada no frontend e backend. Assíncrono: Ideal para lidar com muitas requisições simultâneas (I/O non-blocking).

Banco de Dados

PostgreSQL

Relacional: Oferece consistência e integridade dos dados, essencial para a gestão de informações sobre o lixo e equipes. Geo-enabled: Possui a extensão PostGIS, ideal para trabalhar com dados de geolocalização.

Serviços de Mapeamento

Google Maps API

Precisão: Alta precisão de geolocalização. Features: Ricos recursos de personalização e marcação de pontos no mapa.

Autenticação

JWT (JSON Web Tokens)

Leveza: Não necessita de estado no servidor, o que torna a API mais escalável. Segurança: Utiliza criptografia para garantir a integridade dos tokens.


Modelo de Dados do Sistema Sustenta CE
1. Modelo de Entidade-Relacionamento (MER)
O modelo de dados foi projetado para ser relacional e suportar a gestão de usuários, relatos, equipes e a relação entre eles.

erDiagram
    USUARIO {
        INT id_usuario PK
        VARCHAR nome
        VARCHAR email UK
        VARCHAR senha_hash
        ENUM tipo_usuario
        TIMESTAMP data_cadastro
    }

    RELATO {
        INT id_relato PK
        INT id_usuario FK "Relata"
        FLOAT latitude
        FLOAT longitude
        VARCHAR url_foto
        TEXT descricao
        ENUM status "Pendente, Em Andamento, Resolvido"
        TIMESTAMP data_criacao
        TIMESTAMP ultima_atualizacao
    }

    EQUIPE {
        INT id_equipe PK
        VARCHAR nome_equipe
        TEXT descricao_equipe
    }

    ATRIBUICAO {
        INT id_atribuicao PK
        INT id_relato FK "Atribuído a"
        INT id_equipe FK "Atribui"
        TIMESTAMP data_atribuicao
    }

    HISTORICO_STATUS {
        INT id_historico PK
        INT id_relato FK "Histórico de"
        ENUM status_anterior
        ENUM status_novo
        TIMESTAMP data_mudanca
    }

    USUARIO ||--o{ RELATO : "Relata"
    RELATO }o--|| ATRIBUICAO : "Atribuído a"
    EQUIPE ||--o{ ATRIBUICAO : "Atribui"
    RELATO }o--|| HISTORICO_STATUS : "Histórico de"

2. Dicionário de Dados
Entidade

Campo

Tipo de Dado

Descrição

USUARIO

id_usuario

INT

Identificador único do usuário.



nome

VARCHAR

Nome completo do usuário.



email

VARCHAR

Endereço de email, usado para login (único).



senha_hash

VARCHAR

Senha criptografada.



tipo_usuario

ENUM

Perfil do usuário: 'cidadão' ou 'gestor'.



data_cadastro

TIMESTAMP

Data e hora do cadastro do usuário.

RELATO

id_relato

INT

Identificador único do relato de lixo.



id_usuario

INT

Chave estrangeira para o usuário que fez o relato.



latitude

FLOAT

Coordenada de latitude da localização do lixo.



longitude

FLOAT

Coordenada de longitude da localização do lixo.



url_foto

VARCHAR

URL da foto do local do lixo.



descricao

TEXT

Descrição do tipo de lixo ou problema.



status

ENUM

Situação atual do relato: 'Pendente', 'Em Andamento', 'Resolvido'.



data_criacao

TIMESTAMP

Data e hora em que o relato foi criado.



ultima_atualizacao

TIMESTAMP

Última data e hora em que o status foi atualizado.

EQUIPE

id_equipe

INT

Identificador único da equipe de coleta.



nome_equipe

VARCHAR

Nome da equipe (Ex: Equipe Norte, Equipe Sul).



descricao_equipe

TEXT

Descrição das áreas ou responsabilidades da equipe.

ATRIBUICAO

id_atribuicao

INT

Identificador único da atribuição.



id_relato

INT

Chave estrangeira para o relato atribuído.



id_equipe

INT

Chave estrangeira para a equipe responsável.



data_atribuicao

TIMESTAMP

Data e hora em que a atribuição foi feita.

HISTORICO_STATUS

id_historico

INT

Identificador único do histórico de status.



id_relato

INT

Chave estrangeira para o relato associado.



status_anterior

ENUM

Status anterior ao da mudança.



status_novo

ENUM

Novo status atribuído.



data_mudanca

TIMESTAMP

Data e hora da mudança de status.

Especificação da API RESTful do Sustenta CE
A API do Sustenta CE segue o padrão RESTful e utiliza endpoints descritivos para gerenciar os dados.

1. Endpoints Previstos
Método

Endpoint

Descrição

POST

/api/auth/register

Cria um novo usuário (cidadão).

POST

/api/auth/login

Autentica um usuário e retorna um JWT.

POST

/api/relatos

Cria um novo relato de lixo. Requer autenticação.

GET

/api/relatos

Retorna uma lista de todos os relatos. Pode ser filtrado por status ou localização.

GET

/api/relatos/{id}

Retorna os detalhes de um relato específico.

PUT

/api/relatos/{id}

Atualiza um relato (apenas para gestores). Requer autenticação de gestor.

POST

/api/equipes

Cria uma nova equipe de coleta (apenas para gestores). Requer autenticação de gestor.

GET

/api/equipes

Retorna uma lista de todas as equipes de coleta.

GET

/api/relatos/meus

Retorna a lista de relatos feitos pelo usuário autenticado.

2. Parâmetros de Requisição e Resposta
POST /api/auth/register

Requisição (Body): {"nome": "João", "email": "joao@email.com", "senha": "uma_senha_forte"}

Resposta (Body): {"mensagem": "Usuário criado com sucesso!"}

POST /api/auth/login

Requisição (Body): {"email": "joao@email.com", "senha": "uma_senha_forte"}

Resposta (Body): {"token": "eyJhbGciOiJIUzI1NiIsInR5c..."}, "usuario": {"id": 1, "nome": "João"}}

POST /api/relatos

Requisição (Body): {"latitude": -3.7319, "longitude": -38.5267, "descricao": "Lixo em frente a escola", "foto": "url_da_foto.jpg"}

Resposta (Body): {"mensagem": "Relato enviado com sucesso!", "relato_id": 123}

PUT /api/relatos/{id}

Requisição (Body): {"status": "Em Andamento", "equipe_id": 1}

Resposta (Body): {"mensagem": "Relato atualizado com sucesso."}

3. Autenticação e Autorização
A autenticação será feita via JWT (JSON Web Tokens).

Após o login, o servidor emitirá um token.

Esse token deverá ser incluído no cabeçalho Authorization de todas as requisições que exigem autenticação, no formato Bearer <token>.

4. Exemplos de Chamadas (cURL)
Login de usuário:

curl -X POST -H "Content-Type: application/json" -d '{"email":"gestor@prefeitura.ce.gov.br", "senha":"uma_senha_forte"}' [http://api.sustentace.com.br/api/auth/login](http://api.sustentace.com.br/api/auth/login)

Criar um novo relato (com autenticação):

curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer <seu_token_jwt>" -d '{"latitude":-3.72, "longitude":-38.53, "descricao":"Lixo na calçada", "foto":"url_da_foto.jpg"}' [http://api.sustentace.com.br/api/relatos](http://api.sustentace.com.br/api/relatos)

