# Infra Estrutura Global da AWS
![image](https://github.com/user-attachments/assets/013febea-50f6-4e11-9a31-cff3bec96192)

- regiões
- Zonas disponibilidades
- AWS data center
- AWS Edge Location

## ambientes AWS
- Exemplos de Ambiente de serviços Globais
  - indentity Acess Management (IAM)
  - Route 53 (DNS Service)
  - CloudFront (Content Delivery NetWork)
  - WAF (Web Application Firewall)

- AWS Exemplo de Serviços de escopo de região
  - Amazon EC2 (infra estrutura as a service)
  - Elástic beanstalk (plataform as a service)
  - Lmabda (Function as a service)
  - Recognition (Softwaew as a service)
 
# AWS Identity and Acess Management (IAM) 
## IAM: User Group
- IAM = identity and acess Management, um serviço Global
- conta root criada por padrão, não deve ser usada ou compartilhada
- Os usuários são pessoas dentro da sua organização e podem ser agrupadas
- os grupos contem apenas usuários, nao podem conter outros grupos
- Os usuários não precisam pertencer a um grupo, e os usuários podem pertencer a vários grupos

![image](https://github.com/user-attachments/assets/d9ec3b31-526d-4c19-94a4-4d36bac8f29e)

<br>

## IAM - politica de senhas
- senhas fortes = maior segurança para sau conta.
- na aws você pode criar regas (policy) de uso de senhas
  - minimo de caracteres
  - tipos especificos de caracteres exigidos
    - incluir letras maiusculas
    - incluir letras minúsculas
    - númes
    - caracteres especiais
  - todos os usuarios do IAM devem trocar com regularidade suas senhas (password expiration)
  - todos os usuários podesm criar suas próprias senhas
  - não podem usar senhas repetidas
 
## MFA - multi factor Autenticator
- Os usuários tem acesso a sua conta e podem mudar configuraçoes ou apacar recursos na sua conta.
- você precisa proteger sua RootAccont e seus usuários IAM.
- MFA = password que vc criou + discpositivo de segurança
- Benefícios do MFA: se seu passowrd  for roubado ou hackeado, a sua acc não estara comprometida, pq ainda irão precisa do dispositivo de segurança

### Opções de dispositivos para MFA
- virtual MFA devices
    - google autenticator
    - Authy
- universal 2nd factor (u2f) security key
- haedwarw key fob MFA Device
- Hardware key fob MFA device for awsGovCloud (US)


## IAM - Funçôes para Serviços
- Alguns serviços da AWS precisarão executar algumas ações em seu nome
- para isso, atribuimos permições aos serviçõs da AWS com funções do IAM
- Funções comuns:
  - funções de instacias do EC2
  - Funções Lambda
  - Funções Cloud Formation
    
  ![image](https://github.com/user-attachments/assets/3dd49627-a637-4445-9d12-05fe3a58ea7d)


## IAM -  Diretrizes Prátoicas Recomendadas
- Não use a conta raiz, exeto para a configuração da conta da aws
- um usuário físico = um usuário da aws
- Atribuir usuários a grupos e atribuir permições a grupos
- criar uma política de senha forte
- usar um impor o uso de Mult Factor Authentication (MFA)
- Criar e usar fubnções para concender permições aos serviços da AWS
- Utilizar chaves de acesso para acessi Programático (CLI/SDK)
- Auditar permições de sua conta usando o relatório de credenciais do IAM e o IAM Access Advisor.
- Nunca Compartilhe usuários do IAM e chaves de acesso.


## IAM - Resumo 
- Usuários: Mapeando para um usuário físico, tem uma senha para o Console AWS
- Grupos: contém apenas usuários
- Políticas: Documentos JSON que descreve permições para usuários ou grupos
- Funções: para instâncias do EC2 ou serviço da AWS
- Segurança: MFA + Política de senha
- AWS CLI: Gerencie seus serviços da aws usando uma linha de comando
- AWS SDK:  gerencie seus serviços da AWS usando uma linguagem de programação
- Chaves de acesso: acesse a AWS usando a CLI ou SDK
- Auditoria: Relatórios de credenciais do IAM e IAM Acess Advisor.


# Amazon EC2 nivel Foundation

## EC2 Dimencionamento e opções de Configuração 
- sistema operacional: windows, Linux ou macOs
- Poder de Computação & nucleos (CPU)
- Quanta memória de acesso aleatório (RAM)
- Quanto espaço de Armazenamento
  - Network- atarchemet(EBS e EFS)
  - Hardware (EC2 Instance Store)
- Placa de rede: velocidade da Placa, endereço e Ip Público
- Regras de firewall: Security Group
- Bootstarp Script(Configurar na primeira inicialisação): EC2 user data


## EC2 User Data
- É possível inicializar nossas instâncias usando um script de dados do usuário EC2.
- inicialização significa iniciar comandos quando uma máquina inicia
- Esse script é executado apenas uma vez na primeira inicialização da instância
- Dados do usuário EC2 são usados ​​para automatizar tarefas de inicialização, como:
  - Instalação de atualizações
  - Instalação de software
  - Download de arquivos comuns da Internet
  - Qualquer coisa que você possa imaginar
- O script de dados do usuário EC2 é executado com o usuário root


## Tipos de instância EC2
### Visão geral
- Você pode usar diferentes tipos de instâncias EC2 que são otimizadas para diferentes casos de uso (https://aws.amazon.com/ec2/instance-types/)
- A AWS tem a seguinte convenção de nomenclatura:
  
> ### m5.2xlarge

- m: classe de instância
- 5: geração (a AWS as aprimora ao longo do tempo)
- 2xlarge: tamanho dentro da classe de instância


### Instancias de Propósito geral
- Ótimo para uma diversidade de cargas de trabalho, como servidores web ou repositórios de código
- Equilíbrio entre:
  	- Computação
  	-  Memória
  	-  Rede


### Instancias Otimizadas para computação
- Ótimo para tarefas intensivas de computação que exigem processadores
de alto desempenho:
  - Cargas de trabalho de processamento em lote
  -  Transcodificação de mídia
  -  Servidores web de alto desempenho
  -  Computação de alto desempenho (HPC)
  -  Modelagem científica e aprendizado de máquina
  -  Servidores de jogos dedicados


### Instancias com Memória otimizada
- Desempenho rápido para cargas de trabalho que processam grandes conjuntos de dados na memória
- Casos de uso:
  - Bancos de dados relacionais/não relacionais de alto desempenho
  -  Armazenamentos de cache de escala da Web distribuídos
  -   Bancos de dados na memória otimizados para BI (business intelligence)
  -    Aplicativos que executam processamento em tempo real de grandes dados não estruturados

 
### Instâncias com Armazenamento otimizado
- Ótimo para tarefas intensivas em armazenamento que exigem alto acesso sequencial de leitura e gravação a grandes conjuntos de dados no armazenamento local
- Casos de uso:
  - Sistemas de processamento de transações on-line de alta frequência (OLTP)
  - Bancos de dados relacionais e NoSQL
  - Cache para bancos de dados na memória (por exemplo, Redis)
  - Aplicativos de data warehousing
  - Sistemas de arquivos distribuídos


## Opções de Compra de instancias EC2
- **Instâncias sob demanda (On-Demand)** – carga de trabalho curta, preços previsíveis, pagamento por segundo
- **Reservadas** (1 e 3 anos)
  -  **Instâncias reservadas** – cargas de trabalho longas
  -  **Instâncias reservadas conversíveis**  – cargas de trabalho longas com instâncias flexíveis
- **Savings Plans** (1 e 3 anos) – compromisso com uma quantidade de uso, carga de trabalho longa
- **Instâncias spot** – cargas de trabalho curtas, baratas, podem perder instâncias (menos confiáveis)
- **Hosts dedicados** – reserve um servidor físico inteiro, controle o posicionamento da instância
- **Instâncias dedicadas** – nenhum outro cliente compartilhará seu hardware
- **Reservas de capacidade** – reserve capacidade em uma AZ específica por qualquer duração


### EC2 On Demand
- Pague pelo que você usa:
  - Linux ou Windows - cobrança por segundo, após o primeiro minuto
  - Todos os outros sistemas operacionais - cobrança por hora
- Tem o custo mais alto, mas sem pagamento inicial
- Nenhum compromisso de longo prazo
- Recomendado para cargas de trabalho de curto prazo e ininterruptas, onde você não pode prever como o aplicativo se comportará


### Instâncias reservadas do EC2
- Até 72% de desconto em comparação com o On-demand
- Você reserva atributos de instância específicos (tipo de instância, região, locação, sistema operacional)
- Período de reserva – 1 ano (+desconto) ou 3 anos (+++desconto)
- Opções de pagamento – Sem adiantamento (+), adiantamento parcial (++), adiantamento total (+++)
- Escopo da instância reservada – regional ou zonal (capacidade de reserva em uma AZ)
- Recomendado para aplicativos de uso em estado estável (pense em banco de dados)
- Você pode comprar e vender no Reserved Instance Marketplace
- Instância reservada conversível
  - Pode alterar o tipo de instância EC2, família de instâncias, sistema operacional, escopo e locação
  - Até 66% de desconto

 
### EC2 Savings Plans
- Obtenha um desconto com base no uso de longo prazo (até 72% - o mesmo que RIs)
- Comprometa-se com um certo tipo de uso (US$ 10/hora por 1 ou 3 anos)
- O uso além dos EC2 Savings Plans é cobrado pelo preço On-Demand
- Bloqueado para uma família de instâncias específica e região da AWS (por exemplo, M5 em us-east-1)
- Flexível em:
  - Tamanho da instância (por exemplo, m5.xlarge, m5.2xlarge)
  - SO (por exemplo, Linux, Windows)
  - Locação (Host, Dedicado, Padrão)

 
### Instâncias Spot do EC2
- Pode obter um desconto de até 90% em comparação com o On-demand
- Instâncias que você pode "perder" a qualquer momento se seu preço máximo for menor que o
- Preço spot atual
- As instâncias MAIS econômicas na AWS
- Úteis para cargas de trabalho que são resilientes a falhas
  - Trabalhos em lote
  - Análise de dados
  - Processamento de imagens
  - Quaisquer cargas de trabalho distribuídas
  - Cargas de trabalho com um horário de início e término flexível
- Não adequado para trabalhos ou bancos de dados críticos


### Hosts dedicados EC2
- Um servidor físico com capacidade de instância EC2 totalmente dedicada ao seu uso
- Permite que você atenda aos requisitos de conformidade e use suas licenças de software vinculadas ao servidor existentes (por-socket, por-core, por licensa de software de maquina vrtual)
- Opções de compra:
  - **Sob demanda** — pague por segundo para Host dedicado ativo
  - **Reservado** — 1 ou 3 anos (sem adiantamento, adiantamento parcial, adiantamento total)
- A opção mais cara
- Útil para software que tem modelo de licenciamento complicado (BYOL — Bring Your Own License)
- Ou para empresas que têm fortes necessidades regulatórias ou de conformidade


### EC2 Dedicated Instances 
- Instances run on hardware that’s dedicated to you
- May share hardware with other instances in same account
- No control over instance placement (can move hardware after Stop / Start)


### Reservas de Capacidade EC2
- Reserve capacidade de instâncias On-Demand em uma AZ específica para qualquer duração
- Você sempre tem acesso à capacidade EC2 quando precisar
- Sem compromisso de tempo (crie/cancele a qualquer momento), sem descontos de cobrança
- Combine com Instâncias Reservadas Regionais e Planos de Economia para se beneficiar de descontos de cobrança
- Você é cobrado pela taxa On-Demand, independentemente de executar instâncias ou não
- Adequado para cargas de trabalho ininterruptas de curto prazo que precisam estar em uma AZ específica


### Qual opção de compra é a certa para mim?
Vamos confaram a planejar uma viagem até um resort: 
- **Sob demanda:** chegando e ficando no resort quando quisermos, pagamos o preço integral
- **Reservado:** como planejar com antecedência e se planejamos ficar por um longo tempo, podemos obter um bom desconto.
- **Planos de economia:** pague uma certa quantia por hora por um determinado período e fique em qualquer tipo de quarto (por exemplo,
King, Suíte, Vista para o mar, …)
- **Instâncias pontuais:** o hotel permite que as pessoas façam lances pelos quartos vazios e o maior lance fica com os
quartos. Você pode ser expulso a qualquer momento se alguém estiver disposto a pagar mais.
- **Anfitriões dedicados:** reservamos um prédio inteiro do resort
- **Reservas de capacidade:** você reserva um quarto por um período com preço integral, mesmo que não fique nele


### Solicitações de instância spot do EC2
- Pode obter um desconto de até 90% em comparação com o On-demand
- Defina o preço spot máximo e obtenha a instância enquanto o preço spot atual < máximo
  - O preço spot por hora varia com base na oferta e capacidade
  - Se o preço spot atual > seu preço máximo, você pode optar por interromper ou encerrar sua instância com um período de carência de 2 minutos.
- Outra estratégia: ***Spot Block***
  - "bloqueie" a instância spot durante um período de tempo especificado (1 a 6 horas) sem interrupções
  - Em situações raras, a instância pode ser recuperada
- Usado para trabalhos em lote, análise de dados ou cargas de trabalho que são resilientes a falhas.
- Não é ótimo para trabalhos ou bancos de dados críticos


### Spot Fleets
- Spot Fleets = conjunto de Instâncias Spot + (opcional) Instâncias On-Demand
- A Spot Fleets tentará atingir a capacidade alvo com restrições de preço
  - Defina possíveis pools de lançamento: tipo de instância (m5.large), SO, Zona de Disponibilidade
  - Pode ter vários pools de lançamento, para que a frota possa escolher
  - A Spot Fleets para de lançar instâncias ao atingir a capacidade ou o custo máximo
- Estratégias para alocar Instâncias Spot:
  - **lowestPrice:** do pool com o menor preço (otimização de custo, carga de trabalho curta)
  - **diversified:** distribuído em todos os pools (ótimo para disponibilidade, cargas de trabalho longas)
  - **capacityOptimized:** pool com a capacidade ideal para o número de instâncias
  - **priceCapacityOptimized (recomendado):** pools com a maior capacidade disponível, então selecione pool com o menor preço (melhor escolha para a maioria das cargas de trabalho)
- As Spot Fleets nos permitem solicitar automaticamente Instâncias Spot com o menor preço


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



