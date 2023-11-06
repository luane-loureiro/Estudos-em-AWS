# Aula 65 - Visão geral do armazenamento na nuvem
O armazenamento na nuvem é um modelo de computação na nuvem que armazena dados na Internet por meio de um provedor de computação na nuvem, que gerencia e opera o armazenamento de dados como um serviço

## Principais conceitos
### Como o armazenamento na nuvem funciona
O armazenamento na nuvem é adquirido de um fornecedor de nuvem terceirizado, que possui e opera a capacidade de armazenamento de dados e a entrega pela Internet em um modelo de pagamento conforme o uso. 
Esses fornecedores de armazenamento na nuvem gerenciam capacidade, segurança e durabilidade para tornar os dados acessíveis aos seus aplicativos de todo o mundo.

### Serviços de armazenamento da AWS

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ed8d0056-e009-4ae4-9f1a-091274179a32)

O armazenamento é outra categoria de serviço importante da AWS. Ele tem três grandes categorias: armazenamento de instâncias (ou armazenamento temporário), Amazon EBS e Amazon Simple Storage Service (Amazon S3).
O armazenamento de instâncias, ou armazenamento temporário, é um armazenamento temporário que é adicionado à sua instância do Amazon Elastic Compute Cloud (Amazon EC2).
• O Amazon EBS é um armazenamento persistente e montável. Um volume do EBS pode ser montado como um dispositivo para uma instância do EC2, mas somente se ambos estiverem na mesma zona de disponibilidade.
• Semelhante ao Amazon EBS, o Amazon S3 é um armazenamento persistente. No entanto, ele pode ser acessado de qualquer lugar.


### Quatro categorias de armazenamento na nuvem A AWS oferece quatro categorias para armazenamento na nuvem:
- Armazenamento em bloco
    -  O Amazon Elastic Block Store (Amazon EBS) fornece recursos de armazenamento em bloco altamente disponíveis e de baixa latência para cargas de trabalho que exigem armazenamento persistente acessível a partir de uma instância do Amazon Elastic Compute Cloud (Amazon EC2).

- Armazenamento de objetos - Dois serviços se enquadram nessa categoria.
    - O Amazon Simple Storage Service (Amazon S3) foi projetado para armazenar objetos de qualquer tipo de forma segura, durável e escalável e torná-los acessíveis pela Internet.
    - O Amazon Simple Storage Service Glacier fornece armazenamento de objetos de baixo custo e altamente durável para backup e arquivamento de longo prazo de qualquer tipo de dados.

- Armazenamento de arquivos - Dois serviços oferecem suporte ao armazenamento de dados no nível do arquivo.
    - O Amazon Elastic File System (Amazon EFS) fornece um sistema de arquivos simples, escalável e elástico para cargas de trabalho baseadas no Linux.
    - O Amazon FSx for Windows File Server fornece um sistema de arquivos nativo do Microsoft Windows totalmente gerenciado para oferecer suporte a aplicativos do Windows executados na AWS.
    
- Armazenamento na nuvem híbrida
    - O AWS Storage Gateway fornece um link que conecta seu ambiente local aos serviços de armazenamento na nuvem da AWS de maneira resiliente e eficiente.
 
## Casos de uso e cenários de armazenamento na nuvem da AWS
### Armazenamento na nuvem na AWS 
Casos de uso para serviços de armazenamento na nuvem:
- Análise de big data
- Data warehouses
- Bancos de dados
- Backup e arquivo
  
Todos os aplicativos dependem de alguma forma de arquitetura de armazenamento de dados.

### Cenários de armazenamento na nuvem da AWS 
As soluções abordam cenários comuns, como: 
- Armazenar, recuperar e gerenciar dados de aplicativos.
- Armazenar arquivos de log de instâncias transitórias do EC2 em um armazenamento persistente para análise posterior.
- Fazer backup de instâncias do EC2 e dos seus volumes anexados.
- Fazer backup de dados locais para recuperação de desastres (DR).

#### Amazon EBS
- Armazenamento em bloco persistente para o Amazon EC2.
- Armazenamento que funciona bem para bancos de dados e aplicativos.

#### Amazon S3 
-  Uma plataforma escalável e durável que torna os dados acessíveis de qualquer local da Internet.
-  Armazenamento para conteúdo gerado pelo usuário, arquivamento ativo, computação sem servidor, armazenamento de big data ou backup e recuper

#### Amazon S3 Glacier
-  Um serviço de armazenamento na nuvem seguro, durável e de custo extremamente baixo para o arquivamento de dados e backup de longo prazo.


#### Amazon EFS 
- Um sistema de arquivos NFS simples e escalável para cargas de trabalho do Linux que usam serviços de nuvem da AWS e recursos locais


#### AWS Storage Gateway 
- Armazenamento híbrido que amplia seu ambiente local com o armazenamento na nuvem da AWS
- Armazenamento híbrido para recuperação de desastres (DR), estratificação de preços ou migração


#### Amazon FSx
- Um serviço que fornece sistemas de arquivos para várias cargas de trabalho, como armazenamento para aplicativos do Windows, aprendizado de máquina, automação de projeto eletrônico e computação de alto desempenho







