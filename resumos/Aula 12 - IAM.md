# Aula 12 - AWS Identity and Access Management (IAM) 
## IAM
O AWS Identity and Access Management (IAM) permite gerenciar o acesso aos serviços e recursos da AWS com segurança. Ao usar o IAM, você pode criar e gerenciar usuários e grupos da AWS (para auxiliar na autenticação) e usar permissões para permitir e negar acesso aos recursos da AWS (para auxiliar na autorização).
O IAM usa conceitos de controle de acesso que você já conhece, como usuários, grupos e permissões, para que seja possível especificar quais usuários podem acessar serviços específicos.

## O que é IAM?
AWS Identity and Access Management (IAM) Você pode gerenciar centralmente a autenticação e o acesso aos recursos da AWS. 
- Oferecido gratuitamente como um recurso da conta da AWS.
- Crie usuários, grupos e funções.
- Aplique políticas às entidades para controlar o acesso aos recursos da AWS.

#### Autenticação
Use o IAM para configurar a autenticação, que é a primeira etapa, pois isso controla quem pode acessar os recursos da AWS. O IAM é usado para autenticação de usuários e também é usado por aplicativos e outros serviços da AWS para acesso. 

#### Autorização
O IAM é usado para configurar a autorização, com base no usuário. A autorização determina quais recursos os usuários podem acessar e o que eles podem fazer com esses recursos ou como utilizá-los. 
A autorização é definida por meio do uso de políticas. Uma política é um objeto na AWS que, quando associado a uma identidade ou a um recurso, define suas permissões. 
O IAM reduz a necessidade de compartilhar senhas ou chaves de acesso ao conceder direitos de acesso a outras pessoas ou sistemas. Isso também facilita a ativação ou a desativação do acesso de um usuário. 
Use o IAM como uma ferramenta para gerenciar de forma centralizada o acesso referente a quem pode iniciar, configurar, gerenciar e terminar os recursos. 
Ele fornece controle granular sobre as permissões de acesso a usuários, sistemas ou outros aplicativos que podem fazer chamadas programáticas para outros recursos da AWS.

Use o IAM para realizar as seguintes tarefas:
- Gerencie os recursos que podem ser acessados e as ações que podem ser realizadas nos recursos. Por exemplo, quem tem permissões para terminar instâncias do Amazon Elastic Compute Cloud (Amazon EC2)?
- Defina as credenciais necessárias com base no contexto, como:
    - Quem pode acessar qual serviço da AWS?
    - O que o usuário ou o sistema tem permissão para fazer com o serviço?


## Acesso: Usuário Raiz da conta AWS em relação ao IAM
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/64ff65ee-7a47-4a5c-8fc8-eaafbde6ddd5)

#### Usuário Raiz da conta AWS
Ao criar uma conta da AWS pela primeira vez, você começa com uma identidade de login único. Essa entidade tem acesso completo a todos os serviços e recursos da AWS na conta e é chamada de usuário-raiz da conta da AWS. 
O usuário-raiz da conta é acessado ao fazer login com o endereço de e-mail e a senha usados para criar a conta.
Os usuários-raiz da conta da AWS têm acesso total a todos os recursos na conta. Você não pode controlar as permissões das credenciais de usuário-raiz da conta da AWS. 
Portanto, a AWS recomenda enfaticamente que você não use as credenciais de usuário-raiz da conta da AWS para interações do dia a dia com a AWS.

#### IAM
Use o IAM para criar usuários adicionais e atribuir permissões a eles, seguindo o princípio de privilégio mínimo. Com o IAM, é possível controlar com segurança o acesso de usuários em sua conta da AWS aos serviços e recursos da AWS. 
Por exemplo, se você precisar de permissões de nível de administrador, você pode: 
1. Criar um usuário do IAM.
2. Conceder acesso total a esse usuário.
3. Usar essas credenciais para interagir com a AWS.

