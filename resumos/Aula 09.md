# Serviço de armazenamento simples da Amazon (Amazon S3)
  ## Solução gerenciada de armazenamento em nuvem
  - os dados são armazenados como objetos em buckets 🪣
  - Armazenamento ilimitado
  - um único objeto pode ter até 5 TB
  Projetado para durabilidade de 11 nove (99,999999999%)
  - acesso granular a buckets e objetos
  - Os objetos podem ser praticamente qualquer arquivo de dados, como documentos, imagens ou vídeos.
  - Ao adicionar objetos a um bucket, dê a eles um nome exclusivo, chamado chave do objeto.
  - Por padrão, os dados são privados e você tem a opção de criptografá-los
  - Os dados são armazenados de forma redundante
  - É possível recuperar dados a qualquer hora e em qualquer lugar através da Internet
 
  ## Classes de armazenamento do Amazon S3
  #### - Padrão Amazon S3
  Armazenamento de objetos de alta durabilidade, alta disponibilidade e alto desempenho para dados acessados com frequência. Por fornecer baixa latência e alta taxa de transferência, o Amazon S3 Standard é adequado para muitos casos de uso, como aplicativos em nuvem, sites dinâmicos, distribuição de conteúdo, aplicativos móveis e de jogos e análise de big data.
 
  #### - Camadas inteligentes do Amazon S3
  Armazenamento de objetos de alta durabilidade, alta disponibilidade e alto desempenho para dados acessados com frequência. Por fornecer baixa latência e alta taxa de transferência, o Amazon S3 Standard é adequado para muitos casos de uso, como aplicativos em nuvem, sites dinâmicos, distribuição de conteúdo, aplicativos móveis e de jogos e análise de big data.
 
  #### - Acesso infrequente ao padrão Amazon S3 (Amazon S3 Standard-IA)
  usado para dados acessados com menos frequência, mas que exigem acesso rápido quando necessário. A categoria Amazon S3 Standard – IA foi projetada para oferecer alta durabilidade, alta taxa de transferência e baixa latência das categorias Amazon S3 Standard, com taxas reduzidas por GB de armazenamento e GB de recuperação.
  Ideal para armazenamento e backups de longo prazo e como armazenamento de dados para arquivos de recuperação de desastres (DR).
 
  #### - Acesso pouco frequente ao Amazon S3 One Zone (Amazon S3 One Zone-IA)
  projetado para dados que são acessados com menos frequência, mas que exigem acesso rápido quando necessário. Ao contrário de outras classes de armazenamento do Amazon S3, que armazenam dados em no mínimo três zonas de disponibilidade, o Amazon S3 One Zone – IA armazena dados em uma única zona de disponibilidade.
  É uma ótima opção para armazenar cópias de backup secundárias de dados locais ou dados que podem ser facilmente recriados.
 
  #### - Geleira do Amazon Simple Storage Service
  uma classe de armazenamento segura, durável e de baixo custo para arquivamento de dados. Você pode armazenar com segurança qualquer volume de dados a um custo competitivo ou inferior ao das soluções locais.
 
  #### - Arquivo profundo do Amazon S3 Glacier
  classe de armazenamento Amazon S3 de menor custo. Oferece retenção de longo prazo e preservação digital para dados que podem ser acessados uma ou duas vezes por ano.
 
 
  ## Acesse dados em qualquer lugar
  - console de gerenciamento AWS
  -AWS CLI
  - SDKs da AWS
  - Pontos finais de descanso
 
  ## Objeto do Amazon S3 e estrutura de URL do bucket
 
  ![ imagem ] ( https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/63397d54-cfb1-4803-a9ca-598520d37f40 )
 
 
  O exemplo mostra como um URL de bucket é estruturado. O código da região vem primeiro, seguido por amazonaws.com e o nome do bucket
  Um objeto é composto de dados e quaisquer metadados que descrevam esse arquivo.
 
 
  ## Redundância no Amazon S3
  - Quando você cria um bucket no Amazon S3, ele é associado a uma região específica da AWS.
  - Sempre que você armazena dados no bucket, eles são armazenados de forma redundante em várias instalações da AWS na região selecionada.
  - O Amazon S3 foi projetado para armazenar dados de maneira durável, mesmo se houver perda simultânea de dados em duas instalações da AWS.
 
  ## Dimensionamento contínuo
  - O Amazon S3 gerencia automaticamente o armazenamento por trás do bucket, mesmo quando a quantidade de dados aumenta. Isso permite que você comece imediatamente e aumente seu armazenamento de dados conforme a necessidade do seu aplicativo.
  O Amazon S3 também pode ser dimensionado para lidar com um grande volume de solicitações. Você não precisa provisionar armazenamento ou taxa de transferência e só será cobrado pelo que usar.
 
  ## Casos de uso comuns do Amazon S3
  - Armazenamento de ativos de aplicativos
  - Hospedagem de sites estáticos
  - Backup e recuperação de desastres (DR)
  - Área de preparação para big data Muito mais.
## Preços do Amazon S3
#### Pague somente pelo que usa:
- GBs por mês
- Transferência para FORA, para outras regiões
- Solicitações PUT, COPY, POST, LIST e GET
- 
#### Você NÃO precisa pagar por:
- Transferência para DENTRO do Amazon S3
- Transferência para FORA entre o Amazon S3 e o Amazon CloudFront ou o Amazon EC2 na mesma região

#### Estimativa de custo do Amazon S3 
1. Tipo de classe de armazenamento:
- O armazenamento padrão foi projetado para fornecer 11 noves de durabilidade e quatro noves de disponibilidade.
- O Standard – Infrequent Access (S-IA) pode reduzir os custos ao armazenar os dados acessados com menos frequência em níveis de redundância um pouco mais baixos do que Amazon S3 Standard Storage. O Standard – Infrequent Access foi projetado para fornecer a mesma durabilidade de 11 noves do Amazon S3, com e noves de disponibilidade em determinado ano. É importante observar que cada classe tem taxas diferentes.

2. Quantidade de armazenamento: o número e o tamanho dos objetos armazenados nos buckets do S3, e o tipo de armazenamento, também devem ser considerados.

3. Solicitações: considere o número e o tipo das solicitações. As solicitações GET geram cobranças em taxas diferentes das outras solicitações, como solicitações PUT e COPY.
- GET: recupera um objeto do Amazon S3. Você deve ter acesso de LEITURA para usar essa operação
- PUT: adiciona um objeto a um bucket. Você deve ter permissões de GRAVAÇÃO em um bucket para adicionar um objeto a ele.
- COPY: cria uma cópia de um objeto que já está armazenado no Amazon S3. Uma operação COPY é o mesmo que executar um GET e, em seguida, um PUT

4.  Transferência de dados: considere a quantidade de dados transferidos para fora da Região do Amazon S3. Lembre-se de que a transferência de dados é gratuita, mas você será cobrado pela transferência de dados para fora.
