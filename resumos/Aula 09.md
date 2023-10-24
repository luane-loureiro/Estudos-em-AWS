 # Amazon Simple Storage Service (Amazon S3) 
 ## Managed Cloud Storage Solution 
 - data is stored as objects in buckets 🪣 
 - Unlimited storage 
 - a single object can be up to 5tb 
 - designed for 11 nine (99.999999999%) durability 
 - granular access to buckets and objects 
 - Objects can be virtually any data file, such as documents, images or videos. 
 - When adding objects to a bucket, give them a unique name, which is called the object key. 
 - By default, data is private, and you have the option to encrypt it 
 - Data is stored redundantly 
 - It is possible to recover data at any time and anywhere via the Internet 
 
 ## Amazon S3 Storage classes 
 #### - Amazon S3 Standard 
 High-durability, high-availability, and high-performance object storage for frequently accessed data. Because it provides low latency and high throughput, Amazon S3 Standard is suitable for many use cases, such as cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics. 
 
 #### - Amazon S3 Intelligent-Tiering 
 High-durability, high-availability, and high-performance object storage for frequently accessed data. Because it provides low latency and high throughput, Amazon S3 Standard is suitable for many use cases, such as cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics. 
 
 #### - Amazon S3 Standard-Infrequent Access (Amazon S3 Standard-IA) 
 used for data that is accessed less frequently but requires quick access when needed. The Amazon S3 Standard – IA category is designed to deliver the high durability, high throughput, and low latency of the Amazon S3 Standard categories, with reduced rates per GB of storage and GB of retrieval. 
 Ideal for long-term storage and backups and as a datastore for disaster recovery (DR) files. 
 
 #### - Amazon S3 One Zone-Infrequent Access (Amazon S3 One Zone-IA) 
 designed for data that is accessed less frequently but requires quick access when needed. Unlike other Amazon S3 storage classes, which store data in a minimum of three Availability Zones, Amazon S3 One Zone – IA stores data in a single Availability Zone. 
 It's a great option for storing secondary backup copies of data on-premises or data that can be easily recreated. 
 
 #### - Amazon Simple Storage Service Glacier 
 a secure, durable, and low-cost class of storage for data archiving. You can reliably store any volume of data at a cost that is competitive or lower than on-premises solutions. 
 
 #### - Amazon S3 Glacier Deep Archive 
 lowest-cost Amazon S3 storage class. It offers long-term retention and digital preservation for data that can be accessed once or twice a year. 
 
 
 ## Access data anywhere 
 - aws management console 
 - AWS CLI 
 - AWS SDKs 
 - Rest endpoints 
 
 ## Amazon S3 object and bucket URL structure 
 
 ![ image ] ( https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/63397d54-cfb1-4803-a9ca-598520d37f40 ) 
 
 
 The example shows how a bucket URL is structured. The Region code is first, followed by amazonaws.com and the bucket name 
 An object is made up of data and any metadata that describes that file. 
 
 
 ## Redundancy in Amazon S3 
 - When you create a bucket in Amazon S3, it is associated with a specific AWS Region. 
 - Whenever you store data in the bucket, it is stored redundantly across multiple AWS installations in the selected Region. 
 - Amazon S3 is designed to store data durably even if there is simultaneous data loss across two AWS installations. 
 
 ## Seamless scaling 
 - Amazon S3 automatically manages the storage behind the bucket even as the amount of data increases. This allows you to get started immediately and have your data storage grow as your application needs. 
 Amazon S3 also scales to handle a high volume of requests. You don't need to provision storage or throughput, and you'll only be charged for what you use. 
 
 ## Common Amazon S3 use cases 
 - Application asset storage 
 - Web hosting of static websites
 - Backup and Disaster Recovery (DR)
 - Staging area for big data Many more. 
 
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
