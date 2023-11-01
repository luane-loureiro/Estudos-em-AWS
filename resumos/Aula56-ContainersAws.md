# AConteiners AWS
## O problema
-  “Ele funcionou na minha máquina!”
-  “Você precisa atualizar o sistema operacional de seu computador!”
-  “Você não tem o software necessário para executá-lo!”
-  ...assim por diante!

## Containers
### Introdução aos contêineres Os contêineres são:
- Um método de virtualização do sistema operacional
- Assim como as máquinas virtuais virtualizam o hardware, os contêineres virtualizam um sistema operacional.
- Um aplicativo e suas dependências, que podem ser executadas em processos isolados de recursos

### Benefícios do uso de contêineres 
- Consistência no ambiente
- Eficiência operacional
- Produtividade do desenvolvedor
- Controle de versões

### Mas como?
Os contêineres nos ajudam a resolver alguns dos problemas com programas de software novos e atualizados.
Mas como:
- Criar um contêiner? 
- Executar o contêiner? 
- Gerenciar e implantar vários contêineres?

## Docker 
- O Docker é uma plataforma de aplicativos usada para criar, gerenciar e executar contêineres
- O Docker permite que os desenvolvedores e engenheiros criem, testem e implantem e executem contêineres
- é uma plataforma de software que empacota programas de software (como aplicativos) em unidades chamadas contêineres.
- O Docker é mais adequado como solução quando você deseja:
    - Padronizar ambientes
    - Reduzir conflitos entre pilhas de linguagem e versões
    - Usar contêineres como serviço
    - Executar microsserviços usando implantações de código padronizadas
    - Exigir portabilidade para o processamento de dados
 
### Implantações de exemplo do Docker

## Docker na AWS
### Amazon Elastic Container Registry (Amazon ECR) 
O Amazon ECR é um registro de contêiner do Docker totalmente gerenciado que facilita o armazenamento, o gerenciamento e a implantação de imagens de contêineres do Docker para desenvolvedores.

- Integração com o Amazon ECS 
- Suporte do Docker
- Alta disponibilidade e durabilidade
- Colaboração em equipe Controle de acesso
- Criptografia de dados ociosos
- Integrações com terceiros

### Amazon Elastic Container Service (Amazon ECS)
O Amazon Elastic Container Service (Amazon ECS) é:
- Um serviço de gerenciamento de contêineres altamente dimensionável e de alto desempenho
- Compatível com contêineres do Docker

#### Benefícios do Amazon ECS:
Alguns dos benefícios do Amazon ECS:
- Serviço de gerenciamento de contêineres
- Programação flexível
- Integrado e extensível Segurança
- Desempenho em grande escala
- Definições de tarefas


## Gerenciamento de contêineres
### Kubernetes
O Kubernetes é um software de código aberto de gerenciamento e orquestração de contêineres.
Use o Kubernetes para: 
- Gerenciar clusters de instâncias de computação do EC2 
- Executar contêineres nessas instâncias com processos para implantação, manutenção e scaling
    - Executar aplicativos em grande escala
    - Transferir aplicativos de forma transparente
    - Executar em qualquer lugar
    - Adicionar uma nova funcionalidade
    - Criado pela google


## Amazon Elastic Kubernetes Service (Amazon EKS): gerenciamento de contêineres com o Kubernetes
Você pode optar por gerenciar a infraestrutura do Kubernetes por conta própria executando-a em instâncias do EC2. Ou você pode usar um plano de controle do Kubernetes provisionado e gerenciado automaticamente com o Amazon EKS. 
O Amazon EKS facilita a implantação, o gerenciamento e o dimensionamento de aplicativos conteinerizados por meio do Kubernetes. 
Ele executa a infraestrutura de gerenciamento do Kubernetes para você em várias Zonas de Disponibilidade da AWS para eliminar os pontos únicos de falha. 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8709839a-40dd-483a-bce6-192b47c864de)

O diagrama mostra como o Amazon EKS funciona:
1. Provisionar um cluster do Amazon EKS. O Amazon EKS implanta automaticamente nós do plano de controle do Kubernetes.
2. Implantar nós de operador. Adiciona o número de nós de operador necessários para seu cluster do Amazon EKS.
3. Conectar-se ao Amazon EKS. Aponta suas ferramentas preferidas do Kubernetes para o cluster do Amazon EKS.
4. Executar os aplicativos do Kubernetes. Implanta seus aplicativos do Kubernetes em seu cluster do Amazon EKS


## AWS Fargate: execução de contêineres sem gerenciamento de servidores
O AWS Fargate é uma tecnologia para o Amazon ECS que permite que você execute contêineres sem precisar gerenciar servidores nem clusters.
- Sem clusters para gerenciar
- Scaling transparente
- Funciona com o Amazon ECS
- Opções de configuração flexíveis
- Preço com base em recursos


### Uso do tipo de inicialização do AWS Fargate

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ba70856c-dda0-453f-9e35-209a4ce2fef9)


Com o tipo de inicialização do Fargate, suas tarefas são mínimas. Você só precisa empacotar seu aplicativo em contêineres, especificar os requisitos de CPU e memória, definir Políticas de IAM e de redes e iniciar o aplicativo.
O Fargate gerencia o scaling e infraestrutura necessários para executar seus contêineres de uma forma altamente disponível.


## Desafios do gerenciamento de contêineres
- Os desafios do gerenciamento de contêineres incluem: 
    - O uso de contêineres está crescendo rapidamente
    - Prevenção contra a expansão de contêineres
    - Diferenças de versões
    - Mentalidade de dono
    - Empacotamento de lixeira
    - Contêineres que não são mais necessários (contêineres zumbi)
    - Contêineres que desaparecem