Posteriormente, se você precisar revogar ou modificar suas permissões, poderá excluir ou modificar todas as políticas associadas a esse usuário do IAM.
Além disso, se houver vários usuários que exigem acesso à sua conta da AWS, você poderá criar credenciais exclusivas para cada usuário e definir quem tem acesso a quais recursos. Em outras palavras, você não precisa compartilhar credenciais. 
Por exemplo, você pode criar usuários do IAM com acesso somente leitura a recursos em sua conta da AWS e distribuir essas credenciais para usuários que exigem acesso de leitura


## Principio do Privilégio Mínimo
O princípio do menor privilégio é um conceito importante na segurança do computador: determine o que os usuários (e as funções) precisam fazer e, então, crie políticas que permitam que eles executem apenas essas tarefas.
Ao criar políticas do IAM, siga a prática de segurança padrão de conceder o menor privilégio. Ou seja, conceda apenas as permissões necessárias para realizar uma tarefa. 
Comece com um conjunto mínimo de permissões e conceda permissões adicionais conforme necessário. Fazer isso é mais seguro do que começar com permissões que são muito lenientes e tentar restringi-las posteriormente.

#### Prática recomendada
- O IAM permite que você siga o principio do menor privilégio.

#### O que Você deve Fazer
- Exclua chaves de acesso de usuário Raiz da conta.
- Crie um usuário IAM
- Conceda acesso de admistrador
- Ative a autenticaçâo multifator (MFA)
- Use credenciais do IAM para interagircoma AWS


## Tipos de Crecencias de Segurança
Cada conta da AWS tem um usuário raiz de conta atribuído. Esse usuário raiz da conta tem um endereço de e-mail atribuído para fins de comunicação e recuperação da conta.
No entanto, a AWS recomenda que você não use o usuário raiz da conta para tarefas diárias, mesmo administrativas. Em vez disso, siga as práticas recomendadas de uso do usuário raiz da conta e apenas o utilize para criar seu primeiro usuário do IAM. 
Depois, bloqueie com segurança as credenciais de usuário raiz da conta. Use-as somente quando você precisar executar as poucas tarefas de gerenciamento de contas e serviços que não podem ser realizadas de outras maneiras.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/cfb0c2d6-901c-4dff-85d0-49cd700bd0e2)


#### Quais são as duas maneiras de usar o IAM para acessar os serviços da AWS?
Você pode atribuir aos usuários dois tipos diferentes de acesso: acesso programático e acesso à console de gerenciamento da AWS.

#### Quais dois tipos de chaves são necessários para permitir que os usuários tenham acesso programático?
Um ID de chave de acesso e uma chave de acesso secreta são necessários para conceder acesso aos serviços da AWS.

## IAM: Autorização
- Permite que os usuários acessem os serviços da AWS concedendo autorização.
- Atribua permissões criando uma política do IAM.
- As permissões determinam quais recursos e operações têm uso permitido

Depois que um usuário for autenticado, ele deverá ser autorizado a acessar um serviço da AWS.
Para atribuir permissões a um usuário, um grupo ou uma função, você deve criar uma política do IAM. 
Uma política é um documento que lista as permissões explicitamente. Não há permissões padrão. Todas as ações são negadas por padrão (negação implícita), a menos que sejam explicitamente permitidas. 
Qualquer ação que você não permita explicitamente é negada. Todas as ações que você negar explicitamente serão sempre negadas.
  
Observação: o IAM é global. Não é de acordo com a região. Ele se aplica a todas as regiões AWS.


## MFA - Autentificação Multfator
- A autenticação multifator (MFA) oferece maior segurança.
- Além do nome de usuário e da senha, a MFA requer um código de autenticação exclusivo para acessar os serviços da AWS

Você pode acessar os serviços e recursos da AWS usando as seguintes ferramentas:
- Console de gerenciamento da AWS
- AWS Command Line Interface (AWS CLI)]
- Kits de Desenvolvimento de Software (SDKs) e interfaces de programação de aplicativo (APIs) de uma variedade de ambientes compatíveis

