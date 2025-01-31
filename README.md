# Documentação SGR

## Índice

1. [Introdução](#introducao)
   - [Propósito](#proposito)
   - [Visão Geral das Funcionalidades](#visao-geral-das-funcionalidades)
   - [Tecnologias Utilizadas](#tecnologias-utilizadas)
   - [Estrutura do Projeto](#estrutura-do-projeto)

2. [Começando](#comecando)
   - [Pré-requisitos](#pre-requisitos)
   - [Instalação](#instalacao)
   - [Configuração](#configuracao)
   - [Executando a Aplicação](#executando-a-aplicacao)

3. [Frontend (Angular)](#frontend-angular)
   - [Visão Geral da Aplicação](#visao-geral-da-aplicacao-1)
   - [Funcionalidades Principais](#funcionalidades-principais)
   - [Roteamento](#roteamento)
   - [Hierarquia de Componentes](#hierarquia-de-componentes)
   - [Estilização](#estilizacao)

4. [Backend (Django)](#backend-django)
   - [Visão Geral da Aplicação](#visao-geral-da-aplicacao)
   - [Funcionalidade Principal](#funcionalidade-principal)
   - [Integração com API Udemy](#integracao-com-api-udemy)
   - [Geração de PDF](#geracao-de-pdf)
   - [Relatórios](#relatorios)
   - [Modelos de Dados](#modelos-de-dados)
   - [Endpoints de API](#endpoints-de-api)

5. [Implantação](#implantacao)
   - [Configuração do Docker](#configuracao-do-docker)
   - [Variáveis de Ambiente](#variaveis-de-ambiente)
   - [Considerações para Produção](#consideracoes-para-producao)
   - [Pipeline CI/CD](#pipeline-cicd)

6. [Testes](#testes)
   - [Testes Unitários](#testes-unitarios)
   - [Testes de Integração](#testes-de-integracao)

7. [Contribuindo](#contribuindo)
   - [Código de Conduta](#codigo-de-conduta)
   - [Diretrizes de Contribuição](#diretrizes-de-contribuicao)

8. [Licença](#licenca)

---

## Introdução

### Propósito
O propósito desta aplicação web fullstack é fornecer uma plataforma para gerenciamento de certificados de conclusão de curso para clientes que concluíram cursos na Udemy. A aplicação serve tanto uma parte voltada para o cliente, para gerar e baixar seus certificados, quanto uma parte interna para análises de negócios e tomadas de decisão.

### Visão Geral das Funcionalidades
- **Geração de Certificados:** Gerar automaticamente certificados em PDF para cursos concluídos usando dados da API Udemy.
- **Sincronização de Dados de Curso:** Sincronizar regularmente dados de curso e métricas de conclusão da Udemy.
- **Análise de Negócios:** Utilizar dados de curso e usuário para gerar relatórios e visualizações que auxiliem em decisões estratégicas de negócios.
- **Gerenciamento de Usuários:** Autenticação segura e gerenciamento de usuários para clientes e funcionários internos.
- **Design Responsivo:** Interface frontend moderna e responsiva construída usando Angular e o tema Fuse.

### Tecnologias Utilizadas
- **Backend:** Django
- **Frontend:** Angular com tema Fuse
- **Banco de Dados:** PostgreSQL
- **Integração de API:** API Udemy
- **Implantação:** Docker

### Estrutura do Projeto
O projeto é organizado em duas partes principais:
- **Backend (Django):** Trata da lógica central da aplicação, endpoints da API, processamento de dados e integrações.
- **Frontend (Angular):** Fornece a interface do usuário, construída usando o tema Fuse para uma aparência moderna.

A aplicação é estruturada para permitir fácil manutenção e escalabilidade, garantindo que futuros desenvolvedores possam navegar e entender rapidamente seus componentes.

---

## Começando

Esta seção irá guiá-lo através do processo de configuração da aplicação localmente para fins de desenvolvimento e teste.

### Pré-requisitos

Antes de começar, certifique-se de ter o seguinte software instalado em sua máquina:

- **Python 3.8+**: Necessário para executar o backend Django.
- **Node.js 14+**: Necessário para o desenvolvimento Angular.
- **npm 6+**: Usado para gerenciar pacotes JavaScript.
- **Docker**: Para conteinerização e implantação.
- **Git**: Sistema de controle de versão para clonar o repositório.

### Instalação

Siga estes passos para configurar a aplicação:

1. **Clone o Repositório:**

   ```bash
   git clone https://github.com/your-repo/project.git
   cd project
   ```

2. **Configuração do Backend (Django):**

   - Crie e ative um ambiente virtual:

     ```bash
     python -m venv venv
     source venv/bin/activate  # No Windows use `venv\Scripts\activate`
     ```

   - Instale as dependências do Python:

     ```bash
     pip install -r requirements.txt
     ```

   - Aplique as migrações do banco de dados:

     ```bash
     python manage.py migrate
     ```

   - Crie uma conta de superusuário para a interface de administração do Django:

     ```bash
     python manage.py createsuperuser
     ```

3. **Configuração do Frontend (Angular):**

   - Navegue até o diretório Angular:

     ```bash
     cd angular
     ```

   - Instale as dependências do Node.js:

     ```bash
     npm install
     ```

4. **Configuração de Ambiente:**

   - Copie a configuração de ambiente de exemplo e personalize-a:

     ```bash
     cp project/settings.example.py project/settings.py
     ```

   - Certifique-se de substituir os espaços reservados por valores reais (por exemplo, chaves de API, URL do banco de dados).

### Configuração

- **Variáveis de Ambiente:**
  Defina as variáveis de ambiente necessárias conforme especificado em `project/settings.py` ou no arquivo `.env`.

  - `DJANGO_SECRET_KEY`: Sua chave secreta do Django para a aplicação.
  - `UDEMY_API_KEY`: Chave de API para acessar dados da Udemy.
  - `DATABASE_URL`: URL do banco de dados de produção, se diferente do SQLite.

### Executando a Aplicação

1. **Inicie o Servidor Backend:**

   Certifique-se de que seu ambiente virtual esteja ativado, então execute:

   ```bash
   python manage.py runserver
   ```

   O servidor de desenvolvimento Django começará em `http://127.0.0.1:8000/`.

2. **Inicie o Servidor Frontend:**

   Abra uma nova janela de terminal, navegue até o diretório Angular e execute:

   ```bash
   ng serve
   ```

## Frontend (Angular)

### Visão Geral da Aplicação

O frontend desta aplicação é construído usando o **Fuse Angular Theme**, um template Angular abrangente e altamente personalizável. A documentação do Fuse pode ser encontrada em [Documentação Fuse](https://angular-material.fusetheme.com/docs/guides). Esta documentação serve como um excelente recurso para entender e utilizar os vários componentes e layouts fornecidos pelo tema.

O Fuse é projetado em torno do Angular, Angular Material e TailwindCSS. Ele fornece:

- **Angular** como o framework principal.
- **Angular Material** para componentes de UI como botões, formulários e abas.
- **TailwindCSS** para estilização baseada em utilitários e configurações de layout.

Para mais detalhes sobre seus recursos, layouts e melhores práticas, consulte os [Guias do Fuse](https://angular-material.fusetheme.com/docs/guides).

### Estrutura de Diretórios

A estrutura de diretórios do Fuse pode parecer extensa e complexa inicialmente devido ao seu design multi-propósito e multi-layout.
Para uma explicação detalhada da estrutura de diretórios, consulte a documentação oficial do Fuse: [Estrutura de Diretórios do Fuse](https://angular-material.fusetheme.com/docs/guides/development/directory-structure).

Abaixo está uma versão simplificada da estrutura de diretórios, enfatizando as partes relevantes para o nosso projeto:

```plaintext
public
src/
@fuse/
app/
  core/
  layout/
  mock-api/
  modules/
    admin/
    auth/
    landing/
  app.component.html
  app.component.scss
  app.component.ts
  app.config.ts
  app.resolvers.ts
  app.routes.ts
styles/
index.html
main.ts
```

#### Notas:
1. **Fuse como um Tema Completo:**  
   O Fuse inclui uma ampla gama de recursos e módulos, muitos dos quais podem não ser usados ativamente nesta aplicação. Embora isso possa parecer inicialmente avassalador, garante flexibilidade para expansões ou integrações futuras.
   
2. **Foco na Personalização:**  
   Esta documentação cobrirá principalmente os aspectos que foram personalizados ou especificamente construídos para esta aplicação. Para todos os outros elementos, consulte a documentação do Fuse.

3. **Curva de Aprendizado:**  
   O Fuse é mais do que um simples template—é um guia estruturado para a construção de aplicações. Passar tempo entendendo a estrutura de diretórios e explorando recursos não utilizados será valioso para tirar o máximo proveito deste tema.

---

### Módulos Principais

O diretório `core` contém serviços essenciais, utilidades e configurações que são compartilhados em toda a aplicação. Abaixo estão os principais módulos e seus propósitos:

#### 1. **Módulo de Autenticação**
O módulo `auth` lida com autenticação e autorização dentro da aplicação. Inclui serviços, interceptores e guardas para gerenciar sessões de usuários, proteger rotas e interagir com o backend para autenticação.

- **Arquivos:**
  - `auth.interceptor.ts`: Intercepta requisições HTTP para adicionar tokens de autenticação.
  - `auth.provider.ts`: Fornece configurações e dependências relacionadas à autenticação.
  - `auth.service.ts`: Gerencia a autenticação do usuário, incluindo login, logout e armazenamento de tokens.
  - `auth.utils.ts`: Funções utilitárias para autenticação, como validação de token.
  - `guards/`: Contém guardas de rota para restringir acesso com base em papéis de usuário e status de autenticação.
    - `auth.guard.ts`: Restringe acesso a usuários autenticados.
    - `noAuth.guard.ts`: Restringe acesso a usuários não autenticados.
    - `staff.guard.ts`: Restringe acesso a usuários com permissões de nível de staff.

#### 2. **Módulo de Cursos**
O módulo `course` gerencia dados e interações relacionados a cursos. Inclui serviços e tipos para buscar, atualizar e exibir informações de cursos.

- **Arquivos:**
  - `course.service.ts`: Lida com chamadas de API para dados de cursos, como busca de detalhes de curso ou inscrição de usuários.
  - `course.types.ts`: Define interfaces e tipos TypeScript para estruturas de dados relacionadas a cursos.

#### 3. **Módulo API Udemy**
O módulo `udemyApi` integra-se com a API Udemy para buscar dados de cursos e outras informações relevantes. Abstrai as interações de API em um serviço reutilizável.

- **Arquivos:**
  - `udemyApi.service.ts`: Gerencia requisições de API para a Udemy, incluindo busca de listas de cursos, detalhes e resultados de pesquisa.
  - `udemyApi.types.ts`: Define interfaces e tipos TypeScript para dados retornados pela API Udemy.

#### 4. **Módulo de Usuário**
O módulo `user` lida com dados e interações relacionadas a usuários. Inclui serviços e tipos para gerenciar perfis de usuários, papéis e permissões.

- **Arquivos:**
  - `user.service.ts`: Gerencia chamadas de API para dados de usuários, como busca de perfis de usuários ou atualização de informações de usuários.
  - `user.types.ts`: Define interfaces e tipos TypeScript para estruturas de dados relacionadas a usuários.

---

## Módulos da Aplicação

O diretório `modules` contém os principais módulos de funcionalidade da aplicação, que representam diferentes seções do frontend. Esses módulos lidam com várias funcionalidades, incluindo administração, autenticação, páginas de aterrissagem e configurações do usuário.

Abaixo está uma visão geral de cada módulo e seus principais componentes.

---

### Módulo Admin
O módulo `admin` é responsável por gerenciar tarefas administrativas dentro da aplicação. Inclui submódulos para configurar contas, gerenciar usuários e outras funções administrativas.

#### **Configuração de Conta**
- **Propósito:** Gerencia as configurações da conta.
- **Arquivos:**
  - `account-config.component.html`: Define a estrutura HTML.
  - `account-config.component.ts`: Implementa a lógica para configuração de conta.
  - `account-config.routes.ts`: Gerencia a navegação e roteamento para este componente.

#### **Exemplo**
- **Propósito:** Um componente de exemplo para funcionalidades administrativas.
- **Arquivos:**
  - `example.component.html`
  - `example.component.ts`
  - `example.routes.ts`

#### **Gestão**
- **Propósito:** Gerencia configurações administrativas e permissões de usuários.
- **Arquivos:**
  - `management.component.html`
  - `management.component.ts`
  - `management.routes.ts`

---

### Módulo Auth
O módulo `auth` é responsável pela autenticação, incluindo login, registro e gerenciamento de senhas.

#### **Confirmação Necessária**
- **Propósito:** Exibe uma mensagem de confirmação quando a verificação do usuário é necessária.
- **Arquivos:**
  - `confirmation-required.component.html`
  - `confirmation-required.component.ts`
  - `confirmation-required.routes.ts`

#### **Confirmação de E-mail**
- **Propósito:** Gerencia a verificação de e-mail após o registro.
- **Arquivos:**
  - `email-confirmation.component.html`
  - `email-confirmation.component.ts`
  - `email-confirmation.routes.ts`

#### **Esqueci a Senha**
- **Propósito:** Fornece uma interface para os usuários redefinirem suas senhas.
- **Arquivos:**
  - `forgot-password.component.html`
  - `forgot-password.component.ts`
  - `forgot-password.routes.ts`

#### **Política**
- **Propósito:** Exibe informações relacionadas às políticas da aplicação.
- **Arquivos:**
  - `politica.component.html`
  - `politica.component.ts`
  - `politica.routes.ts`

#### **Redefinição de Senha**
- **Propósito:** Permite que os usuários redefinam suas senhas.
- **Arquivos:**
  - `reset-password.component.html`
  - `reset-password.component.ts`
  - `reset-password.routes.ts`

#### **Login**
- **Propósito:** Implementa a funcionalidade de login do usuário.
- **Arquivos:**
  - `sign-in.component.html`
  - `sign-in.component.ts`
  - `sign-in.routes.ts`

#### **Logout**
- **Propósito:** Gerencia o logout do usuário.
- **Arquivos:**
  - `sign-out.component.html`
  - `sign-out.component.ts`
  - `sign-out.routes.ts`

#### **Cadastro**
- **Propósito:** Implementa o processo de registro de usuários.
- **Arquivos:**
  - `sign-up.component.html`
  - `sign-up.component.ts`
  - `sign-up.routes.ts`

#### **Termos**
- **Propósito:** Exibe os termos de serviço.
- **Arquivos:**
  - `termos.component.html`
  - `termos.component.ts`
  - `termos.routes.ts`

#### **Desbloquear Sessão**
- **Propósito:** Desbloqueia uma sessão de usuário após inatividade.
- **Arquivos:**
  - `unlock-session.component.html`
  - `unlock-session.component.ts`
  - `unlock-session.routes.ts`

---

### Módulo Landing
O módulo `landing` gerencia as páginas públicas da aplicação.

#### **Home**
- **Propósito:** Exibe a página inicial.
- **Arquivos:**
  - `home.component.html`
  - `home.component.ts`
  - `home.routes.ts`

#### **Configuração Inicial**
- **Propósito:** Guia os usuários pelo processo de configuração inicial.
- **Arquivos:**
  - `setup.component.html`
  - `setup.component.ts`
  - `setup.routes.ts`

---

### Módulo Pages
O módulo `pages` inclui diversas páginas funcionais da aplicação.

#### **Dashboard**
- **Propósito:** Exibe análises chave e informações do usuário.
- **Arquivos:**
  - `dashboard.component.html`
  - `dashboard.component.ts`
  - `dashboard.routes.ts`

#### **Configurações**
O módulo `settings` gerencia preferências do usuário e configurações de conta.

##### **Conta**
- **Propósito:** Gerencia as configurações da conta do usuário.
- **Arquivos:**
  - `account.component.html`
  - `account.component.ts`

##### **API**
- **Propósito:** Gerencia chaves de API e integrações.
- **Arquivos:**
  - `api.component.html`
  - `api.component.ts`

##### **Segurança**
- **Propósito:** Gerencia configurações de segurança, como troca de senha e autenticação em duas etapas (2FA).
- **Arquivos:**
  - `security.component.html`
  - `security.component.ts`

##### **Configurações Gerais**
- **Propósito:** Serve como ponto de entrada para as configurações do usuário.
- **Arquivos:**
  - `settings.component.html`
  - `settings.component.ts`
  - `settings.routes.ts`

---


## Backend (Django)

### Visão Geral da Aplicação

O backend desta aplicação é construído usando Django, um framework web de alto nível em Python que incentiva o desenvolvimento rápido e um design limpo e pragmático. Ele lida com toda a lógica do lado do servidor, incluindo integrações de API, processamento de dados e geração de PDF, garantindo uma operação de backend perfeita para a aplicação.

### Funcionalidade Principal

- **Integração com API Udemy:** O backend sincroniza dados de cursos da Udemy usando sua API, armazenando os dados no banco de dados local para uso na geração de certificados e relatórios.
- **Geração de Certificados:** A aplicação gera certificados em PDF para usuários que concluíram cursos, utilizando o módulo `pdf_generator.py`.
- **Relatórios de Dados:** Utiliza `report_generator.py` para criar relatórios abrangentes com base em atividades de usuários e dados de conclusão de cursos.

### Integração com API Udemy

A integração com a API Udemy é gerenciada principalmente dentro do aplicativo `api_integration`. Isso inclui:
- **Scripts:** O módulo `scripts/udemy.py` gerencia a extração de dados da API Udemy.
- **Modelos:** Definidos em `models/udemy_api.py`, representando a estrutura de dados para armazenamento de informações de cursos e atividades de usuários.
- **Views:** Localizado em `views/udemy_api.py`, expondo endpoints para recuperação e processamento de dados da Udemy.

### Geração de PDF

A geração de certificados é gerenciada pelo módulo `pdf_generator.py`, que constrói e renderiza documentos PDF com base nos dados de usuários e no status de conclusão de cursos. Os PDFs são armazenados no diretório `media` e podem ser baixados pelos usuários através do frontend.

### Relatórios

Relatórios abrangentes de usuários e cursos são gerados usando `report_generator.py`, fornecendo insights sobre taxas de conclusão de cursos e métricas de engajamento de usuários. Os relatórios são acessíveis através da interface administrativa e podem ser usados para decisões estratégicas.

### Modelos de Dados

A aplicação inclui vários modelos-chave:
- **Dados da API Udemy:** Definidos em `models/udemy_api.py`, modelando dados de conclusão de cursos e usuários.
- **Atividade do Usuário:** Capturado em `models/user_activity.py`, acompanhando interações de usuários e progresso em cursos.
- **Atividade de Curso do Usuário:** Detalhado em `models/user_course_activity.py`, mapeando o progresso dos usuários em diferentes cursos.

### Endpoints de API

Os endpoints de API são definidos em `urls.py` e implementados nos respectivos módulos de visualização:
- **Endpoints de Dados Udemy:** Gerenciados por `views/udemy_api.py`, fornecendo acesso a dados de cursos e usuários.
- **Endpoints de Atividade do Usuário:** Gerenciados por `views/user_activity.py` e `views/user_course_activity.py`, expondo dados relevantes às interações de usuários e atividades de cursos.
- **Endpoints de Relatórios:** Incluídos em `views/reports.py`, permitindo que os usuários acessem relatórios gerados.

### Componentes Adicionais

- **Configuração do Admin:** Gerenciado por `admin.py` para administração de modelos de dados.
- **Serializadores:** Localizados em `serializers/`, transformando tipos de dados complexos em JSON e vice-versa.
- **Utilitários:** Funções e classes utilitárias são definidas em `utils/`, incluindo autenticação customizada e gerenciamento de tarefas em nuvem.
- **Testes:** Casos de teste são implementados em `tests.py`, garantindo a robustez e confiabilidade da lógica do backend.

---

## Implantação

### Configuração do Docker
Instruções sobre como configurar e usar o Docker para a aplicação.

### Variáveis de Ambiente
Liste e explique as variáveis de ambiente necessárias.

### Considerações para Produção
Discuta considerações e configurações para implantar em um ambiente de produção.

### Pipeline CI/CD
Visão geral da configuração do pipeline CI/CD para a aplicação.

---

## Testes

### Testes Unitários
Explique a estratégia de testes unitários e a cobertura.

### Testes de Integração
Discuta os testes de integração e como diferentes partes da aplicação são testadas em conjunto.

---

## Contribuindo

### Código de Conduta
Descreva o comportamento esperado e o código de conduta para colaboradores.

### Diretrizes de Contribuição
Forneça diretrizes sobre como contribuir para o projeto.

---

## Licença
Inclua informações de licenciamento para o projeto.
