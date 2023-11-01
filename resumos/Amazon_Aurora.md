# Amazon Aurora
O Amazon Aurora é um mecanismo de banco de dados relacional totalmente gerenciado que é compatível com o MySQL e o PostgreSQL

## Aurora
### O que é o Amazon Aurora?
- O Aurora é um banco de dados relacional criado para a nuvem
- O Aurora faz parte do serviço de banco de dados gerenciado Amazon Relational Database Service (Amazon RDS).
- O Aurora é até cinco vezes mais rápido que os bancos de dados MySQL padrão.
- O Aurora é composto de clusters.
- O Aurora também automatiza e padroniza o agrupamento em clusters e a replicação de bancos de dados, que normalmente são os aspectos mais difíceis da configuração e administração do banco de dados.

### Principais Recursos do Amazon Aurora
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4d5cf517-aff6-4275-9861-6476bb9524ff)
## Instâncias do Amazon Aurora e cluster de banco de dados
- Ao criar uma instância do Amazon Aurora, você cria um cluster de banco de dados (DB).
- Um cluster de banco de dados do Aurora consiste em uma ou mais instâncias do banco de dados e um volume de cluster que gerencia os dados para essas instâncias.

### Volume do cluster do Aurora Volumes de cluster
- Um volume de cluster do Aurora é um volume de armazenamento de banco de dados virtual que abrange várias Zonas de Disponibilidade. Cada Zona de Disponibilidade tem uma cópia de dados do cluster. Um cluster de banco de dados do Aurora é composto de dois tipos de instância de banco de dados:
    - Instância de banco de dados primário 
    - Instância do Aurora
 

### O que é um cluster de banco de dados do Amazon Aurora? 
Dois tipos de clusters de banco de dados do Amazon Aurora
- A **instância primária** comporta operações de leitura e gravação e realiza todas as modificações de dados no volume do cluster. Cada cluster de banco de dados do Aurora tem uma instância primária.
- Uma **réplica** do Aurora comporta operações somente leitura. Cada cluster de banco de dados do Aurora pode ter até 15 réplicas do Aurora, além da instância primária. Várias réplicas distribuem a carga de trabalho de leitura e, se estiverem localizadas em Zonas de Disponibilidade separadas, poderão aumentar a disponibilidade do banco de dados.

## Casos de Uso
### Aplicativos corporativos
Comparado aos bancos de dados comerciais, o Aurora ajuda a reduzir os custos de banco de dados em 90% ou mais e, ao mesmo tempo, melhora a confiabilidade e a disponibilidade do banco de dados.

### Aplicativos de software como serviço (SaaS)
Nesse caso, o Aurora fornece recursos em uma oferta de banco de dados gerenciado. Assim, as empresas SaaS podem se concentrar na criação de aplicativos de alta qualidade sem se preocupar com o banco de dados subjacente que alimenta o aplicativo.

### jogos na web e em dispositivos móveis
Como os jogos para web e dispositivos móveis são criados para operar em grande escala, eles precisam de um banco de dados com alta taxa de transferência e grande escalabilidade de armazenamento. O Aurora oferece espaço suficiente para crescimento futuro.


