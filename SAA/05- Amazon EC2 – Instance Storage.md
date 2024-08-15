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
