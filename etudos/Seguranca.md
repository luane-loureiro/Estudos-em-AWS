# segurança
## Modelo de responsabilidade compartilhada da AWS
Quem é responsável por manter seus recursos seguros: você (o cliente) ou AWS?

A resposta é ambos. Isso é porque você não trata seu ambiente AWS como um único objeto. Em vez disso, você trata o ambiente como uma coleção de partes que se combinam. A AWS é responsável por algumas partes do seu ambiente e você (o cliente) é responsável por outras. Esse conceito é conhecido como modelo de responsabilidade compartilhada(opens in a new tab).

O modelo de responsabilidade compartilhada divide-se em responsabilidades do cliente (chamadas de “segurança na nuvem”) e responsabilidades da AWS (chamadas de “segurança da nuvem”).

| Entidade responsável | Parte do ambiente da AWS |
|----------------------|--------------------------|
| | Dados do cliente |
| | Plataforma, aplicações, Identity and Access Management (IAM) |
|  Cliente	| Configuração de sistemas operacionais, rede e firewall |
| |Criptografia de dados no lado do cliente, criptografia de dados no lado do servidor e proteção de tráfego de rede |
| Amazon Web Services (AWS) | Software: computação, armazenamento, banco de dados, rede | 
| | Hardware: Regiões, Zonas de Disponibilidade, locais de borda |


### Clientes: Segurança na nuvem
- Os clientes são responsáveis pela segurança de tudo o que criam e colocam na nuvem AWS.
- Ao usar os serviços da AWS, você, o cliente, mantém controle total sobre seu conteúdo. Você é responsável por gerenciar os requisitos de segurança para seu conteúdo, incluindo qual conteúdo você escolhe armazenar na AWS, quais serviços AWS você usa e quem tem acesso a esse conteúdo. Você também controla como os direitos de acesso são concedidos, gerenciados e revogados.
- As etapas de segurança que você executar dependem de fatores como os serviços que usa, a complexidade de seus sistemas e as necessidades operacionais e de segurança específicas de sua empresa. As etapas são seleção, configuração e aplicação de patches nos sistemas operacionais que serão executados nas instâncias do Amazon EC2, configuração de grupos de segurança e gerenciamento de contas de usuário. 

### AWS: Segurança da nuvem
- A AWS é responsável pela segurança da nuvem.
- A AWS opera, gerencia e controla os componentes em todas as camadas da infraestrutura. Isso inclui áreas como o sistema operacional do host, a camada de virtualização e até mesmo a segurança física do data center no qual o serviço opera.
- A AWS é responsável pela proteção da infraestrutura global que executa todos os serviços oferecidos na nuvem AWS. A infraestrutura inclui Regiões AWS, Zonas de Disponibilidade e locais de borda.
- A AWS gerencia a segurança da nuvem, especificamente a infraestrutura física que hospeda seus recursos, que incluem:
    - Segurança física dos data centers
    - Infraestrutura de hardware e software
    - Infraestrutura de rede
    - Infraestrutura de virtualização
      
- Embora você não possa visitar os data centers da AWS para ver essa proteção pessoalmente, a AWS oferece vários relatórios de auditores terceirizados. Esses auditores verificaram a conformidade com diversas normas e regulamentações de segurança da computação.


## Permissões de usuário e acesso
### AWS Identity and Access Management (IAM)

O AWS Identity and Access Management (IAM)(opens in a new tab) permite que você gerencie o acesso aos serviços e recursos da AWS com segurança.  
O IAM oferece a flexibilidade de configurar o acesso com base nas necessidades operacionais e de segurança específicas da sua empresa. 
Você pode fazer isso usando uma combinação dos recursos do IAM, que vamos conhecer melhor nesta lição:
- Usuários, grupos e perfis do IAM
- Políticas do IAM
- Autenticação multifator

Você também conhecerá as práticas recomendadas para cada um desses recursos.

### Usuário-raiz da conta AWS
Ao criar uma conta AWS pela primeira vez, você começa com uma identidade conhecida como usuário-raiz(opens in a new tab). 
O usuário-raiz é acessado ao entrar com o endereço de e-mail e a senha usados para criar a conta AWS. 
Pense no usuário-raiz como sendo parecido com o proprietário da cafeteria: Ele tem acesso completo a todos os serviços e recursos AWS na conta.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/a3ada0da-3b73-40f1-bb37-1aaeccc67cfd)

