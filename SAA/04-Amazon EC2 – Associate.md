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

# Amazon EC2 – Instance Storage
## O que é um volume EBS?
- Um volume EBS (Elastic Block Store) é uma unidade de rede que você pode anexar às suas instâncias enquanto elas são executadas
- Ele permite que suas instâncias persistam dados, mesmo após seu término
- Elas só podem ser montadas em uma instância por vez (no nível CCP)
- Elas são vinculadas a uma zona de disponibilidade específica
- Analogia: pense nelas como um "pendrive de rede"
- Nível gratuito: 30 GB de armazenamento EBS gratuito do tipo General Purpose (SSD) ou Magnetic por mês


## Volume EBS
- É uma unidade de rede (ou seja, não uma unidade física)
  - Ela usa a rede para comunicar a instância, o que significa que pode haver um pouco de latência
  - Ela pode ser desanexada de uma instância EC2 e anexada a outra rapidamente

- Ela está bloqueada em uma Zona de Disponibilidade (AZ)
  - Um Volume EBS em us-east-1a não pode ser anexado a us-east-1b
  - Para mover um volume, primeiro você precisa fazer um snapshot dele

- Tenha uma capacidade provisionada (tamanho em GBs e IOPS)
  - Você é cobrado por toda a capacidade provisionada
  - Você pode aumentar a capacidade da unidade ao longo do tempo

 
## EBS – Delete on Termination attribute
- Controla o comportamento do EBS quando uma instância EC2 é encerrada
  - Por padrão, o volume raiz do EBS é excluído (atributo habilitado)
  - Por padrão, qualquer outro volume EBS anexado não é excluído (atributo desabilitado)
- Isso pode ser controlado pelo console da AWS/AWS CLI
- **Caso de uso:**
  - preservar o volume raiz quando a instância é encerrada


## EBS Snapshots
- Faça um backup (snapshot) do seu volume EBS em um ponto no tempo
- Não é necessário desanexar o volume para fazer o snapshot, mas é recomendado
- Pode copiar snapshots em AZ ou região

