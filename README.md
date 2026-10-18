# 🎓 Sistema de Gestão de Estudantes (API RESTful)

Este projeto consiste em uma API (Application Programming Interface) desenvolvida em **Java** utilizando o framework **Spring Boot**. O objetivo principal da aplicação é fornecer uma interface de comunicação robusta e escalável para gerenciar dados acadêmicos, servindo como o *backend* de um sistema acadêmico completo.

## 📖 Sobre o Projeto

A necessidade de digitalizar e organizar registros acadêmicos exige sistemas que sejam rápidos, seguros e fáceis de manter. Esta API foi concebida para abstrair a complexidade do gerenciamento de alunos, permitindo que aplicações *frontend* (web ou mobile) consumam, cadastrem e atualizem informações de maneira padronizada via requisições HTTP.

A arquitetura do projeto foi desenhada para ser modular, preparando o terreno para a implementação de padrões de projeto consolidados no mercado, como a separação por camadas (Controllers, Services e Repositories).

## 🎯 Objetivos da API

Embora o projeto esteja em suas fases iniciais de desenvolvimento, a visão arquitetônica contempla os seguintes recursos:

* **Integração de Dados:** Centralizar as informações dos estudantes em um único serviço.
* **Comunicação Padronizada:** Utilizar o padrão REST (Representational State Transfer) com respostas em formato JSON.
* **Escalabilidade:** Uso do ecossistema Spring, que permite fácil expansão e adição de novos módulos no futuro.
* **Persistência Não-Relacional:** Preparação estrutural para armazenar documentos flexíveis utilizando o banco de dados NoSQL **MongoDB**.

## 🛠️ Stack Tecnológico

A escolha das tecnologias visa modernidade, performance e alta adoção no mercado corporativo:

* **Linguagem:** Java (JDK 25)
* **Framework Principal:** Spring Boot 4+
* **Web:** Spring Web (para mapeamento de endpoints REST)
* **Persistência:** Spring Data MongoDB
* **Gerenciamento de Dependências:** Maven

## 🌐 Visão Geral da Comunicação

A API atua como um servidor central que escuta requisições na porta padrão `8080`. A comunicação é feita através de rotas semânticas. 

Atualmente, o serviço conta com o módulo de estudantes (`/api/estudantes`), que no momento implementa um *Health Check* (teste de disponibilidade) retornando uma mensagem de saudação simples (`Hello World`) para validar que a camada de controle (*Controller*) está operando corretamente e pronta para receber as lógicas de negócio.
