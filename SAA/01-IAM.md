# AWS IAM - Gerenciamento de Identidade e Acesso da AWS 

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
