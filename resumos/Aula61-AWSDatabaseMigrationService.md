# Aula 60 - AWS Database Migration Service (AWS DMS)
O AWS Database Migration Service ajuda você a migrar bancos de dados para a AWS de modo rápido e seguro
#### Outros recursos importantes
- O AWS DMS pode replicar dados quase continuamente e é usado com alta disponibilidade.
- 
#### Mais recursos que o AWS DMS oferece
- Se necessário, o AWS DMS habilita bancos de dados consolidados em um data warehouse em escala de petabytes em outros serviços da Amazon. Exemplos desses serviços são o Amazon Redshift e o Amazon S3.

#### Conversão de migração de sintaxe
O AWS DMS pode migrar entre a linguagem de consulta estruturada (SQL) e bancos de dados NoSQL. Por exemplo, ele pode migrar de: 
- SQL para SQL
- NoSQL para SQL
- SQL para NoSQL
- NoSQL para NoSQL.

Por exemplo, você pode migrar do Amazon S3 como uma fonte NoSQL para o Amazon Relational Database Service (Amazon RDS) como um destino SQL.


## Tipos de migrações de banco de dados
### migrações homogêneas de bancos
Compreendendo migrações homogêneas de bancos de dados Destinos Em migrações homogêneas de banco de dados, os mecanismos de banco de dados de origem e de destino são os mesmos ou são compatíveis.
Como a estrutura do esquema, os tipos de dados e o código do banco de dados são compatíveis entre os bancos de dados de origem e destino, esse tipo de migração é um processo que consiste em apenas uma etapa. 
O banco de dados de origem pode estar localizado em um campus corporativo ou localmente fora da AWS. 
Ele pode ser executado em uma instância do Amazon Elastic Compute Cloud (Amazon EC2) ou pode ser um banco de dados do RDS. O destino pode ser um banco de dados no Amazon EC2 ou Amazon RDS.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d77a8cd5-29af-4c52-a1cb-de34f354496b)

### Migrações Heterogêneas de Banco de Dados
A migração heterogênea é um processo de duas etapas.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1eda3a6c-001e-4abe-b208-5d3cc59ca61f)

Em migrações de banco de dados heterogêneas, os mecanismos de banco de dados de origem e de destino são diferentes. 
Os exemplos incluem migrações do Oracle para o Amazon Aurora ou do Microsoft SQL Server para o MySQL. 
Nesses casos, a estrutura do esquema, os tipos de dados e o código do banco de dados dos bancos de dados de origem e destino podem ser muito diferentes. Assim, uma transformação de esquema e código é necessária antes do início da migração de dados.
As etapas do processo são: 
- A primeira etapa usa a AWS SCT para converter o esquema de origem e o código para corresponder ao esquema e ao código do banco de dados de destino.
- A segunda etapa usa o AWS DMS para migrar dados do banco de dados de origem para o banco de dados de destino.

## Visão de alto nível
### Em um grau elevado - O processo em alto nível
Uma migração de banco de dados segue o seguinte processo: 
- Conecta-se ao armazenamento de dados de origem
- Lê os dados de origem
- Formata os dados para consumo pelo armazenamento de dados de destino
- Depois, ela carrega os dados no datastore de destino

#### O que acontece?
Ao usar o AWS DMS, você executa as seguintes ações:
- Criar um servidor de replicação (instância).
- Criar pontos de extremidade de origem e de destino que tenham informações de conexão sobre os datastores.
- Criar uma ou mais tarefas de migração para migrar os dados entre os datastores de origem e de destino.
-  Uma tarefa pode consistir em três fases principais:
    -  A carga total de dados existentes
    -  O aplicativo de alterações em cache
    -  Replicação contínua

## AWS Schema Conversion Tool
A maioria das migrações de banco de dados envolve duas etapas: converter o esquema usando o AWS SCT e migrar os dados usando o AWS DMS.
O AWS DMS, junto com o AWS SCT, permite migrar seu banco de dados para a AWS enquanto reduz o tempo de inatividade
A AWS SCT facilita migrações de bancos de dados heterogêneos. 
Ela converte automaticamente o esquema do banco de dados de origem e a maioria dos objetos de código do banco de dados, incluindo exibições, procedimentos armazenados e funções. 
Ela os converte em um formato compatível com o banco de dados de destino. 

### Conversões compatíveis com o AWS SCT 
O AWS SCT converte:
- Esquema de bancos de dados de origem
- Visualizações
- Procedimentos armazenados
- Funções


| Banco de Dados de Origem | Banco de dados de destino no Amazon RDS |
|--------------------------| ------------------|
| Oracle Database | Amazon Aurora, MySQL, PostgreSQL, MariaDB |
| Oracle Data Warehouse | Amazon Redshift |
| Azure SQL | Amazon Aurora, MySQL, PostgreSQL |
| Microsoft SQL Server | Amazon Aurora, Amazon Redshift, MySQL, PostgreSQL, MariaDB |
| Teradata | Amazon Redshift |
| IBM Netezza Greenplum | Amazon Redshift |
| HPE Vertica | Amazon Redshift |
| MySQL e MariaDB | PostgreSQL |
| PostgreSQL | Amazon Aurora, MySQL, MariaDB |
| Amazon Aurora | PostgreSQL |
| IBM Db2 LUW | Amazon Aurora, MySQL, PostgreSQL |
| Apache Cassandra | Amazon DynamoDB |
| SAP ASE | RDS para MySQL, Aurora MySQL, RDS para PostgreSQL e Aurora PostgreSQL |

----> continua 

## Replicação quase contínua de banco de dados

## Consolidação do AWS DM

## Arquitetura de processos do AWS DMS

## Instância de replicação do AWS DMS

