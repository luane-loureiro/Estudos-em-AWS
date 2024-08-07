# Infra Estrutura Global da AWS
![image](https://github.com/user-attachments/assets/013febea-50f6-4e11-9a31-cff3bec96192)

- regiões
- Zonas disponibilidades
- AWS data center
- AWS Edge Location

## ambientes AWS
- Exemplos de Ambiente de serviços Globais
  - indentity Acess Management (IAM)
  - Route 53 (DNS Service)
  - CloudFront (Content Delivery NetWork)
  - WAF (Web Application Firewall)

- AWS Exemplo de Serviços de escopo de região
  - Amazon EC2 (infra estrutura as a service)
  - Elástic beanstalk (plataform as a service)
  - Lmabda (Function as a service)
  - Recognition (Softwaew as a service)
 
# AWS Identity and Acess Management (IAM) 
## IAM: User Group
- IAM = identity and acess Management, um serviço Global
- conta root criada por padrão, não deve ser usada ou compartilhada
- Os usuários são pessoas dentro da sua organização e podem ser agrupadas
- os grupos contem apenas usuários, nao podem conter outros grupos
- Os usuários não precisam pertencer a um grupo, e os usuários podem pertencer a vários grupos

![image](https://github.com/user-attachments/assets/d9ec3b31-526d-4c19-94a4-4d36bac8f29e)

<br>

## IAM - politica de senhas
- senhas fortes = maior segurança para sau conta.
- na aws você pode criar regas (policy) de uso de senhas
  - minimo de caracteres
  - tipos especificos de caracteres exigidos
    - incluir letras maiusculas
    - incluir letras minúsculas
    - númes
    - caracteres especiais
  - todos os usuarios do IAM devem trocar com regularidade suas senhas (password expiration)
  - todos os usuários podesm criar suas próprias senhas
  - não podem usar senhas repetidas
 
## MFA - multi factor Autenticator
- Os usuários tem acesso a sua conta e podem mudar configuraçoes ou apacar recursos na sua conta.
- você precisa proteger sua RootAccont e seus usuários IAM.
- MFA = password que vc criou + discpositivo de segurança
- Benefícios do MFA: se seu passowrd  for roubado ou hackeado, a sua acc não estara comprometida, pq ainda irão precisa do dispositivo de segurança

### Opções de dispositivos para MFA
- virtual MFA devices
    - google autenticator
    - Authy
- universal 2nd factor (u2f) security key
- haedwarw key fob MFA Device
- Hardware key fob MFA device for awsGovCloud (US)

## IAM - Funçôes para Serviços
- Alguns serviços da AWS precisarão executar algumas ações em seu nome
- para isso, atribuimos permições aos serviçõs da AWS com funções do IAM
- Funções comuns:
  - funções de instacias do EC2
  - Funções Lambda
  - Funções Cloud Formation
    
  ![image](https://github.com/user-attachments/assets/3dd49627-a637-4445-9d12-05fe3a58ea7d)

## IAM -  Diretrizes Prátoicas Recomendadas
- Não use a conta raiz, exeto para a configuração da conta da aws
- um usuário físico = um usuário da aws
- Atribuir usuários a grupos e atribuir permições a grupos
- criar uma política de senha forte
- usar um impor o uso de Mult Factor Authentication (MFA)
- Criar e usar fubnções para concender permições aos serviços da AWS
- Utilizar chaves de acesso para acessi Programático (CLI/SDK)
- Auditar permições de sua conta usando o relatório de credenciais do IAM e o IAM Access Advisor.
- Nunca Compartilhe usuários do IAM e chaves de acesso.

## IAM - Resumo 
- Usuários: Mapeando para um usuário físico, tem uma senha para o Console AWS
- Grupos: contém apenas usuários
- Políticas: Documentos JSON que descreve permições para usuários ou grupos
- Funções: para instâncias do EC2 ou serviço da AWS
- Segurança: MFA + Política de senha
- AWS CLI: Gerencie seus serviços da aws usando uma linha de comando
- AWS SDK:  gerencie seus serviços da AWS usando uma linguagem de programação
- Chaves de acesso: acesse a AWS usando a CLI ou SDK
- Auditoria: Relatórios de credenciais do IAM e IAM Acess Advisor.


![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fcfcc388-b389-42c6-901a-4dd7f79a7723)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ea30084b-d169-4ba7-95df-6712ecd3bb7e)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d95dc9b7-762c-4bdd-9266-2e9d2aa759b5)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/191cf507-e035-4987-980c-64a35ce028fb)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/058e5bb2-6f85-4e31-832a-2e06bd970365)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/77d8cdae-1c8c-4e7b-ab01-453331cc7022)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8223ad57-09b4-4aa3-ab1b-02b64fd4841d)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/3786ae2e-a145-4b2e-a57a-95b69ef6680d)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c9647fc9-7cd4-44fd-a1c8-d4701415eac4)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/66d4ffa8-e0e8-492c-8326-cf33d33bacf5)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/bf0121a4-1ac9-4d3e-970d-cf6110282065)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/94116186-f214-4578-b706-414ef1bb07c6)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8c7ec8e3-d540-495f-b7d1-4685c14c0a0f)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8bd40751-afe6-4326-b4b9-ffcebf2ce8dc)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/34ad6d8e-ea23-4a56-abc7-b48897e8e4a2)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1f8f2998-e881-40e7-8f76-3b5884e139dc)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c7ce53c1-012d-4699-bc46-7d0ea8ab3266)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/cc936781-0092-4757-9434-3a2a65c08a2b)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e9d07205-233c-48e1-be84-1d645a611243)



