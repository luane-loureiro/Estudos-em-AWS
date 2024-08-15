# Amazon EC2 – Associate
## IP privado vs. IP público (IPv4)
- A rede tem dois tipos de IPs. IPv4 e IPv6:
  - IPv4: 1.160.10.240
  - IPv6: 3ffe:1900:4545:3:200:f8ff:fe21:67cf
<br>

- Neste curso, usaremos apenas IPv4.
- IPv4 ainda é o formato mais comum usado online.
- IPv6 é mais novo e resolve problemas para a Internet das Coisas (IoT).
- IPv4 permite 3,7 bilhões de endereços diferentes no espaço público
- IPv4: [0-255].[0-255].[0-255].[0-255].


## IP privado vs. IP público (IPv4) - Diferenças fundamentais
- **IP público:**
  - IP público significa que a máquina pode ser identificada na internet (WWW)
  - Deve ser único em toda a web (duas máquinas não podem ter o mesmo IP público).
  - Pode ser geolocalizado facilmente
<br>

- **IP privado:**
  - IP privado significa que a máquina só pode ser identificada em uma rede privada
  - O IP deve ser único na rede privada
  - MAS duas redes privadas diferentes (duas empresas) podem ter os mesmos IPs.
  - As máquinas se conectam à WWW usando um NAT + gateway de internet (um proxy)
  - Apenas um intervalo especificado de IPs pode ser usado como IP privado


## IPs elásticos
- Quando você para e inicia uma instância EC2, ela pode alterar seu IP
público.
- Se você precisa ter um IP público fixo para sua instância, você precisa de um
IP elástico
- Um IP elástico é um IP IPv4 público que você possui, desde que não o exclua
- Você pode anexá-lo a uma instância por vez
- Com um endereço IP elástico, você pode mascarar a falha de uma instância ou software
remapeando rapidamente o endereço para outra instância em sua conta.
- Você pode ter apenas 5 IP elásticos em sua conta (você pode pedir à AWS para aumentar
isso).
- No geral, tente evitar usar IP elástico:
  - Eles geralmente refletem decisões arquitetônicas ruins
  - Em vez disso, use um IP público aleatório e registre um nome DNS para ele
  - Ou, como veremos mais tarde, use um balanceador de carga e não use um IP público


## IP privado vs. IP público (IPv4) - Hand on
- Por padrão, sua máquina EC2 vem com:
  - Um IP privado para a rede interna da AWS
  - Um IP público, para a WWW.<br>
  
- Quando estamos fazendo SSH em nossas máquinas EC2:
  - Não podemos usar um IP privado, porque não estamos na mesma rede
  - Só podemos usar o IP público.<br>
  
- Se sua máquina for parada e depois iniciada,
- IP público pode mudar


## Grupos de posicionamento - Placement Groups
- Às vezes, você quer controlar a estratégia de posicionamento da instância EC2
- Essa estratégia pode ser definida usando grupos de posicionamento
- Ao criar um grupo de posicionamento, você especifica uma das seguintes estratégias para o grupo:
  - **Cluster** — agrupa instâncias em um grupo de baixa latência em uma única Zona de disponibilidade
  - **Spread** — espalha instâncias pelo hardware subjacente (máximo de 7 instâncias por grupo por AZ)
  - **Partition** — espalha instâncias por muitas partições diferentes (que dependem de diferentes conjuntos de racks) dentro de uma AZ. Escala para centenas de instâncias EC2 por grupo (Hadoop, Cassandra, Kafka)


### Grupos de posicionamento - Cluster
- **Prós:**
  - Ótima rede (largura de banda de 10 Gbps entre instâncias com Enhanced Networking habilitado - recomendado)
- **Contras:**
  - Se o AZ falhar, todas as instâncias falharão ao mesmo tempo
- **Caso de uso:**
  - Tarefa de Big Data que precisa ser concluída rapidamente
  - Aplicativo que precisa de latência extremamente baixa e alta taxa de transferência de rede
![image](https://github.com/user-attachments/assets/bd2aaa4c-5398-411c-8f06-9442bf801c72)


### Grupos de posicionamento - Spread (Distribuição)
- **Prós:**
  - Pode abranger Zonas de disponibilidade (AZ)
  - Risco reduzido é falha simultânea
  - Instâncias EC2 estão em hardware físico diferente
- **Contras:**
  - Limitado a 7 instâncias por AZ por grupo de posicionamento
- **Caso de uso:**
  - Aplicativo que precisa maximizar alta disponibilidade
  - Aplicativos críticos onde cada instância deve ser isolada de falhas uma da outra
 
![Capturar](https://github.com/user-attachments/assets/34176721-40ba-4166-84f7-77f7ad0bba33)


### Grupos de posicionamentos Partição
- Até 7 partições por AZ
- Pode abranger várias AZs na mesma região
- Até 100s de instâncias EC2
- As instâncias em uma partição não compartilham racks com as instâncias nas outras partições
- Uma falha de partição pode afetar muitos EC2, mas não afetará outras partições
- As instâncias EC2 têm acesso às informações da partição como metadados
- Casos de uso: HDFS, HBase, Cassandra, Kafka


## Elastic Network Interfaces (ENI)
- Componente lógico em uma VPC que representa uma placa de rede virtual
- A ENI pode ter os seguintes atributos:
  - IPv4 privado primário, um ou mais IPv4 secundários
  - Um IP elástico (IPv4) por IPv4 privado
  - Um IPv4 público
  - Um ou mais grupos de segurança
  - Um endereço MAC
- Você pode criar ENI de forma independente e anexá-los on the fly (movê-los) em instâncias EC2 para failover
- Vinculado a uma zona de disponibilidade (AZ) específica

![image](https://github.com/user-attachments/assets/6a357080-c6df-4a3c-8d0d-1d1cdc5ee15d)


## EC2 Hibernate
- Sabemos que podemos parar, encerrar instâncias
  - Parar – os dados no disco (EBS) são mantidos intactos na próxima inicialização
  - Terminar – quaisquer volumes EBS (raiz) também configurados para serem destruídos são perdidos
  - 
- Na inicialização, acontece o seguinte:
  - Primeira inicialização: o sistema operacional inicializa e o script de dados do usuário do EC2 é executado
  - Iniciações seguintes: o sistema operacional inicializa
- Então seu aplicativo inicia, os caches são aquecidos e isso pode levar tempo!
- **Introduçao ao EC2 Hibernate:**
  - O estado na memória (RAM) é preservado
  - A inicialização da instância é muito mais rápida! (o SO não é interrompido/reiniciado)
  - Nos bastidores: o estado da RAM é gravado em um arquivo no volume raiz do EBS
  - O volume raiz do EBS deve ser criptografado
- **Casos de uso:**
  - Processamento de longa duração
  - Salvando o estado da RAM
  - Serviços que levam tempo para inicializar

 
### EC2 Hibernate – o que devemos saber...
- **Famílias de instâncias suportadas** – C3, C4, C5, I3, M3, M4, R3, R4, T2, T3, …
- **Tamanho da RAM da instância** – deve ser menor que 150 GB.
- **Tamanho da instância** – não suportado para instâncias bare metal.
- **AMI** – Amazon Linux 2, Linux AMI, Ubuntu, RHEL, CentOS e Windows…
- **Volume raiz** – deve ser EBS, criptografado, não armazenamento de instância e grande
- **Disponível** - para instâncias sob demanda, reservadas e spot
- Uma instância NÃO pode ser hibernada por mais de 60 dias

