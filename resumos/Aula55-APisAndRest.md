# Aula 55 - APis And Rest
## APIs
Uma interface de programação de aplicativo (API): 
- Fornece acesso programático a um aplicativo.
    - Por exemplo, as APIs geralmente são usadas para programas que se comunicam entre si.
      
- Comporta várias linguagens de programação.
    - Por exemplo, API para Java, API para C++ e outras.

## APIs RESTful 
Transferência de estado representacional (REST):
- Um projeto para aplicativos de baixo acoplamento baseados em rede
- A comunicação é via HTTP
- Expõe recursos em URLs específicas
- Muitas APIs da web são RESTful

#### seis peincípiosdo design do RESTfull:
- uma interface uniforme
- stateless
- arquitetura cliente-servidor
- Armazenável em cache Sistema em camadas
- Código sob demanda (opcional) 


## Solicitções REST
os componente das solicitações de rest incluem:
- Endpoint (como URL)
- métodos
      - GET: para ler um recurso
      - POST: para criar um recurso –
      - PUT: para atualizar um recurso existente –
      - DELETE: para excluir um recurso

- Cabeçalho
      - Exemplo: –H "Content-Type: application/json"

- Dados (corpo)
      - Normalmente, parte das solicitações POST e PUT


## Códigos de status HTTP 
Códigos de status HTTP:
- 100: resposta informativa
- 200: sucesso
- 300: redirecionamento
- 400: erros do cliente
- 500: erros do servidor
- 200: indica êxito. O servidor recebeu e aceitou a solicitação.
- 401: indica um erro do cliente, Não autorizado. A autenticação é necessária, mas as credenciais fornecidas não foram aceitas, ou talvez nenhuma credencial tenha sido fornecida na solicitação.
- 403: indica um erro do cliente, Proibido. A solicitação foi feita corretamente, mas parece que o servidor não a permite.
- 404: indica um erro do cliente, Não encontrado. O recurso está indisponível ou não pôde ser acessado.
- 500: indica um erro de servidor interno não específico. 503: indica que o serviço está temporariamente indisponível.
