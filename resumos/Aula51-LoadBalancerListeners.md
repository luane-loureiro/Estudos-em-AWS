# Aula 51 - Balanceadores de Carga e Ouvintes do ELB (Amazon Load Balancer Listeners)

## Balanceadores de casgas de aplicação

### Balanceador de carga do ELB 
#### Recursos
- Alta disponibilidade (HA)
- Verificações de integridade Recursos de segurança
- Encerramento de Transport Layer Security (TLS)
- Balanceamento de carga das camadas 4 ou 7 Monitoramento operacional 


 ### Load balancer: Listeners
- Processo que define a porta e o protocolo nos quais o balanceador de carga escuta.
- Cada balanceador de carga precisa de pelo menos um ouvinte para aceitar o tráfego.
- Até 50 ouvintes podem estar em um balanceador de carga.
- As regras de roteamento são definidas nos ouvintes
- Um ouvinte é um processo que verifica se há uma solicitação de conexão de um cliente para uma instância usando o protocolo e a porta que você especificar.
- As regras do ouvinte que você definir também determinam como o tráfego de conexão de clientes é roteado pelo balanceador de carga para um ou mais destinos ou grupos de destino.
-  Cada regra consiste em uma prioridade, uma ou mais ações e uma ou mais condições. Quando as condições de uma regra são atendidas, suas ações são executadas.
-  Você deve definir uma regra padrão para cada ouvinte e, opcionalmente, pode definir regras adicionais.

### Load balancer: Grupos de destino
#### Grupo de destinos registrados que oferecem suporte a:
- Instâncias do Amazon Elastic Compute Cloud (Amazon EC2)
- Instâncias de contêiner do Amazon Elastic Container Service (Amazon ECS)
#### Um único destino pode ter vários registros de grupo de destino
