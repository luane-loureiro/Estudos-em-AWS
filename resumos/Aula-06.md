# Aula 6 - Visão geral da infraestrutura AWS
## Infraestrutura global da AWS
- A Infraestrutura global da AWS foi projetada e construída para oferecer um ambiente de computação em nuvem flexível, confiável, dimensionável e seguro com desempenho de rede global de alta qualidade
- A infraestrutura global da AWS pode ser dividida em três elementos: Regiões, Zonas de Disponibilidade e pontos de presença.
- 
## Elementos da infraestrutura global da AWS 
#### Aplicativos
- desktops virtuais
- Colaboração e Compartilhamento

#### Serviços de Plataforma
- Banco de Dados
- Análise
- Serviços de aplicativos
- Implementação e Gerencianto
- Serviços Móveis
  
#### serviços básicos
- Computação (Virtual, auto scaling e balanceamento de carga)
- Redes
- Armazenamento (Objeto, bloco e arquivo)

#### Infra esturtura
- Regiões
- Zona de Disponibilidade
- Pontos de presença

## Data centers da AWS
- são a base da infraestrutura da AWS.
- é um local onde os dados físicos reais residem e o processamento de dados ocorre.
- são construídos em clusters em várias Regiões globais.
- Um único data center normalmente abriga de 50.000 a 80.000 servidores físicos.
- Todos os data centers ficam on-line
- Nenhum data center fica inativo (ou não está sendo usado)

## Zonas de Disponibilidade da AWS

  ![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/3774028d-ac06-4505-91ef-29f71f5f3008)

- Cada Zona de Disponibilidade é:
   - Composta de um ou mais data centers
   - Projetada para isolamento de falhas
   - Interconectada com outras Zonas de Disponibilidade por meio de links privados de alta velocidade




- são fisicamente separadas em uma Região metropolitana típica. 
- estão localizadas em planícies de menor risco de inundação com categorização específica de zona de inundação que varia de acordo com a Região. 
- Tem fontes de alimentação ininterrupta distintas e instalações locais de geração de energia como backup, elas geralmente são alimentadas por grades diferentes de concessionárias independentes para reduzir ainda mais os pontos únicos de falha. 

## Regiões AWS

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/93e71baf-4fc0-4917-b5ab-64880e201b1c)

- É uma área geográfica
- Cada Região é composta de duas ou mais Zonas de Disponibilidade
- A AWS atualmte tem 32 reões ao redor do mundo
- Você habilita e controla a replicação de dados entre Regiões
- A comunicação entre as Regiões usa a estrutura de conexões de rede da infraestrutura da AWS


## Infraestrutura global da AWS
- Em Outubro de 2023, a infraestrutura global da AWS incluía 32 Regiões e 102 Zonas de Disponibilidade. 
- A AWS expande constantemente sua infraestrutura global adicionando mais Regiões.
- Ao expandir a infraestrutura, a AWS ajuda os clientes a obter menor latência e taxa de transferência mais alta, bem como a garantir que seus dados residam apenas nos locais desejados.

## Seleção de uma Região
Ao selecionar uma Região, considere aquela que oferece os serviços de que você precisa e o local em que ela está localizada. Isso pode ajudar você a otimizar a latência e, ao mesmo tempo, reduzir custos. 

Determine a Região certa para seus serviços, aplicativos e dados com base nesses fatores.

#### 1) Governaça de Dados
  As leis locais podem exigir que determinadas informações sejam mantidas dentro de limites geográficos.

#### 2) Proximidade som os clientes (latencia)
  É desejável executar os aplicativos e armazenar os dados em uma Região que esteja mais próxima possível do usuário e dos sistemas que os acessarão. Isso ajudará você a reduzir a latência.

#### 3) Serviços dosponíveis
  nem todos os serviços estão disponíveis em todas as Regiões.

#### 4) Custos (variam por região)
   há alguma variação no custo da execução de serviços, que pode depender da Região escolhida.
