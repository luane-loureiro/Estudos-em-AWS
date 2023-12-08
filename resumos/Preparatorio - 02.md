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
O AWS WAF é um firewall de aplicativos web que permitem especificar qual trafego tem o seu acesso permitido ou bloqueado, mediante a definição de regras personalizáveis.

### Caracteristicas
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/83e16b0d-7a04-403c-9c67-be4c213d82b8)

### Dicas do Exame
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/b5c4f030-eb41-440f-b705-89cd883b4653)

### Questão
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c8146659-f986-4547-96f5-9e9d56a5179d)

## AWS Shield standerd
### DDOS- distributed Denial of Service
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/c9a5c1b4-26df-46fa-80cb-42384eb07fae)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ef267711-7b05-4f46-b65a-8399493a1670)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/199926fa-188f-488b-a827-621dd2e63823)

### AWS Shield Advanced
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fe305cb3-6e4a-4d27-b853-94eb9dfbf03b)

### Dicas para o exame
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e7445d6a-8037-43cd-9115-1785de2590ab)


### Questões 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e28a6b26-551d-46d6-b6c1-7eb28dbbd804)


## Amazon cloud watch 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/296ee80a-bcf1-454a-9ca8-ace3f1629e96)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/bfda8440-b193-4743-a594-7f4a2387fa92)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/a6750e59-31a8-4a51-b6e1-dc7817062bf0)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/3b61fba0-d69c-403c-ad0e-c049d9b7e01e)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e86cc455-135b-4f77-9d81-2b8c083b058b)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/a34b0306-31fb-41a5-b729-3d87f24236c2)

### questão
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/abcca24a-369b-4906-bfb5-5d830bb1f70f)


## AWS CloudTrail
#### Definição
O AWS CloudTrail éum serviço que possibilita governaça, conformidade, auditoria operacional e auditoria de riscos em sua conta AWS.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/922ceff9-02e0-4f4c-9453-6eeffa46a6a7)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/f31a0306-729e-4c49-912e-12dc5847db97)

## AWS Config
fornece uma visualização detalhada dos recursos associados à sua conta da AWS, incluindo como eles são configurados, como eles se relacionam entre si e como as configurações e seus relacionamentos foram alterados ao longo do tempo. 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/0a02d016-5f78-440b-b933-290a6d7e9170)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d479a118-a1cd-4f4d-9580-e371146ecac3)


### Qustões

## AWS Organization

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/443dffdc-88e2-4944-a8e2-9e0530a1882b)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/6acbb7ef-3ba7-4e80-987c-3c08b6d710cc)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/347ef757-8b95-414e-aa5e-ed7866b72fce)


## AWS Artefacture
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/028c0fa8-1aa2-4d4a-bebd-2cc1782eefcd)

### Dicas de exame
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/cb3cdd20-48bf-462a-b29f-2b52fe3840c8)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4ffb7348-4bc7-4666-8862-df23784b2b0d)


## AWS Trust Avisor
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/68d83e09-9419-4a1b-abb4-e97798910372)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/53dc79ba-21c1-4f07-8f07-83cbd67ea7c6)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/2e753d78-8530-483d-8be7-ef4023b8929a)





