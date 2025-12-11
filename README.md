
# 🐱‍🏍 Sistema de Gestão de Eventos - API Django REST

### Orientador
**Henrique Pereira de Freitas Filho** (Contato: henrique.filho@ifb.edu.br)

![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Django](https://img.shields.io/badge/Django-5.0-green)
![DRF](https://img.shields.io/badge/DRF-3.15-red)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 📚 Índice

* [1. Sobre o Projeto](#1-sobre-o-projeto)
* [2. Objetivos](#2-objetivos)
* [3. Tecnologias & Arquitetura](#3-tecnologias--arquitetura)
* [4. Funcionalidades Detalhadas](#4-funcionalidades-detalhadas)
* [5. Configuração do Ambiente](#5-configuração-do-ambiente)
* [6. Rotas Principais da API](#6-rotas-principais-da-api)
* [7. Estrutura e Modelos](#7-estrutura-e-modelos)
* [8. Implementação (Deploy)](#8-implementação-deploy)
* [9. Contribuição & Licença](#9-contribuição--licença)

## 1. Sobre o Projeto

O **Sistema de Gestão de Eventos** é uma API desenvolvida utilizando **Django REST Framework** para centralizar o gerenciamento de eventos acadêmicos e corporativos.

* **Contexto:** O projeto visa substituir métodos descentralizados (planilhas, formulários desconexos) por uma solução robusta e escalável, minimizando falhas e simplificando a gestão de eventos, participantes e atividades.
* **Solução:** Uma API RESTful que permite o CRUD completo e gerencia relacionamentos complexos entre as entidades.


## 2. Objetivos

### Objetivo Geral
Desenvolver uma API Backend com autenticação segura para gerenciar eventos, participantes, atividades e seus relacionamentos de forma integrada.

### Objetivos Específicos
* Modelagem de Entidades: **Evento**, **Participante** e **Atividade**.
* Implementação de Relacionamentos: 1:N, N:N e 1:1.
* Criação de CRUD (Create, Read, Update, Delete) completo para todas as entidades.
* Implementação de sistema de **autenticação JWT** (JSON Web Token).
* Desenvolvimento de **rotas de relacionamento** (mínimo 3).
* Criação de **rota composta A-B-C** (Dashboard/Visão Gerencial).


## 3. Tecnologias & Arquitetura

### 💻 Tecnologias (Exódos Utilizados)
| Categoria | Tecnologia | Versão | Propósito |
| :--- | :--- | :--- | :--- |
| **Backend** | Python | 3.11+ | Linguagem principal |
| **Web Framework** | Django | 5.0 | Estrutura web principal |
| **API** | Django REST Framework | 3.15 | Toolkit para construção de APIs REST |
| **Autenticação** | Simple JWT | 5.3 | Gerenciamento de tokens de acesso |
| **Ferramentas** | Git, VS Code | - | Controle de versão e Ambiente de Desenvolvimento |

### 🏛️ Arquitetura
A arquitetura é organizada em camadas (*Layered Architecture*):

* **API Layer:** Responsável pelos Endpoints REST e Rotas.
* **Business Layer:** Views e Serializers (lógica de negócios e validação de dados).
* **Data Layer:** Models Django (persistência de dados).
* **Auth Layer:** JWT Authentication (segurança e autorização).


## 4. Funcionalidades Detalhadas

| Entidade | Funcionalidade Principal | Relacionamento |
| :--- | :--- | :--- |
| **Eventos** | CRUD completo; Campos: `nome`, `descrição`, `data_início`, `data_fim`, `local`. | **1:N** com Atividade |
| **Participantes** | CRUD; Tipos: `estudante`, `palestrante`, `convidado`. | **N:N** com Evento |
| **Atividades** | Gerenciamento de atividades por evento; Tipos: `workshop`, `palestra`, `oficina`. | **1:1** com Participante (Responsável) |


## 5. Configuração do Ambiente

### 🔑 Pré-requisitos
Certifique-se de ter instalado:
* Python 3.11 ou superior
* Pip (gerenciador de pacotes)

**Verificação Rápida:**
```bash
python --version
pip --version

🛠️ Instalação e Execução
Siga os passos abaixo para configurar o ambiente local:
1. Clone o repositório:
git clone [https://github.com/usuario/projeto_api.git](https://github.com/usuario/projeto_api.git)
cd projeto_api

2. Crie e Ative um Ambiente Virtual:
python -m venv venv
# Linux/Mac
source venv/bin/activate  
# Windows
venv\Scripts\activate     

3. Instale as Dependências:
pip install -r requirements.txt

4. Configure as Variáveis de Ambiente:
cp .env.example .env
# Edite o arquivo .env com suas credenciais de banco de dados e chaves secretas.

5. Aplique as Migrações e Inicie o Servidor:
python manage.py migrate
python manage.py runserver

O servidor estará acessível em http://127.0.0.1:8000/.
6. Rotas Principais da API
A documentação interativa estará disponível em /api/docs/ (Swagger UI ou Redoc) após a execução do servidor local.
| Método | Endpoint (Exemplo) | Descrição | Autenticação |
|---|---|---|---|
| GET | /api/eventos/ | Lista todos os eventos | Opcional/Requerida (depende da view) |
| POST | /api/participantes/ | Cria um novo participante | Requerida |
| GET | /api/eventos/{id}/ | Recupera um evento específico | Opcional |
| POST | /api/auth/token/ | Obter Token JWT | Não Aplicável |
| GET | /api/dashboard/ | Rota Composta A-B-C (Visão Gerencial) | Requerida |
7. Estrutura e Modelos
📂 Estrutura do Projeto
(Recomendação: Adicione a árvore de diretórios do projeto aqui, como no modelo de referência.)
💾 Modelo de Dados (Diagramas)
(Recomendação: Substitua a seção "Diagrama de Banco de Dados" por um link ou imagem do seu Diagrama Entidade-Relacionamento.)
Link para o Diagrama Entidade-Relacionamento (ER)
8. Implementação (Deploy)
☁️ Plataforma Recomendada: [Render / Railway / AWS / Sua Escolha]
1. Prepare o Procfile:
web: gunicorn projeto.wsgi:application --log-file -

2. Processo de Deploy:
 * Configure variáveis de ambiente na plataforma de deploy.
 * Execute migrações em produção: python manage.py migrate
 * Colete arquivos estáticos (se aplicável): python manage.py collectstatic
> CI/CD: Integração com GitHub Actions disponível em .github/workflows/deploy.yml.
> 
9. Contribuição & Licença
🤝 Contribuição
 * Faça um fork do projeto.
 * Crie uma branch para sua funcionalidade: git checkout -b feature/MinhaNovaFeature
 * Faça commit das suas alterações: git commit -m 'feat: Adiciona nova feature X'
 * Envie para a branch original: git push origin feature/MinhaNovaFeature
 * Abra um Pull Request.
📜 Licença
Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE.md para mais detalhes.
👨‍🏫 Professor/Orientador
Henrique Pereira de Freitas Filho (henrique.filho@ifb.edu.br)


