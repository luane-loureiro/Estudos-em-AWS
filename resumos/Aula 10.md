# AWS Elastic Compute (EC2)
## Opções de computação no tempo de execução da AWS
A AWS oferece várias opções de computação para atender a diferentes necessidades. Ao considerar o serviço a ser usado para determinado tipo de carga de trabalho, é importante conhecer as opções de computação disponíveis.
As principais opções de computação em tempo de execução podem ser agrupadas em quatro categorias de modelos de computação em nuvem: máquinas virtuais (VMs), contêineres, plataforma como serviço e sem servidor.

## Amazon EC2
O Amazon EC2 oferece máquinas virtuais que podem hospedar os mesmos tipos de aplicativos que você executaria em um servidor tradicional local. 
Ele disponibiliza capacidade computacional segura e redimensionável na nuvem. 
As instâncias do EC2 podem oferecer suporte a uma variedade de cargas de trabalho.
Com o Amazon EC2, é possível iniciar qualquer número de instâncias de qualquer tamanho em qualquer Zona de Disponibilidade em qualquer lugar do mundo em minutos. 

- Exemplos de uso de instâncias do EC2:
    - Servidor de aplicativos
    - Servidor web
    - Servidor de banco de dados
    - Servidor de jogos
    - Servidor de e-mail
    - Servidor de mídia
    - Servidor de catálogo
    - Servidor de arquivos
    - Servidor de computação
    - Servidor de proxy

      
## Iniciar uma instância do EC2
Esta seção do módulo aborda nove decisões importantes a serem tomadas quando você cria uma instância do EC2 usando o Assistente para executar instância do Console de gerenciamento da AWS.
O Assistente para executar instância facilita a inicialização de uma instância. Por exemplo, se você optar por aceitar todas as configurações padrão, poderá ignorar a maioria das etapas fornecidas pelo assistente e iniciar uma instância do EC2 com apenas alguns cliques.
No entanto, para a maioria das implantações, você vai querer modificar as configurações padrão para que os servidores que você inicia sejam implantados para atender às suas necessidades específicas.

### Escolhas feitas usando o Assistente para executar instância:
1. AMI
2. Tipo de instância
3. Configurações de rede
4. Função do IAM
5. Dados do usuário
6. Opções de armazenamento
7. Tags
8. Security group
9. Par de chave

###  1) Selecionar uma AMI
- Imagem de máquina da Amazon (AMI)
    - É um modelo usado para criar uma instância do EC2 (que é uma máquina virtual, ou VM, executada na nuvem AWS)
    - Contém um sistema operacional Windows ou Linux
    - Muitas vezes, ele também tem software pré-instalado

- Opções de AMI:
     - Quick Start: AMIs do Linux e do Windows fornecidas pela AWS
     - Minhas AMIs: Todas as AMIs que você criou
     - AWS Marketplace: Modelos pré-configurados de terceiros 
     - AMIs da comunidade: AMIs compartilhadas por outras pessoas; use por sua conta e risco


#### Benefícios da AMI
- Repetibilidade
    - Usar uma AMI para iniciar instâncias repetidamente, com eficiência e precisão
 
- Capacidade de reutilização
    - Instâncias iniciadas na mesma AMI são configuradas de forma idêntica
 
- Capacidade de recuperação
    - É possível criar uma AMI em uma instância configurada como um backup restaurável
    - É possível substituir uma instância com falha iniciando uma nova instância da mesma AMI
 

### 2) Selecionar um tipo de instância
#### - Considere seu caso de uso 
    - Como será usada a instância do EC2 que você criar?
#### - O tipo de instância que você escolher determinará 
    - Memória (RAM) 
    - Capacidade de processamento (CPU) 
    - Espaço em disco e tipo de disco (armazenamento) 
    - Desempenho de rede
#### - Categorias de tipo de instância: 
    - Uso geral 
    - Otimizadas para computação 
    - Otimizadas para memória 
    - Otimizadas para armazenamento 
    - Computação acelerada
#### - Os tipos de instância oferecem família, geração e tamanho 

## Denominação e tamanhos de tipo de instância do EC2 

| Nome da Instância | vCPU | Memória(GB) | Armazenamento |
|-------------------|------|-------------|---------------|
| t3.nano | 2 | 0,5 | Somente EBS |
| t3.micro | 2 | 1 | Somente EBS |
| t3.small | 2 | 2 | Somente EBS |
| t3.Mediun | 2 | 4 | Somente EBS |
| t3.large | 2 | 8 | Somente EBS |
| t3.xlarge | 4 | 16 | Somente EBS |
| t3.2xlarge | 8 | 32 | Somente EBS |


Exemplo: t3.large  
- T é o nome da família 
- 3 é o número da geração 
- Large é o tamanho

## Casos de uso de tipo de instância
- Os tipos de instância variam de várias maneiras, incluindo o tipo de CPU, a contagem de CPUs ou de núcleos, o tipo de armazenamento, a quantidade de armazenamento, a quantidade de memória e o desempenho de rede.

- As instâncias T3 fornecem instâncias de uso geral com desempenho com capacidade de intermitência que fornecem um nível básico de desempenho de CPU com a capacidade de intermitência acima da linha de base.
- Os casos de uso para esse tipo de instância incluem:
  - sites e aplicativos web
  - ambientes de desenvolvimento
  - servidores de compilação
  - repositórios de código
  - microsserviços
  - ambientes de teste
  - preparação e aplicativos de linha de negócios

- As instâncias C5 são otimizadas para cargas de trabalho com uso intensivo de computação e oferecem alto desempenho econômico a uma taxa baixa de preço por computação.
- Os casos de uso incluem:
    - modelagem científica
    - processamento em batch
    - veiculação de anúncios
    - jogos multijogador altamente dimensionáveis
    - codificação de vídeo.
 
- R5 são instâncias otimizadas para aplicativos com uso intensivo de memória.
- Os casos de uso incluem:
- bancos de dados de alto desempenho
    - mineração e análise de dados
    - bancos de dados na memória
    - caches distribuídos na memória na escala da web
    - aplicativos que executam processamento em tempo real de big data não estruturado
    - clusters Apache Hadoop ou Apache Spark
    - outros aplicativos empresariais.



![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fedbb61b-342a-4748-b3bd-70b8ed46d81e)





