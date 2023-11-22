# preparatório 02
## responsabilidade compartilhada
Enquanro a que a AWS gerencia a segurança danuvem, você é reponsavel pela segurança na nuvem.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/bd897157-2071-4aee-84de-9335c201d80e)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/5914755b-3c16-409c-b42f-92f4ef406d8b)

### Questões

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4d7a12a0-d9de-4441-b0f6-2a6095b66efc)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/13fae368-11b3-4b74-9bfe-8f8df86f9abb)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/04fe0fd5-3306-4096-b33b-3d2200185ffc)


## AWS IAM
### Use, Groups & Roles
#### 👱 Usuários (users)
Pessoa ou serviuço, com credenciais permanentes **Não** compartilhe o usuário root & use o least privilege.

#### Grupos ( groups )
coletivo de usuários
Grupos não podem conter outros grupos

#### funções (roles)
Não são suas permições
éummétodo de autentificação temporária.


### Regras Básicas
**Autentificação** 
(usuários, grupos e funções)
➡️
**Autorização** 
(políticas & permições)

### Autorizar
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c18b2e4d-db7a-4042-93f1-d037c13101e8)


### API execution Statement
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/11f4634d-703c-4011-8162-34255b299bde)

### API Engine
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/40865095-a5c7-4a72-9413-86ab50236052)

### Dicas do Exame

- Usuários possuem credenciais permanentes e funções possuem credenciqais temporárias.
- Usuários **Não** devem ser compartilhados
- Use o leatest privilege Principle nos usuários
- Documentos JSON definem as permições de acesso
- Grupos podem contem outros usuários, mas não podem conter outros grupos

### Questões 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1d605499-abc2-418c-95d7-65a550947cb9)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4a14bb22-de7a-44a7-a5f2-6ccc5103a54a)


## AWS WAF - Web Application Firewall