#### Prática recomendada:
- não use o usuário-raiz para tarefas cotidianas.
- Em vez disso, use o usuário-raiz para criar seu primeiro usuário do IAM e atribua a ele permissões para criar outros usuários.
- Em seguida, continue a criar outros usuários do IAM e acesse essas identidades para executar tarefas comuns em toda a AWS.
- Use o usuário-raiz somente quando precisar executar um número limitado de tarefas disponíveis somente para o usuário-raiz. Exemplos dessas tarefas são a alteração do endereço de e-mail do usuário-raiz e a alteração do plano do AWS Support. 


### Usuários do IAM
Um usuário do IAM é uma identidade que você cria na AWS. 
Ele representa a pessoa ou o aplicativo que interage com os serviços e recursos AWS. Consiste em um nome e credenciais.
Por padrão, ao criar um novo usuário do IAM na AWS, não há permissões associadas a ele. 
Para permitir que o usuário do IAM execute ações específicas na AWS, como iniciar uma instância do Amazon EC2 ou criar um bucket do Amazon S3, você deve conceder ao usuário do IAM as permissões necessárias.

#### Prática recomendada:
- recomendamos que crie usuários individuais do IAM para cada pessoa que precisa acessar a AWS.
- Mesmo que você tenha vários funcionários que precisem do mesmo nível de acesso, você deve criar usuários individuais do IAM para cada um deles.
- Isso fornece segurança adicional, permitindo que cada usuário do IAM tenha um conjunto exclusivo de credenciais de segurança.

### Políticas do IAM
Uma política do IAM é um documento que concede ou nega permissões para serviços e recursos AWS.  
As políticas do IAM permitem que você personalize os níveis de acesso dos usuários aos recursos. Por exemplo, você pode permitir que os usuários acessem todos os buckets do Amazon S3 em sua conta AWS ou apenas um bucket específico.

#### Prática recomendada:
- siga o princípio de segurança de menor privilégio ao conceder permissões.
- Seguindo esse princípio, você ajuda a impedir que usuários ou perfis tenham mais permissões do que o necessário para executar as tarefas.
- Por exemplo, se um funcionário precisar acessar apenas um bucket específico, especifique o bucket na política do IAM. Faça isso em vez de conceder ao funcionário acesso a todos os buckets em sua conta AWS.

### Grupos do IAM
Um grupo do IAM é um conjunto de usuários do IAM. 
Quando você atribui uma política do IAM a um grupo, todos os usuários do grupo recebem permissões especificadas pela política.
Veja um exemplo de como isso pode funcionar na cafeteria. 
Em vez de atribuir permissões aos operadores um de cada vez, o proprietário pode criar o grupo “operadores de caixa” do IAM. O proprietário pode, em seguida, adicionar usuários do IAM ao grupo e anexar permissões no nível do grupo. 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/782cf6d5-7f75-4acc-9b55-59b4cca268fc)

### Perfis do IAM (IAM Rules)
Na cafeteria, um funcionário se reveza em diferentes estações de trabalho ao longo do dia. 
Dependendo do tamanho da equipe da cafeteria, esse funcionário pode desempenhar várias tarefas: trabalhar na caixa registradora, atualizar o sistema de inventário, processar pedidos on-line e assim por diante. 
Quando o funcionário precisa alternar para uma tarefa diferente, ele abre mão do acesso a uma estação de trabalho e ganha acesso à próxima estação. 
O funcionário pode alternar facilmente entre estações de trabalho, mas, a qualquer momento, ele pode ter acesso a uma única estação de trabalho. 
Esse mesmo conceito existe na AWS com os perfis do IAM.
Um perfil do IAM é uma identidade que você pode assumir para obter acesso temporário a permissões.  
Antes que um usuário, aplicação ou serviço do IAM possa assumir um perfil do IAM, ele precisa receber permissões para alternar para o perfil. 
Quando alguém assume uma função do IAM, ele abandona todas as permissões anteriores que tinha em uma função anterior e assume as permissões da nova função. 

### Autenticação com multifator
Você já entrou em um site que exigia várias informações para verificar sua identidade? Talvez tenha sido necessário digitar sua senha e, em seguida, uma segunda forma de autenticação, como um código aleatório enviado para o telefone. 
Este é um exemplo de autenticação multifator(opens in a new tab).
No IAM, a autenticação multifator (MFA) é uma camada extra de segurança para sua conta AWS.















