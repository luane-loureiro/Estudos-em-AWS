# Alta disponibilidade e escalabilidade

## Escalabilidade e Alta Disponibilidade
- Escalabilidade significa que um aplicativo/sistema pode lidar com cargas maiores por adaptação.
- Existem dois tipos de escalabilidade:
  - Escalabilidade Vertical
  - Escalabilidade Horizontal (= elasticidade)
  
- Escalabilidade está vinculada, mas é diferente de Alta Disponibilidade
- Vamos nos aprofundar na distinção, usando um call center como exemplo


## Escalabilidade Vertical
- Escalabilidade vertical significa aumentar o tamanho da instância
- Por exemplo, seu aplicativo é executado em um t2.micro, Escalar esse aplicativo verticalmente significa executá-lo em um t2.large
- Escalabilidade vertical é muito comum para sistemas não distribuídos, como um banco de dados.
- RDS, ElastiCache são serviços que podem escalar verticalmente.
- Geralmente, há um limite para o quanto você pode escalar verticalmente (limite de hardware)

  ![image](https://github.com/user-attachments/assets/4c39f8ee-a442-472e-b50f-3cfe1547b7ef)


## Escalabilidade horizontal 
- Escalabilidade horizontal significa aumentar o número de instâncias / sistemas para seu aplicativo
- Escalabilidade horizontal implica sistemas distribuídos.
- Isso é muito comum para aplicativos da web / aplicativos modernos
- É fácil escalar horizontalmente graças às ofertas de nuvem, como Amazon EC2

![image](https://github.com/user-attachments/assets/ad0b1071-a084-421f-b574-11c5e9c55e05)


## Alta Disponibilidade
- Alta Disponibilidade geralmente anda de mãos dadas com escalonamento horizontal
- Alta disponibilidade significa executar seu aplicativo/sistema em pelo menos 2 datacenters (== Zonas de Disponibilidade)
- O objetivo da alta disponibilidade é sobreviver a uma perda de datacenter
- A alta disponibilidade pode ser passiva (para RDS Multi AZ, por exemplo)
- A alta disponibilidade pode ser ativa (para escalonamento horizontal)

![image](https://github.com/user-attachments/assets/83f87eb7-8569-46a9-bd5a-c627e44ae99a)


## Alta disponibilidade e escalabilidade para EC2
- Escala vertical: Aumentar o tamanho da instância (= escalar para cima/para baixo)
  - De: t2.nano - 0,5 G de RAM, 1 vCPU
  - Para: u-12tb1.metal – 12,3 TB de RAM, 448 vCPUs
    
- Escala horizontal: Aumentar o número de instâncias (= escalar para fora/para dentro)
  - Grupo de escala automática
  - Balanceador de carga
    
- Alta disponibilidade: Executar instâncias para o mesmo aplicativo em várias AZ
  - Grupo de escala automática várias AZ
  - Balanceador de carga várias AZ
 

## Load Balance - O que é balanceamento de carga?
- Os balanceamentos de carga são servidores que encaminham o tráfego para vários
servidores (por exemplo, instâncias EC2)

![image](https://github.com/user-attachments/assets/b5754a93-076a-4d8c-a936-e343f1980599)


## Por que usar um balanceador de carga? 
- Distribua a carga em várias instâncias downstream 
- Exponha um único ponto de acesso (DNS) ao seu aplicativo 
- Lide perfeitamente com falhas de instâncias downstream 
- Faça verificações regulares de integridade em suas instâncias 
- Forneça terminação SSL (HTTPS) para seus sites
- Aplique a aderência com cookies 
- Alta disponibilidade em todas as zonas 
- Separe o tráfego público do tráfego privado


## Por que usar um Elastic Load Balancer?
- Um Elastic Load Balancer é um balanceador de carga gerenciado
  - A AWS garante que ele estará funcionando
  - A AWS cuida de atualizações, manutenção, alta disponibilidade
  - A AWS fornece apenas alguns botões de configuração
    
- Custa menos configurar seu próprio balanceador de carga, mas será muito mais esforço da sua parte
  
- Ele é integrado com muitas ofertas/serviços da AWS
  - EC2, EC2 Auto Scaling Groups, Amazon ECS
  - AWS Certificate Manager (ACM), CloudWatch
  - Route 53, AWS WAF, AWS Global Accelerator
 

## Health Checks - Verificações de saúde
- As Health Checks são cruciais para balanceadores de carga
- Elas permitem que o balanceador de carga saiba se as instâncias para as quais ele encaminha o tráfego estão disponíveis para responder às solicitações
- A Health Checks é feita em uma porta e uma rota (/health é comum)
- Se a resposta não for 200 (OK), a instância não está íntegra

![image](https://github.com/user-attachments/assets/4a41e691-7c83-4d56-afc0-52500187301f)


## Tipos de balanceador de carga na AWS
- A AWS tem 4 tipos de balanceadores de carga gerenciados:\
  - Balanceador de carga clássico (v1 - geração antiga) – 2009 – CLB
    - HTTP, HTTPS, TCP, SSL (TCP seguro)
      
  - Balanceador de carga de aplicativo (v2 - nova geração) – 2016 – ALB
    - HTTP, HTTPS, WebSocket
      
  - Balanceador de carga de rede (v2 - nova geração) – 2017 – NLB
    - TCP, TLS (TCP seguro), UDP
      
  - Balanceador de carga de gateway – 2020 – GWLB
    - Opera na camada 3 (camada de rede) – Protocolo IP
      
- No geral, é recomendável usar os balanceadores de carga de geração mais recente, pois eles fornecem mais recursos
- Alguns balanceadores de carga podem ser configurados como ELBs internos (privados) ou externos (públicos)


## Application Load Balancer (v2)
- Application load balancers é Layer 7 (HTTP)
- Balanceamento de carga para vários aplicativos HTTP em máquinas (grupos de destino)
- Balanceamento de carga para vários aplicativos na mesma máquina (ex: contêineres)
- Suporte para HTTP/2 e WebSocket
- Suporte a redirecionamentos (de HTTP para HTTPS, por exemplo)
- Tabelas de roteamento para diferentes grupos-alvo:
  - Roteamento com base no caminho na URL (exemplo.com/usuários e exemplo.com/postagens)
  - Roteamento com base no nome do host na URL (um.exemplo.com e outro.exemplo.com)
  - Roteamento com base na sequência de consulta, cabeçalhos (exemplo.com/usuários?id=123&order=false)
- ALB são uma ótima opção para microsserviços e aplicativos baseados em contêineres (exemplo: Docker e Amazon ECS)
- Tem um recurso de mapeamento de porta para redirecionar para uma porta dinâmica no ECS
- Em comparação, precisaríamos de vários Classic Load Balancers por aplicativo


## Application Load Balancer (v2) - Tráfego baseado em HTTP

![image](https://github.com/user-attachments/assets/2759992b-f59e-4ce5-a9a5-a80531ea7deb)


## Application Load Balancer (v2) - Grupos de destino
- Instâncias EC2 (podem ser gerenciadas por um Auto Scaling Group) – HTTP
- Tarefas ECS (gerenciadas pelo próprio ECS) – HTTP
- Funções Lambda – a solicitação HTTP é traduzida em um evento JSON
- Endereços IP – devem ser IPs privados
- O ALB pode rotear para vários grupos de destino
- As verificações de integridade são no nível do grupo de destino


## Application Load Balancer (v2) - Query Strings/Parameters Routing

![Capturar](https://github.com/user-attachments/assets/db3c9bd2-5d8a-4977-bc3d-3d1ecc384f35)


## Application Load Balancer (v2)
> [!TIP]
> - Nome do host corrigido (XXX.region.elb.amazonaws.com)
> - Os servidores de aplicativos não veem o IP do cliente diretamente
>   - O IP verdadeiro do cliente é inserido no cabeçalho X-Forwarded-For
>   - Também podemos obter a porta (X-Forwarded-Port) e o proto (X-Forwarded-Proto)

![image](https://github.com/user-attachments/assets/b1caa46d-14f3-4049-bd35-b2e0814ce55d)




