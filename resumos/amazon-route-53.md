# amazon route 53

## O Amazon Route 53 é um serviço da Web do Domain Name System (DNS) escalável
- Registra ou transfere um nome de domínio
- Resolve nomes de domínio para endereços IP
- Roteia solicitações com base na latência, verificações de integridade, pesos ou outros fatores
- Distribui tráfego entre regiões – Pode oferecer suporte à alta disponibilidade e menor latência

Associado nomes de DNS ao elástic load balancing
- Nome DNS padrão do ELB.
  
      - A AWS atribui um nome de host ao seu load balancer que é solucionado em um conjunto de endereços IP

- Associar o seu próprio nome DNS

        - Atribuir seu próprio nome de host por meio de um conjunto de registros de recursos de alias
        - Criarum registro CNAME que aponte para o seu load balancer


## Políticas de roteamento do Amazon Route 53
O Amazon Route 53 oferece suporte às sete políticas de roteamento a seguir: 
#### 1. Política de roteamento simples
use para um único recurso que execute uma determinada função para o seu domínio, por exemplo, um servidor Web que oferece conteúdo para o site example.com .

#### 2. Política de roteamento ponderado
use para rotear o tráfego para vários recursos nas proporções que você especificar.

#### 3. Política de roteamento de latência 
use quando você tiver recursos em várias regiões da AWS e quiser rotear o tráfego para a região que fornece a latência mais baixa.
   
#### 4. Política de roteamento de failover 
use quando quiser configurar o failover ativo/passivo.

#### 5. Política de roteamento de Elastic Load Balancing geolocalização (localização da consulta DNS)
use quando quiser rotear o tráfego com base na localização dos seus usuários.

#### 6. Política de roteamento de geoproximidade (fluxo de tráfego para a região da AWS ou latitude e longitude)
use quando desejar rotear o tráfego com base na localização dos seus recursos e, opcionalmente, alternar o tráfego de recursos em uma localização para recursos em outra.
   
#### 7. Política de roteamento de resposta com valores múltiplos
use quando quiser que o Route53 responda a consultas DNS com até oito registros íntegros selecionados aleatoriamente.
