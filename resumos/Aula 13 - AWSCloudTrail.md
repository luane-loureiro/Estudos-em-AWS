# Aula 13 - AWS CloudTrail 

## Introdução ao AWS CloudTrail
O AWS CloudTrail é um serviço da web que registra chamadas de API
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4175ef4c-3134-41ee-9b65-fc65bd0eef49)

O AWS CloudTrail é um serviço da web que registra chamadas da interface de programação de aplicativo (API) da AWS para sua conta e entrega arquivos de log para você.
O CloudTrail é uma ferramenta crucial para simplificar a governança, a conformidade e a auditoria de riscos. Tudo na AWS é uma chamada de API. O
CloudTrail registra as chamadas de API feitas em uma conta da AWS entre as regiões AWS. Ele faz isso se essa ação foi executada usando a AWS Command Line Interface (AWS CLI), um kit de desenvolvimento de software (SDK), o console ou diretamente por meio de uma API.
Os logs de serviço incluem ações como: 
- Iniciar e interromper instâncias
- Criar ou modificar bancos de dados do Amazon Relational Database Service(Amazon RDS)
- Fazer upload de um arquivo para o Amazon Simple Storage Service (Amazon S3).

## Benefícios do AWS CloudTrail 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c786f1ea-c4b9-4bd3-9958-806ede454f8e)

O CloudTrail tem vários benefícios importantes:
- Ele aumenta a visibilidade da atividade de usuários e recursos. Com essa visibilidade, você pode identificar quem fez o quê e quando em sua conta da AWS.
- As auditorias de conformidade são simplificadas porque as atividades são registradas e armazenadas automaticamente nos logs de eventos. O registro de atividades permite pesquisar dados de log, identificar ações que não estão em conformidade, acelerar investigações sobre incidentes e, então, agilizar uma resposta.
- Como você é capaz de capturar um histórico abrangente de alterações feitas em sua conta, é possível analisar e solucionar problemas operacionais relacionados a ela.

## Como o CloudTrail funciona? 
1. Uma atividade acontece em sua conta.
2. O CloudTrail captura e registra essa atividade, que é chamada de evento do CloudTrail. O evento contém detalhes sobre o seguinte:
  - Quem realizou a solicitação 
  - Data e hora da solicitação 
  - Endereço IP (Protocolo de Internet) de origem 
  - Como a solicitação foi feita 
  - Ação executada 
  - Região onde a ação foi realizada 
  - Resposta

Por padrão, os logs são armazenados por 7 dias. Você pode enviar o log de atividades para outros serviços da AWS. Portanto, é possível reter o histórico de atividades pelo tempo que quiser.

## Uso do CloudTrail 
Para aproveitar ao máximo o CloudTrail, ative as validações de arquivos de log dele. Ao configurar o CloudTrail, você pode agregar todos os arquivos de log em um único bucket do S3.

Uma configuração que se aplique a todas as regiões significa que todas as configurações serão aplicadas de modo consistente em todas as regiões atuais e recém-criadas.

Você também pode validar a integridade dos arquivos de log detectando se eles foram alterados ou excluídos após o envio ao bucket do S3. Também é uma boa prática executar a autenticação multifator (MFA) para excluir um bucket do CloudTrail. Isso pode ser feito restringindo o acesso ao local onde eles estão armazenados.

A integração do CloudTrail ao Amazon CloudWatch permite definir ações a serem executadas quando o CloudTrail registrar eventos específicos. 
O CloudWatch é um serviço de monitoramento para recursos da nuvem AWS. Você pode usar o serviço para coletar e monitorar métricas, coletar e monitorar arquivos de log, definir alarmes e reagir automaticamente a alterações nos recursos da AWS. 
A integração do CloudTrail ao CloudWatch também fornece um histórico de eventos abrangente, seguro e pesquisável das atividades. Essas atividades podem ser originadas do console, dos AWS SDKs, das ferramentas de linha de comando e de outros serviços da AWS.

#### Práticas recomendadas
- Ative a validação de arquivos de log do CloudTrail.
- Agregue arquivos de log a um único bucket do S3.
- Certifique-se de que o CloudTrail esteja ativado globalmente na AWS.
- Restrinja o acesso aos buckets do S3 do CloudTrail.
- Integração com o Amazon CloudWatch