![image](https://github.com/user-attachments/assets/2c4cd069-21b6-4538-9b3c-409831b97b3e)


## Visão geral do AMI
- AMI = Amazon Machine Image

- AMI são uma personalização de uma instância EC2
  - Você adiciona seu próprio software, configuração, sistema operacional, monitoramento...
  - Tempo de inicialização/configuração mais rápido porque todo o seu software é pré-empacotado

- AMI são criados para uma região específica (e podem ser copiados entre regiões)

- Você pode iniciar instâncias EC2 de:
  - Um AMI público: fornecido pela AWS
  - Seu próprio AMI: você os cria e os mantém você mesmo
  - Um AMI do AWS Marketplace: um AMI que outra pessoa criou (e potencialmente vende)


## Processo AMI (de uma instância EC2)
- Inicie uma instância EC2 e personalize-a
- Pare a instância (para integridade de dados)
- Crie uma AMI – isso também criará snapshots do EBS
- Inicie instâncias de outras AMIs

![image](https://github.com/user-attachments/assets/2d9f11cb-8a59-4d5e-94af-9f8da7f4b18f)


## EC2 Instance Store
- Volumes EBS são unidades de rede com desempenho bom, mas "limitado"
- Se você precisa de um disco de hardware de alto desempenho, use EC2 Instance Store
- Melhor desempenho de E/S
- EC2 Instance Store perde seu armazenamento se for interrompido (efêmero)
- Bom para buffer / cache / dados temporários / conteúdo temporário
- Risco de perda de dados se o hardware falhar
- Backups e replicação são de sua responsabilidade


## Tipos de volume EBS
- Os volumes EBS vêm em 6 tipos
  - **gp2 / gp3 (SSD):** volume SSD de uso geral que equilibra preço e desempenho para uma ampla variedade de cargas de trabalho
  - **io1 / io2 Block Express (SSD):** volume SSD de mais alto desempenho para cargas de trabalho de missão crítica de baixa latência ou alto rendimento
  - **st1 (HDD):** volume HDD de baixo custo projetado para cargas de trabalho de alto rendimento acessadas com frequência
  - **sc1 (HDD):** volume HDD de menor custo projetado para cargas de trabalho acessadas com menos frequência

- Os volumes EBS são caracterizados em Tamanho | Rendimento | IOPS (operações de E/S por segundo)
- Em caso de dúvida, consulte sempre a documentação da AWS.
- Somente gp2/gp3 e io1/io2 Block Express podem ser usados ​​como volumes de inicialização


## Tipos de volume EBS Casos de uso
### SSD de uso geral
- Armazenamento econômico, baixa latência
- Volumes de inicialização do sistema, desktops virtuais, ambientes de desenvolvimento e teste
- 1 GiB - 16 TiB
  
- **gp3:**
  - Linha de base de 3.000 IOPS e taxa de transferência de 125 MiB/s
  - Pode aumentar IOPS até 16.000 e taxa de transferência até 1000 MiB/s independentemente

- **gp2:**
  - Pequenos volumes gp2 podem estourar IOPS para 3.000
  - O tamanho do volume e IOPS são vinculados, o IOPS máximo é 16.000
  - 3 IOPS por GB, significa que em 5.334 GB estamos no IOPS máximo


### SSD Provisioned IOPS (PIOPS)
- Aplicativos empresariais críticos com desempenho de IOPS sustentado
- Ou aplicativos que precisam de mais de 16.000 IOPS
- Ótimo para cargas de trabalho de bancos de dados (sensíveis ao desempenho e consistência do armazenamento)
- **io1 (4 GiB - 16 TiB):**
  - PIOPS máx.: 64.000 para instâncias Nitro EC2 e 32.000 para outras
  - Pode aumentar PIOPS independentemente do tamanho do armazenamento
- **io2 Block Express (4 GiB - 64 TiB):**
  - Latência abaixo de milissegundos
  - PIOPS máx.: 256.000 com uma proporção de IOPS:GiB de 1.000:1
- Suporta EBS Multi-attach


### Unidades de disco rígido (HDD) 
- Não pode ser um volume de inicialização
- 125 GiB a 16 TiB 
- **HDD otimizado para throughput (st1)**
  - Big Data, data warehouses, processamento de log 
  - throughput máximo de 500 MiB/s – IOPS máximo de 500

- **HDD frio (sc1):**
  - Para dados acessados ​​com pouca frequência 
  - Cenários em que o menor custo é importante 
- throughput máximo de 250 MiB/s – IOPS máximo de 250


## EBS Multi-Attach – família io1/io2
- Anexar o mesmo volume EBS a várias instâncias EC2 na mesma AZ
- Cada instância tem permissões totais de leitura e gravação para o volume de alto desempenho
- Caso de uso:
  - Obter maior disponibilidade de aplicativos em aplicativos Linux em cluster (ex: Teradata)
  - Os aplicativos devem gerenciar operações de gravação simultâneas
- Até 16 instâncias EC2 por vez
- Deve usar um sistema de arquivos que tenha reconhecimento de cluster (não XFS, EXT4, etc…)

![image](https://github.com/user-attachments/assets/654e3a2b-95de-4f6f-8374-008af4cef045)


## Criptografia EBS
- Ao criar um volume EBS criptografado, você obtém o seguinte:
  - Dados em repouso são criptografados dentro do volume
  - Todos os dados em movimento entre a instância e o volume são criptografados
  - Todos os snapshots são criptografados
  - Todos os volumes criados a partir do snapshot
- Criptografia e descriptografia são manipuladas de forma transparente (você não tem nada a fazer)
- A criptografia tem um impacto mínimo na latência
- A Criptografia EBS aproveita chaves do KMS (AES-256)
- Copiar um snapshot não criptografado permite criptografia
- Snapshots de volumes criptografados são criptografados


## Criptografia: criptografar um volume EBS não criptografado
- Criar um instantâneo EBS do volume
- Criptografar o instantâneo EBS (usando cópia)
- Criar um novo volume ebs a partir do instantâneo (o volume também será criptografado)
- Agora você pode anexar o volume criptografado à instância original

## Amazon EFS – Elastic File System
- NFS gerenciado (network file system) que pode ser montado em muitos EC2
- EFS funciona com instâncias EC2 em multi-AZ
- Altamente disponível, escalável, caro (3x gp2), pagamento por uso

![image](https://github.com/user-attachments/assets/9afbc963-6636-4b7f-899b-42bc44b35df6)


## Amazon EFS – Elastic File System
- Casos de uso: gerenciamento de conteúdo, serviço web, compartilhamento de dados, Wordpress
- Usa protocolo NFSv4.1
- Usa grupo de segurança para controlar o acesso ao EFS
- Compatível com AMI baseado em Linux (não Windows)
- Criptografia em repouso usando KMS
- Sistema de arquivos POSIX (~Linux) que tem uma API de arquivo padrão
- O sistema de arquivos é dimensionado automaticamente, pagamento por uso, sem planejamento de capacidade!


## EFS – Classes de desempenho e armazenamento
- Escala EFS
  - Milhares de clientes NFS simultâneos, taxa de transferência de 10 GB+/s
  - Cresça para um sistema de arquivos de rede em escala de petabytes, automaticamente

- Modo de desempenho (definido no momento da criação do EFS)
  - Uso geral (padrão) – casos de uso sensíveis à latência (servidor web, CMS, etc…)
  - E/S máxima – latência mais alta, taxa de transferência, altamente paralelo (big data, processamento de mídia)

- Modo de taxa de transferência
  - Bursting – 1 TB = 50 MiB/s + burst de até 100 MiB/s
  - Provisionado – defina sua taxa de transferência independentemente do tamanho do armazenamento, ex: 1 GiB/s para armazenamento de 1 TB
  - Elástico – dimensiona automaticamente a taxa de transferência para cima ou para baixo com base em suas cargas de trabalho
    - Até 3 GiB/s para leituras e 1 GiB/s para gravações
    - Usado para cargas de trabalho imprevisíveis


## EFS – Classes de armazenamento
- Camadas de armazenamento (recurso de gerenciamento de ciclo de vida – mover arquivo após N dias)
  - Padrão: para arquivos acessados ​​com frequência
  - Acesso pouco frequente (EFS-IA): custo para recuperar arquivos, menor preço para armazenar.
  - Arquivo: dados raramente acessados ​​(poucas vezes por ano), 50% mais barato
  - Implementar políticas de ciclo de vida para mover arquivos entre camadas de armazenamento
    
- Disponibilidade e durabilidade
  - Padrão: Multi-AZ, ótimo para prod
  - Uma zona: Uma AZ, ótimo para dev, backup habilitado por padrão, compatível com IA (EFS One Zone-IA)

- Mais de 90% em economia de custos

![image](https://github.com/user-attachments/assets/f4d99662-f1ce-4542-b045-58c20b349434)


## EBS vs EFS
### Elastic Block Storage
- Volumes EBS…
  - uma instância (exceto multi-attach io1/io2)
  - são bloqueados no nível da Zona de Disponibilidade (AZ)
  - gp2: IO aumenta se o tamanho do disco aumentar
  - gp3 e io1: podem aumentar IO independentemente

- Para migrar um volume EBS através de AZ
  - Tirar um snapshot
  - Restaurar o snapshot para outro AZ
  - Os backups EBS usam IO e você não deve executá-los enquanto seu aplicativo estiver lidando com muito tráfego
  
- Os volumes EBS raiz de instâncias são encerrados por padrão se a instância EC2 for encerrada. (você pode desabilitar isso)

![image](https://github.com/user-attachments/assets/45fef556-97d3-414b-ab8b-fa6b86b6e40d)


### Elastic File System
- Montagem de centenas de instâncias em AZ
- EFS compartilha arquivos de site (WordPress)
- Somente para instâncias Linux (POSIX)
- EFS tem um ponto de preço mais alto que EBS
- Pode aproveitar os níveis de armazenamento para economia de custos
- Lembre-se: EFS vs EBS vs Instance Store

![image](https://github.com/user-attachments/assets/9b9c0cc5-af9e-4133-ba44-9bde8dd348c7)
