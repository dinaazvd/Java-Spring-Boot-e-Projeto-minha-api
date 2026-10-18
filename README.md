# Java-Spring-Boot-e-Projeto-minha-api

# Passo a Passo: Criando uma API com Java e Spring Boot

## 1. Configurando o Projeto no Spring Initializr

O primeiro passo é gerar a estrutura base do projeto através do site do Spring Initializr.

*   **Acesse o gerador:** https://start.spring.io/.
*   **Project (Gerenciador de Pacotes):** Selecione **Maven**. (Ele é o mais difundido no mercado Java).
*   **Language:** Selecione **Java**.
*   **Spring Boot Version:** Escolha a versão mais recente e estável (aquela que não possui os sufixos "SNAPSHOT" ou "M2"). Recomendado o uso da versão `4.1.1` ou `4.0.8`.
*   **Project Metadata:**
    *   **Group:** Define o *reverse domain* da aplicação (ex: `br.com.sistemasjefter` ou o padrão `com.example`).
    *   **Artifact:** Insira `minha-primeira-api` (é recomendado utilizar o padrão *kebab-case*, ou seja, com traços separando as palavras).
*   **Packaging:** Mantenha a opção **Jar**.
*   **Java Version:** Selecione a versão correspondente ao JDK instalado na sua máquina ( estou usando a versão **25**, mas se você tem a 17 ou a 21, selecione a que corresponde).

### Adicionando Dependências
No painel direito da interface, clique em **Add Dependencies** e busque por:
1.  **Spring Web:** Necessário para construir a API e lidar com as requisições HTTP (arquitetura RESTful).
2.  **Spring Data MongoDB:** Necessário para fazer a integração futura com o banco de dados MongoDB. (Cuidado para não escolher a opção que apenas diz "MongoDB", deve ser a versão "Spring Data").

### Gerando o Arquivo
Após conferir tudo, clique no botão **Generate**. O site fará o download de um arquivo `.zip` chamado `minha-primeira-api.zip`.

---

## 2. Extraindo o Projeto

*   **Descompactação correta:** Extraia os arquivos para uma pasta no seu computador.
*   **ATENÇÃO (Regra da Raiz):** Certifique-se de extrair o conteúdo diretamente, sem criar uma subpasta redundante (não crie uma pasta dentro de outra pasta com o mesmo nome). Os arquivos do projeto devem estar logo na raiz da pasta que você abrir.

---

## 3. Abrindo e Configurando o Projeto no IntelliJ

*   Abra a IDE **IntelliJ IDEA**.
*   Clique em **Open** e navegue até a pasta recém-extraída do seu projeto (`minha-primeira-api`) e selecione-a.
*   Se aparecer um prompt de segurança, clique em **Trust Project** (Confiar no projeto).

### Conferindo a Estrutura (Project Structure)
Para evitar erros de compilação, você deve alinhar as versões do Java na IDE.

1.  Vá no menu (geralmente nos 4 traços superiores) e selecione **Project Structure**.
2.  Na aba **Project**, garanta que o *SDK* e o *Language Level* estejam setados para a sua versão do Java (ex: **25**). Use a opção `Compact` se disponível.
3.  Na aba **Modules**, certifique-se de que o *Language level* também está como **25**.
4.  Clique em **Apply** / **OK**.

### Resolvendo Erros do Maven
Se as palavras no código estiverem sublinhadas em vermelho (indicando que as dependências não baixaram corretamente), force o download através do Maven:
1.  Abra a aba **Maven** no canto superior direito do IntelliJ.
2.  Navegue por `minha-primeira-api` > `Lifecycle`.
3.  Dê um duplo clique em **install**. O IntelliJ irá baixar todas as dependências (isso pode levar alguns minutos dependendo da sua internet).
4.  *Se ocorrer erro de caminho/compilador:* Vá em **Settings > Build, Execution, Deployment > Build Tools > Maven** e verifique se as configurações de compilação do Java estão apontando para o JDK 25.

---

## 4. Testando a Execução Padrão

*   No lado esquerdo do IntelliJ, navegue pelas pastas: `src` > `main` > `java` > pacote do projeto.
*   Abra o arquivo principal (geralmente chamado `MinhaPrimeiraApiApplication.java`).
*   Clique no botão de **Play** (ícone de execução verde) localizado ao lado da declaração da classe principal ou do método `main`.
*   Acompanhe o painel do terminal inferior. Se estiver tudo certo, aparecerá o logo do Spring em ASCII e a mensagem de que o Tomcat inicializou na porta **8080** (`Tomcat initialized with port(s): 8080`).

---

## 5. Criando a Rota da API (Controller)

Agora o objetivo é criar uma rota real que o servidor irá responder.

1.  **Criando o Package:** Na aba esquerda, clique com o botão direito sobre o seu pacote base (onde está o arquivo Application), escolha **New > Package** e nomeie-o como `controllers`.
2.  **Criando a Classe:** Clique com o botão direito no recém-criado pacote `controllers`, selecione **New > Java Class** e chame de `Estudante` (Lembre-se da convenção PascalCase, começando com letra maiúscula).

### Escrevendo o Código do Controller
Abra a classe `Estudante` e escreva o código abaixo.

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

// 1. Informa ao Spring Boot que esta classe é um controlador de rotas
@RestController
// 2. Define o prefixo do caminho base para esta classe
@RequestMapping("/api/estudantes")
public class Estudante {

    // 3. Define que este método responderá por uma requisição HTTP do tipo GET
    @GetMapping
    public String hello() {
        return "Hello World"; // Mensagem de retorno da API
    }
}
