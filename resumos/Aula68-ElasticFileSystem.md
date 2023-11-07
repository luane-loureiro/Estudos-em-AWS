# Aula 69 - Elastic File System (EFS)

## Amazon Elastic File System (Amazon EFS)
O Amazon EFS é um armazenamento escalável, totalmente gerenciado e elástico do Network File System (NFS) para uso com serviços de nuvem da AWS e recursos locais.

### Amazon EFS
#### Recursos
- Sistema de arquivos em escala de petabytes e baixa latência
- Capacidade elástica
- Suporta NFS
- Compatível com todas as imagens de máquina da Amazon (AMIs) baseadas no Linux para Amazon Elastic Compute Cloud (Amazon EC2)

  ![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/b72d9afc-5a28-4fc7-b2e4-3b31c6c0878a)


### Benefícios do Amazon EFS
#### Elástica 
O armazenamento do Amazon EFS é simples, escalável e elástico.

#### Elasticidade dinâmica
O Amazon EFS foi criado para escalar elasticamente sob demanda, sem interromper os aplicativos. 
Os sistemas de arquivos do Amazon EFS crescem e diminuem automaticamente à medida que você adiciona e remove arquivos. Seus aplicativos têm o armazenamento de que precisam, quando precisam.

#### Totalmente gerenciado 
O Amazon EFS é um serviço gerenciado que facilita a configuração e o dimensionamento de armazenamento de arquivos na nuvem da AWS. 
É uma maneira fácil de criar um sistema de arquivos para big data e análise, fluxos de trabalho de processamento de mídia, gerenciamento de conteúdo, veiculação da Web e diretórios iniciais.


### Atributos de desempenho do Amazon EFS

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/f4ec5f5f-e7d7-46c7-8306-8dc6fedafdc4)


## Exemplo de arquitetura e configuração do Amazon EFS
O Amazon EFS oferece armazenamento de arquivos na nuvem. Com o Amazon EFS, você pode criar um sistema de arquivos, montar o sistema de arquivos em uma instância do EC2 e, em seguida, ler e gravar dados de e para o sistema de arquivos.
Você pode acessar o sistema de arquivos do Amazon EFS simultaneamente a partir de instâncias do EC2 na sua Amazon VPC, para que os aplicativos que escalam além de uma única conexão possam acessar um sistema de arquivos. 
As instâncias do EC2 executadas em várias zonas de disponibilidade dentro da mesma região da AWS podem acessar o sistema de arquivos para que muitos usuários possam acessar e compartilhar uma fonte de dados comum.


### Diagrama de arquitetura do Amazon EFS

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/2fec191d-7636-4ff1-8c83-1a6edad66643)


### Configuração do sistema de arquivos do Amazon EFS

1. Criar o sistema de arquivos do Amazon EFS.
2. Criar um destino de montagem na VPC da instância. Instância
3. Montar o sistema de arquivos no destino de montagem.
4. Conectar a instância do EC2 ao destino de montagem. 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/875c27c9-b08b-4e39-803f-8cb32667aa41)


## Implantação e recursos do Amazon EFS

### Lembre-se do diagrama de arquitetura do Amazon EFS

1. Crie seus recursos do Amazon EC2 e execute sua instância do EC2.
2. Crie um sistema de arquivos do Amazon EFS.
3. Crie suas montagens de destino nas sub-redes apropriadas.
4. Conecte suas instâncias do EC2 às montagens de destino.
5. Limpe recursos e proteja sua conta da AWS.

### Recursos do Amazon EFS
No Amazon EFS, o principal recurso é o sistema de arquivos. 
Cada sistema de arquivos tem propriedades como ID, token de criação, hora de criação, tamanho do sistema de arquivos em bytes, número de destinos de montagem criados para o sistema de arquivos e o estado do sistema de arquivos.

#### Alvos de montagem 
- ID da sub-rede Grupos de segurança
- Um ou mais por sistema de arquivos
- Criar em uma sub-rede VPC
- Uma por zona de disponibilidade
- As instâncias que desejam se conectar ao Amazon EFS devem estar na mesma VPC.

#### Tags
Para ajudar a organizar seus sistemas de arquivos, você pode atribuir seus próprios metadados a cada sistema de arquivos criado. Cada tag é um par de chave/valor.
Pense em destinos de montagem e tags como sub-recursos que existem somente se eles estiverem associados a um sistema de arquivos.


## Casos de uso do Amazon EFS
O Amazon EFS foi projetado para fornecer um desempenho para um amplo espectro de cargas de trabalho e aplicativos.

### Casos de uso do Amazon EFS
#### - Diretórios iniciais
O Amazon EFS pode fornecer armazenamento para organizações que têm muitos usuários que precisam acessar e compartilhar conjuntos de dados comuns.

#### - Sistema de arquivos para aplicações empresariais
O Amazon EFS fornece escalabilidade, elasticidade, disponibilidade e durabilidade para ser o armazenamento de arquivos para aplicativos corporativos e para aplicativos entregues como um serviço. 
A interface padrão do sistema de arquivos, as permissões do sistema de arquivos e a hierarquia de diretórios facilitam a migração de aplicativos corporativos de ambientes locais para a Nuvem AWS.

#### - Testes e desenvolvimento de aplicativos
O Amazon EFS fornece aos seus ambientes de desenvolvimento um repositório de armazenamento comum. Com um sistema de arquivos do Amazon EFS, você pode compartilhar código e outros arquivos de forma segura e organizada. 
O Amazon EFS oferece uma solução escalável e altamente disponível que funciona bem para cargas de trabalho de teste e desenvolvimento.

#### - Backups de bancos de dados
O Amazon EFS apresenta um sistema de arquivos padrão que pode ser facilmente montado com o NFSv4 a partir de servidores de banco de dados. 
Ele fornece uma maneira de criar backups de banco de dados portáteis com ferramentas de aplicativos nativos ou aplicativos de backup corporativos.

#### - Gerenciamento de conteúdo e serviços na Web
O Amazon EFS fornece um sistema de arquivos durável e de alta taxa de transferência para sistemas de gerenciamento de conteúdo que armazenam e veiculam informações para uma variedade de aplicativos, como sites, publicações on-line e arquivos.

#### - Fluxos de trabalho de mídia
Fluxos de trabalho de mídia — como edição de vídeo, produção em estúdio, processamento de transmissão.
design de som e renderização — geralmente dependem do armazenamento compartilhado para manipular arquivos grandes. 
Um modelo de consistência de dados robusto com alta taxa de transferência e acesso a arquivos compartilhados pode reduzir o tempo necessário para realizar esses trabalhos. 
Ele também pode consolidar vários repositórios de arquivos locais em um único local para todos os usuários.

#### - Análise de big data
O Amazon EFS fornece escala e desempenho para aplicativos de big data que exigem alta taxa de transferência para nós de computação. Ele também fornece consistência de leitura após gravação e operações de arquivo de baixa latência.
