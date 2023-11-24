## Aula 20 - Aprofundamento: Amazon CloudWatch - Logs e eventos
## Amazon CloudWatch Events
O Amazon CloudWatch Events oferece um streaming quase em tempo real de eventos do sistema que descrevem as alterações feitas aos recursos da AWS. 
Com regras simples que você pode configurar, é possível corresponder eventos e roteá-los para um ou mais streams ou funções de destino. 
O CloudWatch Events torna-se ciente das alterações operacionais à medida que ocorrem. 
Ele responde a essas mudanças operacionais enviando mensagens, ativando funções, fazendo alterações e capturando informações de estado.
Você pode usar o CloudWatch Events para programar ações automatizadas que sejam acionadas automaticamente em determinados momentos usando as expressões cron ou rate. 

Você também pode configurar eventos programados a serem gerados periodicamente.
- **Destinos** – Um destino processa eventos. Os destinos de exemplo incluem instâncias do EC2, funções do AWS Lambda, tópicos do Amazon Simple Notification Service (Amazon SNS) e filas do Amazon Simple Queue Service (Amazon SQS).
- **Regras** – Uma regra faz a correspondência de eventos de entrada e os encaminha aos destinos para o processamento. Uma única regra pode encaminhar para vários destinos, todos processados paralelamente. Isso permite que diferentes partes de uma organização procurem e processem os eventos que as interessam.

No exemplo, uma regra do CloudWatch Event está sendo criada.
Aqui, sempre que uma nova instância é criada, um script do AWS Systems Manager Run Command é executado na instância.

## Amazon CloudWatch Logs 
### Processo típico de análise de log 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/16d48493-f10f-4092-8733-b1af508e6f7e)

Você pode usar o Amazon CloudWatch Logs para monitorar, armazenar e acessar os seus arquivos de log de instâncias do Amazon EC2, do AWS CloudTrail, do Amazon Route 53 e de outras origens. Você pode recuperar os dados de log associados ao CloudWatch Logs.
É possível monitorar os seus logs praticamente em tempo real, em busca de frases, valores ou padrões específicos.
Os dados de log podem ser armazenados e acessados indefinidamente, bem como armazenados externamente em instâncias do EC2, para que você não precise se preocupar com o preenchimento de discos rígidos.

### Funcionalidade do Amazon CloudWatch Logs 
A funcionalidade do CloudWatch Logs inclui:
- Coleta automática de logs (por exemplo, de instâncias do EC2)
- Como agregar dados em grupos de logs
- Ser capaz de configurar filtros de métricas em um grupo de logs
    - Procurar padrões de string específicos
    - Fazer com que cada correspondência incremente uma métrica personalizada do CloudWatch
    - Usar a métrica para criar alarmes do CloudWatch ou enviar notificações
- Consultar logs e criar visualizações com o CloudWatch Logs Insights

### Criar alarmes do CloudWatch em métricas de filtro de log 
Use os alarmes do CloudWatch para relatar condições fora do limite descobertas em arquivos de log.
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/7b255812-7920-44da-bb1b-210fcfc5bca9)

No diagrama, ocorrem os seguintes processos:
1. Um grupo de logs do CloudWatch chamado HttpAccessLog contém dados de log agregados. Os dados de log são coletados pelos agentes do CloudWatch instalados em uma ou mais instâncias do EC2.
2. Em seguida, um administrador cria um filtro personalizado do CloudWatch no grupo de logs O filtro pesquisa os dados de log para mensagens de erro HTTP 404 página não encontrada no log.
3. Cada correspondência incrementa uma métrica personalizada do CloudWatch para a métrica 404Count.
4. Em seguida, o administrador usou essa métrica para acionar um alarme do CloudWatch quando a métrica 404Count exceder um valor especificado (que é exibido como x).
5. Quando o alarme do CloudWatch é acionado, uma notificação é enviada. Nesse caso, a notificação é encaminhada para a equipe de suporte de TI.

### Formatos de log típicos

**Exemplo:** Logs httpd do Apache configurados usando uma string de substituição no httpd.conf

````Formato de registro "%h %l %u %t \“%r\" %>s %b" comum````

**Resultado:** Uma string delimitada por espaço contém informações sobre cada solicitação HTTP(S)

````127.0.0.1 - marcia [10/Oct/2000:13:55:36 -0700] "GET /apache_pb.gif HTTP/1.0" 200 2326````

Os logs de aplicativos normalmente geram dados em um formato padronizado. Para conseguir analisar os dados relevantes dos arquivos de log com êxito, você precisa entender o formato do log.
Neste exemplo, cada registro de log contém o seguinte: 
- %h é o endereço IP da máquina host que fez uma solicitação HTTP.
- %l é a identidade da máquina do cliente. Essas informações geralmente não estão disponíveis, o que é indicado pela saída do caractere de traço (-) no resultado do exemplo.
- %u é o ID de usuário da pessoa que solicita as informações. Se o site não exigir um login, essas informações não serão conhecidas. No exemplo, uma usuária chamada marcia fez a solicitação.
- %t é o horário em que a solicitação foi recebida.
- %r é a linha de solicitação. Isso inclui o tipo de solicitação HTTP que foi recebida, como GET. Além de qual recurso foi solicitado, como uma página HTML, um arquivo gráfico ou um arquivo de folha de estilo.
- %s é o código de status HTTP com o qual o servidor Web respondeu. No resultado de exemplo, o código de status é 200, o que indica sucesso, mas você pode encontrar outros códigos, como códigos de erro 404 (recurso não encontrado).

### Padrões de filtro do Amazon CloudWatch
#### Padrões de filtro
**Diferencia maiúsculas de minúsculas** 
- Vários termos permitidos em um padrão de filtro de métricas (no entanto, todos os termos devem aparecer no evento de log para serem uma correspondência)
- Exemplo: Crie uma métrica para todos os resultados com a string html em qualquer lugar da solicitação e qualquer erro HTTP 400-series (cliente)

  ```[ip, user, username, timestamp, request = *html*, status_code = 4*, bytes]```
