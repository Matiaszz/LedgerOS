# 📊 LedgerOS

O **LedgerOS** é um projeto de controle financeiro pessoal desenvolvido para fins de aprendizado, focado na construção de uma arquitetura **Backend Serverless robusta** e na integração **Fullstack de ponta a ponta**.

---

## 🎯 Principais Objetivos de Aprendizado

O foco principal deste projeto está no **Backend e Infraestrutura em Nuvem**, com destaque para:

* ☁️ **Aplicações Serverless**: Uso do modelo *Function-per-Route* (Multi-Lambda) em **Java 21** na AWS.
* 🛡️ **API Gateway & Segurança**: Configuração de rotas, **Custom Authorizer** com JWT, Secrets Manager e CORS.
* ⚙️ **Separação de Ambientes (Dev / Prod)**: Gerenciamento de variáveis de ambiente com `env.json` localmente e parâmetros dinâmicos (`Stage=prod`) na nuvem via **AWS SAM / CloudFormation**.
* 🚀 **CI/CD & Deploy Automatizado**: Pipeline contínuo no **GitHub Actions** que compila o projeto Java 21, empacota os artefatos Serverless e realiza o deploy automático na AWS.
* 🏛️ **Clean Architecture**: Organização do código em camadas desacopladas (Domain, Use Cases, Presentation e Infrastructure).
* 🔄 **Integração Fullstack**: Conectar a API com um cliente frontend completo e funcional.

---

## 🚀 Pipeline de CI/CD

O projeto conta com automação de deploy contínuo configurado via **GitHub Actions** (`backend/.github/workflows/deploy.yml`):

1. **Trigger**: Executado automaticamente a cada `push` na branch `main` ou via acionamento manual (*workflow_dispatch*).
2. **Build**: Configuração do ambiente Java 21 (Temurin), compilação via Maven e empacotamento das Lambdas com `sam build`.
3. **Deploy Automático**: Autenticação segura na AWS e deploy da stack CloudFormation com o comando `sam deploy --parameter-overrides Stage=prod`.

---

## 🗺️ Roadmap de Desenvolvimento

### 📍 Fase 1 (Atual): Integração Fullstack com React
Construção e validação do ecossistema completo conectando o backend Java/AWS ao frontend em **React 19**. O objetivo desta etapa é entregar uma aplicação 100% funcional com autenticação, refresh tokens e consumo das rotas da API.

### 🔮 Fase 2 (Futura): Aprendizado & Migração para Angular
Após a conclusão e validação da integração com React, o frontend será migrado para **Angular**. Essa etapa terá como objetivo o aprendizado do ecossistema Angular:
- Arquitetura baseada em *Standalone Components*
- Injeção de Dependência nativa
- *Reactive Forms* e validações avançadas
- Gerenciamento de estado e reatividade com **RxJS** e **Signals**

---

## 📁 Estrutura do Projeto

* 🔹 [`backend/`](file:///E:/Projetos/Pessoal/LedgerOS/backend/README.md) – API Serverless em Java 21 + AWS SAM + GitHub Actions CI/CD (Foco Principal)
* 🔹 [`frontend-react/`](file:///E:/Projetos/Pessoal/LedgerOS/frontend-react/README.md) – Aplicação web atual em React 19
* 🔹 [`docs/`](file:///E:/Projetos/Pessoal/LedgerOS/docs/routes.md) – Documentação de rotas, autorizador e arquitetura da API

---

## 🛠️ Como Executar Localmente

### 1. Clonar o Repositório com Submódulos
```bash
git clone --recursive https://github.com/Matiaszz/LedgerOS.git
cd LedgerOS
```

### 2. Rodar o Backend Localmente (AWS SAM)
```bash
cd backend
mvn clean package
sam build
sam local start-api -n env.json
```
A API estará acessível em `http://127.0.0.1:3000`.

### 3. Rodar o Frontend (React)
```bash
cd frontend-react
npm install
npm run dev
```
O frontend estará acessível em `http://localhost:5173`.
