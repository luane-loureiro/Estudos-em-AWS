# Aula 69 - Amazon Simple Storage Service Glacier
## Amazon S3 Glacier
O Amazon S3 Glacier é uma classe de armazenamento segura, durável e de custo extremamente baixo do Amazon S3 para arquivamento de dados e backup de longo prazo.

## Conceitos do Amazon S3 Glacier
### Principais conceitos do Amazon S3 Glacier: arquivamento Conceitos de modelo de dados
****Arquivo:**** qualquer objeto (como foto, vídeo, arquivo ou documento) armazenado no Amazon S3 Glacier.
- Cada arquivo tem um endereço exclusivo. O formulário geral para endereços de arquivo é o seguinte:

```https://<region-specific endpoint>/<account-id>/vaults/<vault-name>/archives/<archive-id>```

Um exemplo de URI é: 

```https://glacier.us-west-2.amazonaws.com/111122223333/vaults/examplevault/archives/Nk....e1_EXAMPLEArchiveId```

### Principais conceitos do Amazon S3 Glacier: cofre Conceitos de modelo de dados
****Cofre :**** um contêiner para armazenar arquivos. Ao criar um cofre, você especifica o nome do cofre e a Região em que deseja que o cofre esteja localizado.
Um exemplo de URI: 

```https://glacier.us-west-2.amazonaws.com/111122223333/vaults/examplevault```

Explicação do exemplo de URI: 
```
- glacier.us-west-2.amazonaws.com identifica a região Oeste dos EUA (Oregon).
- 111122223333 é o ID da conta da AWS que possui o cofre.
- cofres refere-se à coleção de cofres pertencentes à conta da AWS.
- examplevault identifica um cofre específico na coleção de cofres.
```

### Principais conceitos do Amazon S3 Glacier: política de acesso ao cofre Conceitos de modelo de dados
- ****Política de acesso ao cofre:**** determina quem pode ou não acessar os dados armazenados no cofre. Também determina quais operações os usuários podem ou não realizar. Uma política de permissões de acesso ao cofre pode ser criada para cada cofre para gerenciar permissões de acesso para um cofre específico.
- Você também pode usar uma ****política de bloqueio de cofre**** para ajudar a garantir que um cofre não possa ser alterado. Cada cofre pode ter uma política de acesso ao cofre e uma política de bloqueio de cofre anexada a ele.

### Principais conceitos do Amazon S3 Glacier: trabalho Conceitos de modelo de dados
- ****Trabalho:**** os trabalhos do Amazon S3 Glacier podem realizar uma consulta selecionada em um arquivo, recuperar um arquivo ou obter um inventário de um cofre. Ao executar uma consulta em um arquivo, você inicia um trabalho que fornece uma consulta de linguagem de consulta estruturada (SQL) e uma lista de objetos de arquivamento do Amazon S3 Glacier.

### Amazon Glacier
#### Projetado paraSegurança,Durabilidade e Baixo Custo
- projetado para 11 9s de durabilidade para objetos
- Suporta criptografia Secure Sockets Layer (SSL)/Transport Layer Security (TLS) de dados em trânsito e em repouso
- O recurso vault lock impõe a conformidade por meio de uma política bloqueáve

## Acessando o Amazon S3 Glacier

- Serviços Web REST
- Kits de desenvolvimento de software (SDKs) Java ou .NET 
- Amazon S3 com políticas de ciclo de vida

### Acesso e recuperação do Amazon S3 Glacier para arquivos 
#### O Amazon S3 Glacier oferece três opções
Para manter os custos baixos, mas adequados para diferentes necessidades de recuperação, o Amazon S3 Glacier oferece três opções de acesso a arquivos. Essas opções variam de alguns minutos a várias horas. Eles são:

****- Acelerado**** — as recuperações aceleradas permitem o acesso aos seus dados rapidamente quando você recebe uma solicitação urgente ocasional de um subconjunto de arquivos. Exceto para os arquivos maiores (mais de 250 MB), os dados acessados por meio de recuperações expressas costumam ser disponibilizados entre 1 a 5 minutos. Os dois tipos de recuperações aceleradas são Capacidade sob demanda e provisionada . As solicitações sob demanda são semelhantes às instâncias sob demanda do Amazon EC2 e estão disponíveis na maioria das vezes. As solicitações de capacidade provisionada estarão disponíveis garantidamente quando você precisar delas.

****- Padrão**** — As recuperações padrão permitem que você acesse qualquer um dos seus arquivos em várias horas. Geralmente, as recuperações padrão são concluídas entre 3 e 5 horas. Essa é a opção padrão para solicitações de recuperação que não especificam a opção de recuperação.

