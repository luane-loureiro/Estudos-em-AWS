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

## Amazon S3
É um serviço que fornece armazenamento a nível do objeto. O Amazon S3 armazena dados como objetos em buckets.
É possível fazer upload de qualquer tipo de arquivo para o Amazon S3, como imagens, vídeos, arquivos de texto e assim por diante. 
Por exemplo, você pode usar o Amazon S3 para armazenar arquivos de backup, arquivos de mídia para um site ou documentos arquivados. 
O Amazon S3 oferece espaço de armazenamento ilimitado. O tamanho máximo de arquivo para um objeto no Amazon S3 é de 5 TB.


Buckets 🪣 = 📁 Diretórios, Pastas
Objetos 📦 = 📄 Arquivos


Ao fazer upload de um arquivo para o Amazon S3, é possível definir permissões para controlar a visibilidade e o acesso a ele. Você também pode usar o recurso de versionamento do Amazon S3 para rastrear alterações em seus objetos ao longo do tempo.


