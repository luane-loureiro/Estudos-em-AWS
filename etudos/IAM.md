# Serviços Adicionais da AWS para IAM
Os seguintes serviços da AWS também podem ser usados ​​para proteger credenciais, fornecer federação de usuários e gerenciar e proteger centralmente várias contas da AWS. 

### AWS Secrets Manager
O AWS Secrets Manager foi projetado para gerenciar centralmente segredos usados ​​para acessar recursos na AWS, no local e serviços de terceiros. Os segredos podem ser credenciais de banco de dados, senhas, chaves de API de terceiros e até mesmo texto arbitrário. Com o Secrets Manager, você pode substituir credenciais codificadas no seu código por uma chamada de API para o Secrets Manager para recuperar o segredo programaticamente. Além disso, você pode configurar o Secrets Manager para girar automaticamente o segredo para você de acordo com uma programação que você especificar.

![image](https://github.com/user-attachments/assets/067dd775-0d44-46ea-b07b-c5dfa95742cb)
<hr>

### AWS IAM Identity Center
O AWS IAM Identity Center é um serviço de logon único (SSO) na nuvem que fornece o gerenciamento central do acesso SSO a várias contas da AWS e aplicativos comerciais. Os usuários podem fazer login em um portal do usuário com suas credenciais corporativas existentes e acessar todas as suas contas e aplicativos atribuídos de um só lugar. O IAM Identity Center inclui integrações SAML integradas a muitos aplicativos comerciais. Ele pode ser integrado ao Microsoft Active Directory, o que significa que seus funcionários podem fazer login no seu portal do usuário usando suas credenciais corporativas do Active Directory.
<hr>

### AWS Security Token Service (STS)
O AWS Security Token Service (STS) é um serviço web que lhe dá a capacidade de solicitar credenciais temporárias de privilégio limitado para usuários do IAM que estão assumindo uma função diferente ou para usuários que estão sendo federados. Um cenário em que alguém, ou algo, precisa de acesso à sua conta para executar uma tarefa específica que não é feita diariamente seria um ótimo candidato para credenciais temporárias.

![image](https://github.com/user-attachments/assets/5920d701-7075-41c1-a382-6628da0aca44)
<hr>

### AWS Managed Microsoft AD
O AWS Directory Service for Microsoft Active Directory, também conhecido como AWS Managed Microsoft AD, permite que suas cargas de trabalho de domínio e recursos da AWS usem o Active Directory gerenciado na Nuvem AWS. O AWS Managed Microsoft AD é criado no Microsoft Active Directory real e não exige que você sincronize ou replique dados do seu Active Directory existente para a nuvem.

![image](https://github.com/user-attachments/assets/862a90b4-a3b8-413f-a14d-946830bef53a)

<hr>

### AWS Organizations
Com o AWS Organizations, você pode gerenciar e aplicar políticas centralmente para várias contas da AWS. Este serviço permite agrupar contas em unidades organizacionais (OUs) e usar políticas de controle de serviço para controlar centralmente os serviços da AWS em várias contas da AWS. Com o Organizations, você pode automatizar a criação de novas contas por meio de APIs. Você também pode agilizar o faturamento configurando um único método de pagamento para todas as contas da sua organização por meio do faturamento consolidado. O Organizations está disponível para todos os clientes da AWS sem custo adicional. 

![image](https://github.com/user-attachments/assets/f13d748d-7d51-40c5-9d91-c4480bad38d3)
