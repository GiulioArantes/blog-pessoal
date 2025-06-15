# Blog-Pessoal

![Blog-Pessoal on Render](https://i.postimg.cc/fTLSy2QP/Render-swagger.png)

O **Blog-Pessoal** é uma API completa e intuitiva para postagem e divulgação de conteúdos diversos, construída com **Spring Boot** no backend e **React** no frontend. Permite que os usuários cadastrem, atualizem e excluam postagens e temas.

**Você pode acessar a API hospedada clicando [aqui](https://blogpessoal-nngj.onrender.com/).**

### 🔗 **Sobre o Frontend**
>🔧 **Observação:** Existe um frontend disponível para você visualizar e interagir com o backend de forma prática e visual. Acesse o site clicando [aqui](https://blog-pessoal-frontend-bice.vercel.app/).

>📂 Caso queira consultar o código-fonte, entender a estrutura ou rodar o frontend localmente, acesse o repositório neste [link](https://github.com/GiulioArantes/blog-pessoal-frontend).

## ✨ Funcionalidades

* 🔗 **API RESTful completa**, seguindo boas práticas de desenvolvimento.
* **🔎 CRUD de Usuários, Postagens e Temas:**
    * Cadastrar, listar, editar e excluir.
    * Buscar por ID, nome ou departamento.

*  🏗️ **Arquitetura organizada:**
    * **Model:** Estrutura das entidades (**Usuário**, **Postagem** e **Categoria**).
    * **Repository:** Comunicação com o banco de dados, incluindo consultas personalizadas.
    * **Service:** Regra de negócio e tratamento de erros.
    * **Controller:** Disponibilização dos endpoints para consumo externo.
    * **Security:** Implementação de autenticação e segurança com JWT.
*  🚀 **Escalável:** Arquitetura pensada para facilitar o crescimento do projeto e a inclusão de novas funcionalidades no futuro.
> 💡 Este projeto vai além de um MVP e está em constante evolução para atender a demandas mais robustas no gerenciamento de conteúdo.

## 🚀 Tecnologias Utilizadas

Este projeto foi construído com uma stack moderna, performática e escalável:

* **Frontend:**
    * [**React**](https://reactjs.org/) - Biblioteca para construção de interfaces de usuário.
    * [**Tailwind CSS**](https://tailwindcss.com/) - Framework de utilitários para estilização rápida e responsiva.
* **Backend & Banco de Dados:**
    * [**Spring Boot**](https://spring.io/projects/spring-boot) - Framework Java para aplicações web robustas e seguras.
    * [**PostgreSQL**](https://www.postgresql.org/) - Banco de dados relacional utilizado no ambiente de **produção**.
    * [**MySQL**](https://www.mysql.com/) - Banco de dados relacional utilizado no ambiente de **desenvolvimento**.
* **Hospedagem e Deploy:**
    * [**Vercel**](https://vercel.com/) - Plataforma utilizada para o deploy do **front-end**.
    * [**Render**](https://render.com/) — Plataforma utilizada para hospedar o **backend**.
    * [**Docker**](https://www.docker.com/) - Containerização utilizada no deploy via **Render**.
* **Testes:**
    * [**Postman**](https://www.postman.com/) - Ferramenta para teste e validação de APIs.

## ⚙️ Como Rodar o Projeto

### 🖥️ Aplicação Back-end

Siga os passos abaixo para executar o backend localmente:

```bash
# 1. Clone o repositório
git clone https://github.com/GiulioArantes/blog-pessoal.git

# 2. Navegue até o diretório do projeto
cd blog-pessoal

# 3. Configure o arquivo application.properties em:
src/main/resources/application.properties

# 4. Defina o perfil de desenvolvimento
spring.profiles.active=dev

# 5. Configure suas credenciais e dados do banco MySQL

# 6. Execute a aplicação via sua IDE ou pelo terminal
```

### 🌐 Front-end

> **🔗 Importante:** Para utilizar este backend, você pode rodar o frontend localmente ou utilizar ferramentas como o Postman.
> Acesse o repositório do frontend [aqui](https://github.com/GiulioArantes/blog-pessoal-frontend) e siga as instruções para execução.

### 🔗 Endpoints

> ✅ Supondo que a aplicação está rodando na porta padrão `localhost:8080` (ajuste conforme necessário).

**GET**
* `/usuarios/all` — Lista todos os usuários  
* `/postagens` — Lista todas as postagens
* `/temas` — Lista todos os temas
* `/usuarios/{id}` — Busca um usuario por ID
* `/postagens/{id}` — Busca uma postagem por ID
* `/temas/{id}` — Busca um tema por ID
* `/postagens/titulo/{titulo}` — Busca postagens por título
* `/temas/descricao/{descricao}` — Busca temas por descrição

**POST & PUT**
* `/usuarios/cadastrar` — Cria um novo usuário
* `/usuarios/atualizar` — Atualiza os dados de um usuário
* `/usuarios/logar` — Realiza login (gera o token JWT)
* `/postagens` — Cria ou atualiza uma postagem
* `/temas` — Cria ou atualiza um tema

> ⚠️ No método **PUT**, o ID do item a ser alterado deve ser informado no corpo do JSON.

> ⚠️ É necessário cadastrar e autenticar um usuário antes de acessar os demais endpoints protegidos.

**DELETE**
* `/postagens/{id}` — Deleta uma postagem
* `/temas/{id}` — Deleta um tema

### 🗂️ Atributos das entidades

🔹**Usuario**

| Atributo        | Tipo              | Descrição                                      |
| --------------- | ----------------- | ---------------------------------------------- |
| `id`            | Long              | Identificador único (gerado automaticamente)   |
| `nome`          | String            | Nome do usuário                                |
| `usuario`       | String            | E-mail do usuário (utilizado na autenticação)  |
| `senha`         | String            | Senha do usuário                               |
| `foto`          | String            | URL da foto do usuário                         |
| `postagem`      | List\<Postagem>   | Lista de postagens associadas (um para muitos) |

🔹**Postagem**

| Atributo        | Tipo       | Descrição                                            |
| --------------- | ---------- | ---------------------------------------------------- |
| `id`            | Long       | Identificador único (gerado automaticamente)         |
| `titulo`        | String     | Título da postagem                                   |
| `texto`         | String     | Conteúdo da postagem                                 |
| `data`          | LocalDate  | Data de criação da postagem (gerada automaticamente) |
| `tema`          | Tema       | Tema vinculado (muitos para um)                      |
| `usuario`       | Usuario    | Usuário autor da postagem (muitos para um)           |

🔸 **Tema**

| Atributo     | Tipo            | Descrição                                      |
| ------------ | --------------- | ---------------------------------------------- |
| `id`         | Long            | Identificador único (gerado automaticamente)   |
| `descricao`  | String          | Descrição do tema                              |
| `postagem`   | List\<Postagem> | Lista de postagens associadas (um para muitos) |

✅ **Observação:**
* A entidade **Postagem** está associada a **um único Tema** e **um único Usuário**.
* As entidades **Tema** e **Usuario** podem ter várias **Postagens** vinculadas.
* O campo `foto` na entidade **Usuario** recebe um **link (URL)** da imagem.
* O campo `usuario` na entidade **Usuario** representa o **e-mail** utilizado para autenticação.
* O campo `data` em **Postagem** registra automaticamente o momento da criação.

## 🤝 Contribuição

Sua colaboração é muito bem-vinda! Existem duas formas de contribuir:

* **💡 Sugestões e feedbacks:** Me envie um e-mail em [giulio.arantes@icloud.com](giulio.arantes@icloud.com) ou me chame no [LinkedIn](https://www.linkedin.com/in/giulio-arantes/).
* **🔧 Contribuição no código:** Fork o projeto, crie suas melhorias e envie um Pull Request.

> Toda contribuição será analisada com atenção e respeito. Vamos construir algo incrível juntos! 💙
