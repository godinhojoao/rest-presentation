# Arquitetura REST
  ### O que é uma API ( Application Programming Interface ) ?
    - Como o nome já diz: Uma interface de programação. É um intermediário que permite duas aplicações distintas conversarem entre si.
    - Conjunto de rotinas e padrões que uma aplicação disponibiliza para que outras aplicações peguem essa informação.
    - Exemplo: Um aplicativo que consome a API do github para listar repositórios.

  ### O que é HTTP ( hypertext transfer protocol ) e quais suas características ?
      - É um protocolo de transferência de texto, utilizado para trafegar dados.
      - Funciona com `Requisição` e `Resposta`
      - Stateless: Chamadas não dependem uma da outra, cada chamada deve ter os dados necessários para "funcionar" sozinha. ( não guardam estado )
      - Headers: São informações adicionais de uma `requisição` ou `resposta` HTTP
      - Metodos HTTP - ( CRUD )
        - GET: Utilizado para buscar dados
        - POST: Utilizado para enviar dados.
        - PUT: Utilizado para atualizar dados.
        - DELETE: Utilizado para deletar dados.
    - Status code ( 1xx - 2xx - 3xx - 4xx - 5xx )
      - 1xx: `Informacional` - Avisa o que está acontecendo ( é "novo" )
        - 102: Processing ( Aceitou a requisição, mas ainda não foi completada e ainda não há resposta )
      - 2xx: `Sucesso` - Exemplos com *usuários*:
        - 200: Ok ( após fazer um `GET` em uma URL e ter os usuários retornados )
        - 201: Created ( após fazer um `POST` em uma URL e criar um usuário )
        - 204: No Content ( após fazer um `DELETE` em uma URL e deletar um usuario )
      - 3xx: `Redirecionamentos`
        - 301: Moved Permanently - ( Quando um recurso muda de endereço. A resposta deve conter o header: Location com a "nova" URL )
      - 4xx: `Erros de cliente`
        - 400: Bad Request - ( Quando o cliente manda uma request mal formatada )
        - 404: Not Found - ( O servidor não tem a URL solicitada )
      - 5xx: `Erros de servidor`
        - Geralmente são erros que o `log` é enviado apenas para o servidor e não para o client. Por ser algo mais "privado" como: um erro do banco de dados.
        - 500: Internal Server Error - ( Algum erro no servidor que impediu que a resposta fosse enviada da forma esperada )

  ### O que é REST e quais suas características ?
  - REST é um conjunto de características arquiteturais ( padrões ) e restrições que podem ser implementados em uma API.
  - Quando, por quem e por que foi criada ?
    - Criado no ano 2000 por Roy Fielding, para dar "sentido" as requisições HTTP e tornar o uso desse protocolo mais padronizado e simplificado.
  - Utiliza os métodos HTTP corretos para determinadas ações:
    - Get para buscar dados, Post para enviar, Put para atualizar e Delete para deletar.
  - Utiliza os HTTP status code adequados para cada ocasião:
    - 400 erros de cliente, 500 erros de servidor, etc...
  - Recurso indicado na URL da requisição: ( nós temos duas opções )
    - Ou identificamos o tipo de recurso na mensagem, e aí quem consome a URL da requisição se vira para descobrir se é produtos, usuários, etc... ( incorreto )
    - Ou identificamos o tipo de recurso pela URL ( correto )
  - Formatos apropriado das URIs, por exemplo: ( seguimos um padrão de plural/:id )
      - Buscar todos os cadernos: /cadernos
      - Buscar um caderno: /cadernos/:id
      - Buscar todas folhas de um caderno: /cadernos/:id/folhas
      - Buscar uma folha de um caderno: /cadernos/:id/folhas/:folhaId
  ### Vantagens de utilizar arquitetura rest
    - Padronização e simplificação da API.
    - Dessa forma obtemos: agilidade, facilidade na manutenção, em consumir a API, simplificação nas mensagens trocadas, escalabilidade, entre outras vantagens... ( Redução de custo )

# RESTFUL
  ### O que é ?
    - O quanto nós seguimos a arquitetura REST.
    Significado com exemplos:
      - Palavras com o sufixo ful ( full == "cheio"):
      - Beautiful --> Beauty + full --> "beleza" + "cheio de" --> "cheio de beleza"
      - Restful --> REST + full --> "rest" + "cheio de" --> "cheio de rest"

  ### Modelo de maturidade REST ( Leonard Richardson ) --> Richardson Maturity Model
  #### O que é ?
    - Um modelo para classificar a maturidade de uma API REST. Classificar quão `RESTFUL` a API é.
  ### Separação do modelo em 4 niveis: ( 0 até o 3 )
  - sendo `0` o "menos adequado" e `3` o "mais adequado".
  #### Level 0:
    - Utiliza o XML ( eXtensible Markup Language )
      - É uma linguagem de marcação que define um conjunto de regras para codificação de documentos. Uma forma de representar dados, assim como JSON. ( porém diferente )
    - Não usa nem os metodos HTTP corretos para determinadas ações:
      - Buscar dados com o metodo: `POST`
      - Postar dados com o metodo: `POST`
      - Atualizar dados com o metodo: `POST`
      - Deletar dados com o metodo: `POST`
    - Só uma URI pra todos recursos
    - Utiliza status code errados
  #### Level 1:
  - Recursos com URIs específicas:
    - GET ALL PRODUCTS: `/products`
    - GET ONLY ONE PRODUCT: `/products/:id`
  - Continua utilizando um metodo ( POST ) pra todas ações possíveis
  #### Level 2:
    - Metodos HTTP corretos para determinadas ações
      - Buscar dados com o metodo: `GET`
      - Postar dados com o metodo: `POST`
      - Atualizar dados com o metodo: `PUT`
      - Deletar dados com o metodo: `DELETE`
    - Utiliza status code corretos
  #### Level 3:
    - Suporta `HATEOAS`:
      - Tudo o que pode ser feito naquela API ela mesma te diz. É a possibilidade de navegar em uma API apenas sabendo a URL inicial.
      ##### GET orders/1 --> orders/:id
      - Response sem HATEOAS:
        - {
            "buyer_id": 456,
            "order_date": "2020-15-08T09:30:00",
            "total_price": 4.99,
            "payment_date": null,
            "status": "open",
            "items": [
              {
                "product_id" : 789,
                "quantity": 1,
                "price": 4.99
              }
            ]
          }
      - Response com HATEOAS:
        - {
            "buyer_url": "/customers/456",
            "order_date": "2020-15-08T09:30:00",
            "total_price": 4.99,
            "payment_date": null,
            "status": "open",
            "items": [
              {
                "product_url" : "/products/789",
              }
            ]
          }

# Fontes: ( algumas não foram citadas )
  - HTTP status code, link: https://www.yeahhub.com/1xx-2xx-3xx-4xx-5xx-http-status-codes/
  - Full HTTP status code list + explanation of each, link: https://umbraco.com/knowledge-base/http-status-codes/
  - O que é API REST ?, link: https://www.redhat.com/pt-br/topics/api/what-is-a-rest-api
  - O que é API? REST e RESTful? | Mayk Brito, link: https://www.youtube.com/watch?v=ghTrp1x_1As&t=228s
  - 4 Maturity Levels of REST API Design, link: https://blog.restcase.com/4-maturity-levels-of-rest-api-design/
  - Richardson Maturity Model, link: https://martinfowler.com/articles/richardsonMaturityModel.html

# Exemplo de rest API level 2:
https://github.com/godinhojoao/login-app/tree/main/server

# Sinta-se a vontade para abrir um PR e contribuir com o projeto!!! :D