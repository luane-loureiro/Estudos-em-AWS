# Aula 21 - AWS CloudTrail

## O AWS CloudTrail é um serviço que:
- Registrar em log, monitorar continuamente e reter a atividade da conta relacionada a ações na sua infraestrutura da AWS
- Registrar chamadas de interface de programação de aplicativos (API) para a maioria dos serviços da AWS
    - As atividades do Console de gerenciamento da AWS e da AWS Command Line Interface (AWS CLI) também são registradas
- É compatível com um número crescente de serviços da AWS
- Envia logs automaticamente para o Amazon Simple Storage Service (Amazon S3) depois que ele é configurado
- Não rastreará eventos em uma instância do Amazon Elastic Compute Cloud (Amazon EC2)
    - Exemplo: desligamento manual de uma instância

## Exemplo do CloudTrail 
O CloudTrail pode ajudá-lo a responder a perguntas que exigem análise detalhada.
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/84acdb4b-4bc4-44c9-8400-1f469385e2e5)

## Configure uma trilha 
As etapas para configurar uma trilha são:
1. Configure um bucket novo ou existente do Amazon Simple Storage Service (Amazon S3) para fazer upload de arquivos de log.
2. Defina uma trilha para registrar os eventos desejados (todos os eventos de gerenciamento são registrados por padrão).
3.
Crie um tópico do Amazon Simple Notification Service (Amazon SNS) para receber notificações.
4. Configure o Amazon CloudWatch Logs para receber logs do CloudTrail (opcional).
5. Ative a criptografia de arquivos de log e a validação de integridade para arquivos de log (opcional).
6. Adicione tags à sua trilha (opcional). 

## Exemplo de entrada de log do AWS CloudTrail: 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/037a60a3-127e-40e8-84e5-c5a1f33c6db6)

Cada arquivo de log do CloudTrail formatado pelo JavaScript Object Notation (JSON) pode conter uma ou mais registros de log.
Uma entrada de log representa uma única solicitação de qualquer fonte. Ela inclui informações sobre a ação de solicitação e a resposta.
O exemplo mostra a seçãorequestParameters de uma entrada de log. Ela inclui parâmetros como: 
- **userIdentity** — Quem (ou qual aplicativo) realizou uma ação.
- **eventTime** — A data e a hora em que a ação ocorreu.
- **eventSource** — Uma indicação de se a ação foi feita por meio do console, da AWS CLI ou da chamada da API.

Parâmetros adicionais também podem ser incluídos. A lista real de parâmetros depende do tipo de ação que foi registrada.
Não é garantido que as entradas de log estejam em uma ordem específica. Elas não são um rastreamento de pilha de ordem de chamadas de API

## Monitoramento e segurança
Quando você monitora a atividade na sua conta e protege seus recursos e dados, os recursos do CloudWatch e do CloudTrail são complementares. 
Recomenda-se o uso de ambos os serviços. Por exemplo, você pode examinar os logs das entradas do CloudWatch Logs e do CloudTrail para detectar potenciais usos não autorizados.
**Exemplos:**
- Tentativas fracassadas de login no Console de gerenciamento da AWS ou de login de endereços IP suspeitos
- Acesso não autorizado aos serviços que usam a API
- Execuções suspeitas de recursos




