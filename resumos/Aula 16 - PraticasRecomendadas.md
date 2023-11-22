# Aula 16 - Práticas recomendadas de segurança para criar uma conta da AWS
## Prática recomendada (1 de 4): dia um com a AWS
#### 1. Pare de usar o Usuário Raiz da conta AWS o mais rápido possivel
A AWS recomenda que, se você tiver chaves de acesso para o usuário raiz da sua conta, remova-as. Antes de remover as chaves de acesso, confirme se elas não estão sendo usadas em nenhum lugar dos aplicativos.
Parar de usar o usuário raiz da conta da AWS o mais rápido possível. Para parar de usar o usuário raiz da conta, siga as seguintes etapas: 
1. Com o usuário raiz da conta, crie um usuário do AWS Identity and Access Management (IAM) para você.
2. Crie um grupo do IAM:
   a) Dê ao grupo permissões totais de administrador.
   b)Adicione o usuário do IAM ao grupo.
3. Faça login com as credenciais de usuário do IAM.
4. Armazene as credenciais de usuário raiz da sua conta em um local seguro.
5. Se você tiver chaves de acesso de usuário raiz da conta, desative-as e remova-as.


## Prática recomendada (2 de 4): dia um com a AWS 
#### 2. Exija a autenticação multifator (MFA) para acesso.
1. Exija MFA para o usuário raiz da conta da AWS e para todos os usuários do IAM.
2. Use a MFA para controlar o acesso às interfaces de programação de aplicativo (APIs) de serviços da AWS.

**MFA de software** 
- MFA virtual da AWS
- Google Authenticator
- Authy Authenticator (aplicativo móvel do Windows)
- Notificação do serviço de mensagens curtas (SMS)


**MFA de hardware** 
- Forma de chaveiro ou cartão de exibição da Gemalto


## Prática recomendada (3 de 4): dia um com a AWS 
#### 3. Ative o AWS CloudTrail.
O CloudTrail registra todas as solicitações da interface de programação de aplicativo (API) para recursos em sua conta.
Veja como ativar o AWS CloudTrail:
1. Crie uma trilha:
    a) Dê um nome à trilha.
    b) Aplique a trilha em todas as regiões.
    c) Insira um nome para o novo bucket do Amazon Simple Storage Service (Amazon S3) no qual os logs serão armazenados.
   
2. Certifique-se de que o bucket do Amazon S3 que você usa para o CloudTrail tenha seu acesso restrito apenas àqueles que precisam de acesso, como administradores.

O CloudTrail agora está ativado por padrão para todos os usuários. Ele fornece visibilidade dos últimos sete dias de atividade da conta. Ele elimina a necessidade de configurar uma trilha no serviço para começar.


## Prática recomendada (4 de 4): dia um com a AWS 
#### 4. Ative um relatório de faturamento, como o AWS Cost and Usage Report:
Os relatórios de faturamento oferecem informações sobre seu uso dos recursos da AWS e os custos estimados para esse uso. A AWS fornece os relatórios para um bucket do S3 especificado por você e atualiza os relatórios pelo menos uma vez por dia.
O AWS Cost and Usage Report rastreia seu uso da AWS. O relatório fornece cobranças estimadas associadas à sua conta da AWS, por hora ou por dia.
Por exemplo, o AWS Cost and Usage Report rastreia seu uso da AWS. O relatório fornece cobranças estimadas associadas à sua conta da AWS, por hora ou por dia.

## Práticas Recomendadas do IAM 
- Exclua as chaves de acesso da conta (raiz) da AWS.
- Usuários do IAM
    - Crie usuários individuais do IAM.
    - Remova os usuários e as credenciais desnecessários.
- Use grupos para atribuir permissões a usuários do IAM.
- Funções do IAM
    - Use as funções para aplicativos que são executados em instâncias do Amazon EC2.
    - Delegue usando as funções em vez de compartilhar credenciais.
- Reforçar o controle de acesso
    - Conceda acesso com base no menor privilégio.
    - Configure uma política de senha forte.
    - Ative a MFA para usuários privilegiados.
    - Use as condições de política para segurança extra.
    - Alterne as credenciais regularmente.
    - Monitore a atividade em sua conta da AWS.