Para aumentar a segurança, a AWS recomenda ativar a MFA. Com a MFA, os usuários e os sistemas devem ser autenticados para que possam acessar os serviços e recursos da AWS. 
Duas opções são fornecidas para dispositivos de autenticação: dispositivos de hardware e aplicativos virtuais compatíveis com MFA (autenticação de dois fatores do Google Authenticator ou Authy). 
O Serviço de mensagens curtas (SMS) é outra alternativa de autenticação em que você usa seu dispositivo móvel que pode receber mensagens SMS para receber um código.
O AWS Security Token Service (AWS STS) é um serviço da web que também permite solicitar credenciais temporárias de permissão limitada para usuários do IAM ou para usuários autenticados.

## Usuários do IAM
- Uma entidade que você cria na AWS
- Oferece uma maneira de interagir com a AWS
- Nenhuma credencial de segurança padrão para usuários do IAM
- Pode representar pessoas ou aplicativos

Um usuário do IAM é uma entidade criada na AWS que fornece uma maneira de interagir com a AWS. Um usuário do IAM fornece principalmente identidades aos indivíduos que eles podem usar para fazer login no console e fazer solicitações aos serviços da AWS.
Um usuário do IAM é somente uma identidade com permissões associadas. Você pode criar um usuário do IAM para representar um aplicativo que precisa de credenciais para fazer solicitações à AWS. Um aplicativo pode ter sua própria identidade em sua conta e seu próprio conjunto de permissões, da mesma forma que os processos têm suas próprias identidades e permissões em um sistema operacional, como Microsoft Windows ou Linux.


## Grupos do IAM
Um grupo é um conjunto de usuários do IAM. Os grupos permitem especificar permissões para um conjunto de usuários, o que pode facilitar o gerenciamento das permissões para esses usuários. 
Por exemplo, você pode ter um grupo chamado Desenvolvedores e fornecer a esse grupo os tipos de permissões que os desenvolvedores normalmente precisam. 
Qualquer usuário nesse grupo tem automaticamente as permissões atribuídas ao grupo. Se um novo usuário ingressar na sua organização e tiver permissões de desenvolvedor, adicione esse usuário ao grupo Desenvolvedores. 
Isso concede automaticamente a esses usuários as permissões apropriadas. Da mesma forma, se uma pessoa mudar de cargo em sua organização, em vez de editar as permissões desse usuário, você poderá removê-lo do grupo anterior e adicioná-lo ao novo grupo.

#### Características importantes dos grupos:
- Um grupo pode conter vários usuários, e um usuário pode pertencer a vários grupos.
- Os grupos não podem ser aninhados. Eles podem conter apenas usuários, não outros grupos.
- Não há um grupo padrão que inclua automaticamente todos os usuários na conta da AWS. Se você quiser ter um grupo padrão, é preciso criá-lo e atribuir cada novo usuário.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1366c5ba-4994-4b9c-aa31-52991d8683a4)

Um grupo do IAM é um conjunto de usuários do IAM. 
- Coleção de usuários do IAM
- Sem grupos padrão
- Os grupos não podem ser aninhados
- Os usuários podem pertencer a vários grupos
  
Você pode:
- Especificar permissões para todo o grupo
- Definir permissões usando políticas do IAM

## Funções do IAM
- Usadas para delegar acesso a recursos da AWS
- Fornecem acesso temporário
- Permissões
        - Definidas usando políticas do IAM
        - Anexadas à função, não a um usuário ou grupo do IAM

Uma função é uma ferramenta para conceder acesso temporário aos recursos da AWS em sua conta da AWS. As permissões não são anexadas a um usuário ou grupo do IAM. Em vez disso, no tempo de execução, os aplicativos ou serviços da AWS podem assumir uma função de uma forma programática. Quando uma função é atribuída, a AWS retorna credenciais de segurança temporárias que o usuário ou aplicativo pode usar para fazer solicitações programáticas à AWS. 

#### Casos de uso
Um caso de uso para usar funções é com usuários federados. Um usuário federado não tem uma identidade permanente em uma conta da AWS da mesma forma que um usuário do IAM. Para atribuir permissões a um usuário federado, você pode criar uma entidade de função.

