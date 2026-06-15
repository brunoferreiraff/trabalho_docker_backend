# Sistema de Cadastro de Filmes

## Objetivo
Desenvolver a continuação do sistema iniciado em aula, integrando front-end e back-end utilizando SpringBoot + Thymeleaf. Permitindo cadastro e listagem de filmes em uma interface web funcional.

## Itens Obrigatório

| Componentes da Equipe| Bruno César Franca Ferreira; Caio Campos; Guilherme Augusto dos Santos; Fernando Menezes |
<br></br>
| Tema escolhido | Sistema de Cadastro de Filmes |
<br></br>
| Tecnologias usadas | Spring Boot, Thymeleaf, Spring Data JPA, H2 Database, Bootstrap |
<br></br>
| Funcionalidades | Cadastrar, Listar, Alterar, Excluir |
<br></br>
| Como executar |


## Campos do filme

- Nome
- Gênero
- Duração (em minutos)
- Classificação

## Funcionalidades

- Tela de cadastro de filme (Nome, Gênero, Duração, Classificação)
- Botão "Novo Filme" que abre o formulário de cadastro
- Salvamento no banco H2
- Atualização automática da tabela de listagem após cadastrar
- Funcionalidade Alterar (editar filme existente)
- Funcionalidade Excluir (remover filme)
- Mensagem "Filme salvo com sucesso"

## Estrutura do projeto

```
filme-crud
├── pom.xml
└── src/main
    ├── java/com/
    │   ├── CadastroFilmeApplication.java
    │   ├── Filme.java
    │   ├── FilmeDAO.java
    │   └── WebControl.java
    └── resources
        └── templates
            ├── filmes.html
            └── form.html
```

## Como executar

Pré-requisitos: Java 17 (ou superior) e Maven instalados.
1. Abra o eclipse e seleciona o projeto CadastroFilme.java
2. Abra o docker
3. Procure pela imagem do postgres:latest
4. Configure o container: 1. Nome: postgres-db; 2. Port: 5432. 3. Variavel: POSTGRES_PASSWORLD; 4. Value: postgres
5. Rode o container
6. No eclipse, clique com o botão direito em cima do arquivo " CadastroFilmeApplication.java"
4. Selecione "Run As "
5. Escolha a Opção " Spring Boot App"
6. Clique duas vezes no arquivo que está no Boot Dashboard
7. Acesse no navegador:

```
http://localhost:8080/filmes
```
# COMANDOS POSTGRESQL NO DOCKER

## 1. VER TODOS OS FILMES (Todas as colunas)
docker exec -it postgres-db psql -U postgres -d banco -c "SELECT * FROM filme;"

## 2. VER TODOS OS TÍTULOS (Apenas a coluna 'nome')
docker exec -it postgres-db psql -U postgres -d banco -c "SELECT nome FROM filme;"

## 3. VER QUANTAS ENTRADAS POSSUEM NO BANCO (Contagem)
docker exec -it postgres-db psql -U postgres -d banco -c "SELECT COUNT(*) FROM filme;"

## 4. ADICIONAR UMA ENTRADA (Inserir novo filme)
docker exec -it postgres-db psql -U postgres -d banco -c "INSERT INTO filme (classificacao, duracao, genero, nome) VALUES (16, 148, 'Ficção Científica', 'Inception');"

## 5. ALTERAR UMA ENTRADA (Atualizar dados - Filtro por ID)
docker exec -it postgres-db psql -U postgres -d banco -c "UPDATE filme SET genero = 'Ação', classificacao = 14 WHERE id = 6;"

## 6. EXCLUIR UM ITEM DO BANCO (Deletar - Filtro por ID)
docker exec -it postgres-db psql -U postgres -d banco -c "DELETE FROM filme WHERE id = 6;"

## Fluxo de uso

1. Na tela principal, clique em **Novo Filme**.
2. Preencha o formulário (ex.: Nome: Matrix, Gênero: Ficção, Duração: 136, Classificação: 14 anos) e clique em **Salvar**.
3. O filme é salvo no banco e a tabela é atualizada automaticamente, exibindo a mensagem "Filme salvo com sucesso".
4. Use os botões **Alterar** e **Excluir** em cada linha para editar ou remover filmes.