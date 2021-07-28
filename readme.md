# Arquitetura REST

  ### O que é Rest ?
  - O que é uma API ?
    - """"""falar sobre aqui""""""
  - O que é REST?
    - """"""falar sobre aqui""""""
  - Quando, por quem e por que foi criada ?
    - """"""falar sobre aqui""""""

  ### Como funciona ?
  - Como a Arquitetura REST funciona ?
    - o que é HTTP ( hypertext transfer protocol ) e quais suas características ?
      - É um protocolo de transferência de texto, utilizado para trafegar dados.
      - Stateless: chamadas não dependem uma da outra, cada chamada deve ter os dados necessários para "funcionar" sozinha
      - Metodos HTTP - ( CRUD )
        - GET: Utilizado para buscar dados
        - POST: Utilizado para enviar dados.
        - PUT: Utilizado para atualizar dados.
        - DELETE: Utilizado para deletar dados.
    - Status code ( 1xx - 2xx - 3xx - 4xx - 5xx )
      - 1xx: `Informacional` """"""falar sobre aqui""""""
        - exemplo de um codigo 100... """"""falar sobre aqui""""""
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
    - Formatos apropriado das URIs, por exemplo:
      -""""""falar sobre aqui""""""

  ### Vantagens de utilizar arquitetura rest
    -""""""falar sobre aqui""""""

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
  - sendo `0` o "menos adequado"
  #### Level 0:
    - Utiliza o XML ( falar o que é XML )
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
    - Suporta `HATEOS`:
      - """"""falar sobre aqui""""""

# Fontes:
  - 4 Maturity Levels of REST API Design, link: https://blog.restcase.com/4-maturity-levels-of-rest-api-design/
  - Richardson Maturity Model, link: https://martinfowler.com/articles/richardsonMaturityModel.html
  - HTTP status code, link: https://www.yeahhub.com/1xx-2xx-3xx-4xx-5xx-http-status-codes/
  - Códigos de status de respostas HTTP, link: https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status

### Ainda incompleto, portanto:
  - Onde tiver: """"""falar sobre aqui"""""" === falta adicionar informações