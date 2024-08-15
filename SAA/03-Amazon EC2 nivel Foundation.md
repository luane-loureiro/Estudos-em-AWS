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
