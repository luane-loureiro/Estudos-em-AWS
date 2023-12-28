# Armazenamento e Banco de Dados
## Armazenamentos de instância e Amazon Elastic Block Store (Amazon EBS)
### Armazenamentos de instâncias
Os volumes de armazenamento a nível de bloco se comportam como discos rígidos físicos.
Um armazenamento de instância(opens in a new tab) é um meio temporário de armazenamento a nível de bloco para uma instância do Amazon EC2.
Um armazenamento de instância é o armazenamento em disco fisicamente anexo ao computador host para uma instância do EC2 e, portanto, tem a mesma vida útil da instância. 
Quando a instância for terminada, você perderá todos os dados no armazenamento de instância.
O **Amazon Elastic Block Store (Amazon EBS)** é um serviço que fornece volumes de armazenamento a nível de bloco que você pode usar com instâncias do Amazon EC2. Se você interromper ou terminar uma instância do Amazon EC2, todos os dados no volume do EBS anexo permanecerão disponíveis.
Para criar um volume do EBS, defina a configuração (como tamanho e tipo do volume) e a provisão. Depois de criado, o volume do EBS pode ser anexado a uma instância do Amazon EC2.
Como os volumes do EBS são para dados que precisam perdurar, é importante fazer backup dos dados. Você pode fazer backups incrementais de volumes do EBS criando snapshots do Amazon EBS.

### Snap shot do Amazon EBS
Um **snapshot do EBS** é um backup incremental. Isso significa que o primeiro backup de um volume copia todos os dados. 
Nos backups subsequentes, somente os blocos de dados que foram alterados desde o snapshot mais recente são salvos. 
Os backups incrementais são diferentes dos backups completos, nos quais todos os dados em um volume de armazenamento são copiados cada vez que ocorre um backup.
O backup completo inclui dados que não foram alterados desde o backup mais recente.


## Amazon S3 (Simple Storage Service)
### Armazenamento de objetos
No armazenamento de objetos, cada objeto consiste em dados, metadados e uma chave.
Os **dados** podem ser uma imagem, vídeo, documento de texto ou qualquer outro tipo de arquivo. 
Os **metadados** contêm informações sobre o que são os dados, como eles são usados, o tamanho do objeto e assim por diante. 
A **chave** de um objeto é seu identificador exclusivo.

### Amazon S3
É um serviço que fornece armazenamento a nível do objeto. O Amazon S3 armazena dados como objetos em buckets.
É possível fazer upload de qualquer tipo de arquivo para o Amazon S3, como imagens, vídeos, arquivos de texto e assim por diante. 
Por exemplo, você pode usar o Amazon S3 para armazenar arquivos de backup, arquivos de mídia para um site ou documentos arquivados. 
O Amazon S3 oferece espaço de armazenamento ilimitado. O tamanho máximo de arquivo para um objeto no Amazon S3 é de 5 TB.

```
Buckets 🪣 = 📁 Diretórios, Pastas
Objetos 📦 = 📄 Arquivos
```

Ao fazer upload de um arquivo para o Amazon S3, é possível definir permissões para controlar a visibilidade e o acesso a ele. Você também pode usar o recurso de versionamento do Amazon S3 para rastrear alterações em seus objetos ao longo do tempo.

### Storage classes do Amazon S3
Com o Amazon S3, você paga somente pelo que usar. Você pode escolher dentre diversas storage classes(opens in a new tab) aquela que melhor se ajusta às suas necessidades de negócios e de custo. Ao selecionar uma storage class do Amazon S3, considere estes dois fatores:
- Com que frequência você planeja recuperar seus dados
- Seus dados precisam estar muito ou pouco disponíveis

#### Amazon S3 Standard
- Projetado para dados acessados com frequência
- Armazena dados em um mínimo de três Zonas de Disponibilidade
  
O Amazon S3 Standard fornece alta disponibilidade para objetos. Isso o torna uma boa escolha para diversos casos de uso, como sites, distribuição de conteúdo e data analytics. O Amazon S3 Standard tem um custo mais alto do que outras storage classes destinadas a dados acessados com pouca frequência e armazenamento de arquivamento.

#### Amazon S3 Standard IA (infrequent access)
- Ideal para dados com pouca frequência de acesso
- Semelhante ao Amazon S3 Standard, mas com um preço de armazenamento mais baixo e um preço de recuperação mais alto
  
O Amazon S3 Standard-IA é ideal para dados acessados com pouca frequência, mas que precisam ter alta disponibilidade para quando necessário. O Amazon S3 Standard e o Amazon S3 Standard-IA armazenam dados no mínimo em três Zonas de Disponibilidade. O Amazon S3 Standard-IA tem o mesmo nível de disponibilidade da Amazon S3 Standard, mas com um preço de armazenamento mais baixo e um preço de recuperação mais alto.