****- Em massa**** — Recuperações em massa são a opção de recuperação de menor custo para o Amazon S3 Glacier. Você pode usá-las para recuperar grandes quantidades de dados — até mesmo petabytes — de forma econômica em um dia. Geralmente, as recuperações em massa são concluídas entre 5 e 12 horas.


## Armazenar dados e interagir com dados no Amazon S3 Glacier
Como o Amazon S3 Glacier armazena dados
- O Amazon S3 Glacier armazena dados em um arquivamento. –
      - Uma unidade básica de dados no Amazon Glacier (documento, vídeo, imagem etc.)
- Um cofre é uma coleção de arquivos.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/edc64b77-e39e-40e6-b501-902c15be8bf7)

### Maneiras de interagir com o Amazon S3 Glacier 
#### Interagir com o Amazon S3 Glacier usando:
***Políticas de ciclo de vida do Amazon S3***
- Os arquivos armazenados são acessados por meio do console do Amazon S3 ou da API do Amazon S3

***API do Amazon S3 Glacier***
- Adicionar arquivos diretamente 
- Para recuperar arquivos:
    1. Inicie uma solicitação de trabalho.
    2. Selecione a operação de recuperação de arquivamento.
    3. Opcionalmente, especifique um intervalo de datas ou um filtro de intervalo de bytes.
    4. Faça uma pesquisa para conclusão do trabalho ou receba uma notificação do Amazon Simple Notification (Amazon SNS).

### Políticas, criptografia e segurança com o Amazon S3 Glacier
#### Políticas de ciclo de vida do Amazon S3 
***As políticas permitem excluir ou mover objetos com base na idade.***
Você deve automatizar o ciclo de vida dos dados armazenados no Amazon S3. Usando políticas de ciclo de vida, você pode ter dados alternados em intervalos regulares entre diferentes tipos de armazenamento do Amazon S3. Ele reduz os custos gerais porque você paga menos pelos dados quando eles se tornam menos importantes com o tempo.
Além de definir regras de ciclo de vida por objeto, você também pode definir regras de ciclo de vida por bucket.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ea4850cb-aa0d-434d-8fa6-442aa945691f)

### Criptografia no lado do servidor 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/77193972-6bdd-4775-bed1-91c3e4e03e5b)

Outra diferença importante entre o Amazon S3 e o Amazon S3 Glacier é como os dados são criptografados. A criptografia do lado do servidor protege os dados em repouso. 
Com as duas soluções, você pode transferir seus dados com segurança por HTTP seguro (HTTPS). Todos os dados arquivados no Amazon S3 Glacier são criptografados por padrão. 
Com o Amazon S3, seu aplicativo deve iniciar a criptografia no lado do servidor. Esse tipo de criptografia pode ser realizado de várias maneiras:

****- A criptografia do lado do servidor**** com chaves de criptografia gerenciadas pelo Amazon S3 (SSE-S3) emprega criptografia multifator forte. O Amazon S3 criptografa cada objeto com uma chave exclusiva. Como proteção adicional, a própria chave é criptografada com uma chave mestra que é alterada regularmente. A criptografia no lado do servidor do Amazon S3 usa uma das cifras de bloco mais fortes disponíveis, o padrão de criptografia avançada de 256 bits (AES-256), para criptografar seus dados.

****- O AWS Key Management Service (AWS KMS)**** é um serviço que combina hardware e software seguros e altamente disponíveis para fornecer um sistema de gerenciamento de chaves dimensionado para a nuvem. O AWS KMS usa chaves mestras do cliente (CMKs) para criptografar seus objetos do Amazon S3. Você usa o AWS KMS por meio da seção Chaves de criptografia no console do AWS Identity and Access Management (IAM) ou por meio de APIs do AWS KMS. Você pode criar chaves de criptografia centralmente, definir as políticas que controlam como as chaves podem ser usadas e auditar o uso da chave para provar que elas estão sendo usadas corretamente. Você pode usar essas chaves para proteger seus dados em buckets do Amazon S3.

****- Usando a criptografia do lado do servidor com chaves de criptografia fornecidas pelo cliente (SS-EC)****, você pode definir suas próprias chaves de criptografia. Com a chave de criptografia que você fornece como parte da sua solicitação, o Amazon S3 gerencia a criptografia, à medida que grava em discos, e a descriptografia quando você acessa seus objetos.

### Segurança com o Amazon S3 Glacier 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4cbc9e91-3e7f-45af-810f-af3115a965e7)

# CONTINUA -->