#### Criar funções 
Você cria uma função na conta da AWS que contém os recursos aos quais você deseja permitir acesso. Ao criar a função, especifique duas políticas:
- A política de confiança especifica quem tem permissão para assumir a função, como o principal ou a entidade confiável.
  
- A política de acesso (ou permissões) define quais ações e recursos o principal tem permissão para usar. O principal pode ser:
    - Conta da AWS
    - Serviço da AWS (como Amazon Elastic Compute Cloud ou Amazon EC2)
    - Provedor de Security Assertion Markup Language (SAML) 
    - Provedor de identidade (IdP) que pode incluir Login with Amazon, Facebook ou Google.

O principal também pode ser um usuário, um grupo ou uma função do IAM de outras contas da AWS, incluindo as que não são suas.


## Permições do IAM
#### Como o IAM Determina Permições
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e412d713-986a-42df-b7bb-e58eb16cb3ce)

Com o uso das políticas, você pode ajustar as permissões concedidas a usuários, grupos e funções do IAM. Como as políticas são armazenadas no formato JavaScript Object Notation (JSON), você pode usá-las com um sistema de controle de versão. 
É uma prática recomendada definir o acesso de privilégio mínimo para cada usuário, grupo ou função. Assim, você pode personalizar o acesso a recursos específicos usando uma política de autorização.
Quando você determina se as permissões são concedidas, o IAM primeiro verifica se há uma política de negação explícita. Se não houver, ele vai então conferir se há uma política de permissão explícita. 
Caso não haja uma política de permissão nem de negação explícita, o IAM reverterá para o padrão: negação implícita.


## Políticas do IAM
Uma política do IAM é uma declaração formal de uma ou mais permissões. As políticas podem ser anexadas a qualquer entidade do IAM, o que inclui um usuário, um grupo, uma função ou um recurso. 
As políticas especificam quais ações são permitidas, em quais recursos permitir as ações e qual será o efeito quando o usuário solicitar acesso aos recursos.
A ordem em que as políticas são avaliadas não tem efeito no resultado da avaliação. Todas as políticas são avaliadas, e o resultado é sempre que a solicitação é permitida ou negada. Quando há um conflito, a política mais restritiva prevalece.

#### Tipos de políticas do IAM
- As **políticas baseadas em identidade** são políticas de permissões que você pode anexar a um principal ou uma identidade, como um usuário, uma função ou um grupo do IAM. Essas políticas controlam quais ações essa identidade pode realizar, em quais recursos e em que condições. As políticas baseadas em identidade podem ser categorizadas como:
    - **Políticas gerenciadas:** políticas independentes baseadas em identidade que você pode anexar a vários usuários, grupos e funções em sua conta da AWS
    - **Políticas em linha:** políticas que você cria e gerencia e que são incorporadas diretamente em um único usuário, grupo ou função

- As **Políticas com base em recursos** são documentos de política JSON anexados a um recurso, como um bucket do Amazon Simple Storage Service (Amazon S3). Essas políticas controlam quais ações uma entidade principal pode realizar nesse recurso e em quais condições. As políticas baseadas em recurso são políticas em linha. Não há políticas baseadas em recurso gerenciadas. 


#### Uma política do IAM é uma declaração formal de uma ou mais permissões.
- Anexe uma política a qualquer entidade do IAM, como usuário, grupo ou função.
- As políticas autorizam as ações que podem, ou não, ser executadas pela entidade.
- Uma única política pode ser anexada a várias entidades.
- Uma única entidade pode ter várias políticas anexadas.

***Prática recomendada*** Ao anexar a mesma política a vários usuários do IAM, coloque os usuários em um grupo e anexe a política ao grupo.

## IAM: Atribuição de Política:
Você pode atribuir a mesma política a um usuário do IAM, um grupo do IAM e funções do IAM. Isso permite a reutilização e reduz a necessidade de recriar a mesma política para identidades diferentes.
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c71cb388-ccb4-46b0-9f20-2988bcb576a0)

