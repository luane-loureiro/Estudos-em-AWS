# Amazon RedShift
O Amazon Redshift é um serviço de data warehouse na nuvem totalmente gerenciado, na escala de petabytes.

## Compreendendo petabytes (PB) e data warehouses
### Petabytes e Data warehouses
#### O que é um petabyte?
- Um petabyte é de 10 15 bytes de informação.
- Um petabyte é aproximadamente igual a 1.000 terabytes (TB).
- Um terabyte é aproximadamente igual a 1.000 gigabytes (GB).

#### O que é data warehouse?
- Um data warehouse é um repositório central de informações que podem ser analisadas para tomar decisões mais adequadas.
- Os data warehouses impulsionam relatórios, painéis e ferramentas de análise. Os data warehouses permitem que os usuários consultem rapidamente os resultados para centenas e milhares de usuários ao mesmo tempo.


### Como isso funciona e quais são os benefícios? 
#### Como funciona um data warehouse?
- Um data warehouse pode conter vários bancos de dados.
- Dentro de cada banco de dados, os dados são organizados em tabelas e colunas.
- Dentro de cada coluna, você pode definir uma descrição dos dados, como número inteiro, campo de dados ou sequência.
- As tabelas podem ser organizadas dentro de esquemas, que você pode considerar como pastas.

#### Os benefícios de um data warehouse são:
- Tomada de decisão adequada
- Dados consolidados de várias fontes
- Análise de dados históricos
- Qualidade, consistência e precisão de dados
- Separação do processamento analítico dos bancos de dados transacionais, o que melhora o desempenho dos dois sistemas


### Arquitetura do Amazon Redshift Como um data warehouse é arquitetado?
- Uma arquitetura de data warehouses é composta de camadas.
- A camada superior é o cliente de front-end, que apresenta os resultados por meio de ferramentas de relatórios, análises e mineração de dados.
- A camada intermediária consiste no mecanismo de análises, usado para acessar e analisar os dados.
- A camada inferior da arquitetura é o servidor de banco de dados, onde os dados são carregados e armazenados.

### Como todos eles trabalham juntos?
- Normalmente, as empresas usam uma combinação de banco de dados, data lake e data warehouse para armazenar e analisar dados.
- Armazene os dados em um banco de dados ou datalake, prepare os dados, mova os dados selecionados para um data warehouse e execute os relatórios.
- Para o contexto, um Data Lake é:
  - Um data lake é um repositório centralizado que permite armazenar todos os seus dados estruturados e não estruturados em qualquer escala.
  - Você pode armazenar seus dados como estão, sem precisar primeiro estruturar os dados e executar diferentes tipos de análise, desde painéis e visualizações até processamento de big data, análise em tempo real e aprendizado de máquina para orientar melhores decisões.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/42b26d57-7985-479e-a4c4-d1efd6bff02b)


## O que é o Amazon Redshift?
### Amazon Redshift
Principais recursos:
- O Amazon Redshift é rápido e poderoso.
- O Amazon Redshift é um serviço de data warehouse totalmente gerenciado.
- Ele permite que você execute consultas analíticas complexas em petabytes de dados estruturados.
- O Amazon Redshift usa otimização de consulta sofisticada, armazenamento colunar em discos locais de alto desempenho e execução de consultas paralelas.

### Principais recursos do Amazon Redshift
- **Gerenciar** -> Data warehouse totalmente gerenciado
- **Criptografia** -> Criptografia dos seus dados em repouso e em trânsito
- **Compatível** -> Suporta linguagem de consulta estruturada padrão (SQL) e fornece conectores de alto desempenho para Java Database Connectivity (JDBC) e Open Database Connectivity (ODBC)


## Mecânica do processamento paralelo no Amazon Redshif
O processamento paralelo é um método de computação em que dois ou mais microprocessadores* estão simultaneamente desmontando programas e executando tarefas do programa simultaneamente.

## Casos de uso do Amazon Redshif
### Data warehouse corporativo (EDW)
- Migre a um ritmo confortável para os clientes
- Experimente sem grandes custos iniciais ou compromissos
- Responda mais rapidamente às necessidades empresariais

### Big data 
- Preço baixo para clientes pequenos
- Serviço gerenciado para facilidade de implantação e manutenção
- Concentre-se mais nos dados e menos no gerenciamento do banco de dados

### Software como serviço (SaaS) 
- Escale a capacidade do data warehouse à medida que a demanda cresce
- Adicione funcionalidade analítica a aplicativos
- Reduza os custos de hardware e software em uma ordem de magnitude