#### Amazon S3 one zone - infrequent access (S3 one zone - IA)
- Armazena dados em uma única Zona de Disponibilidade
- Tem um preço de armazenamento menor do que o Amazon S3 Standard-IA
  
Comparado com o S3 Standard e o S3 Standard-IA, que armazenam dados em um mínimo de três Zonas de Disponibilidade, o S3 One Zone – IA armazena em uma única Zona de Disponibilidade. Isso o torna uma boa storage class nas seguintes condições:

- o ideal é economizar custos com armazenamento.
- Você pode reproduzir facilmente seus dados em caso de falha na Zona de Disponibilidade.

#### Amazon S3 intelligent Tiering
- Ideal para dados com padrões de acesso desconhecidos ou em alteração
- Requer uma pequena taxa mensal de monitoramento e automação por objeto
  
Na storage class S3 Intelligent-Tiering, o Amazon S3 monitora os padrões de acesso dos objetos. Se você não acessou um objeto por 30 dias consecutivos, o Amazon S3 o move automaticamente para o nível de acesso pouco frequente S3 Standard – IA. Se você acessar um objeto no nível de acesso pouco frequente, o Amazon S3 o move automaticamente para o nível de acesso frequente S3 Standard.

#### S3 Glacier instant Retrieval
- Funciona bem para dados arquivados que requerem acesso imediato
- Pode recuperar objetos em alguns milissegundos

Ao decidir entre as opções de armazenamento de arquivamento, considere a rapidez com que deve recuperar os objetos arquivados. Você pode recuperar objetos armazenados na storage class do S3 Glacier Instant Retrieval em milissegundos, com o mesmo desempenho que o S3 Standard.

#### S3 Glacier Flexible Retrieval
- Armazenamento de baixo custo projetado para arquivamento de dados
- Capaz de recuperar objetos em poucos minutos a horas

O S3 Glacier Flexible Retrieval é uma storage class de baixo custo, ideal para o arquivamento de dados. Por exemplo, você pode usar essa storage class para armazenar registros de clientes arquivados ou arquivos de fotos e vídeos mais antigos. Você pode recuperar seus dados do S3 Glacier Flexible Retrieval de 1 minuto a 12 horas.

#### S3 Glacier deep Archive
- Storage class de objetos de menor custo, ideal para arquivamento
- Capaz de recuperar objetos em 12 horas

O S3 Deep Archive dá suporte a retenção de longo prazo e preservação digital de dados acessados uma ou duas vezes por ano. Essa storage class é o armazenamento de menor custo na nuvem AWS, com recuperação de dados de 12 a 48 horas. Todos os objetos dessa storage class são replicados e armazenados em pelo menos três Zonas de Disponibilidade geograficamente dispersas.

#### S3 Outposts
- Cria buckets do S3 no Amazon S3 Outposts
- Torna mais fácil recuperar, armazenar e acessar dados no AWS Outposts

O Amazon S3 Outposts oferece armazenamento de objetos para seu ambiente on-premises do AWS Outposts. O Amazon S3 Outposts foi projetado para armazenar dados de maneira durável e redundante em vários dispositivos e servidores em seus Outposts. Por manter os dados próximos às aplicações on-premises, ele funciona bem para cargas de trabalho que exigem um alto desempenho e a permanência dos dados no local.


## Amazon Elastic File System (Amazon EFS)
### Armazenamento de arquivos
No armazenamento de arquivos, vários clientes (como usuários, aplicações, servidores e assim por diante) podem acessar os dados armazenados em pastas de arquivos compartilhadas. Nessa abordagem, um servidor de armazenamento usa armazenamento em bloco com um sistema de arquivos local para organizar os arquivos. Os clientes acessam dados por meio de caminhos de arquivo.
Comparado ao armazenamento em blocos e ao armazenamento de objetos, o armazenamento de arquivos é ideal para casos de uso em que um grande número de serviços e recursos precisam acessar os mesmos dados ao mesmo tempo.
O **Amazon Elastic File System (Amazon EFS)** é um sistema de arquivos dimensionável usado com os AWS Cloud Services e recursos on-premises. À medida que você adiciona e remove arquivos, o Amazon EFS expande e retrai automaticamente. Ele pode dimensionar sob demanda para petabytes sem interromper os aplicativos. 

### Comparação entre EBS e EFS

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fa656650-2046-4e49-95c4-5944ab801c11)
