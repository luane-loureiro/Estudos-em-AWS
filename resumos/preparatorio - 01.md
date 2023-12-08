

![Captura de tela 2023-11-16 202920](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/2fdb1f3a-c3d9-4484-aa57-0857be69115e)
![Captura de tela 2023-11-16 203010](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1dc9186d-da2a-42fd-8512-7e86f2e2c5a1)
![Captura de tela 2023-11-16 203051](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d340fe15-67fd-4b5c-8e78-c565000eb8f6)
![Captura de tela 2023-11-16 203301](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/2c551177-e996-493e-a9c7-3b697983baa1)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/f47ecf1a-121d-43fe-b231-b0f6fa8d2a9f)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/37d4ba9c-0473-4562-93dc-70c6bd473765)

## IaaS, PaaS e Saas

### Iaas 
Infra estrutura como serviço

### PaaS
Plataforma como serviço - ferramenta, plataforma, portal

### SaaS
Software como serviço - software pronto (ex: e-mail, sales force)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/7be5a9b2-4006-4034-99d0-b8ee75b00910)

### Exemplo
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/b826bc91-47ab-43fd-8d81-467779468076)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/1fd73166-8aa4-4e47-aa11-dc60ec9a431e)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/56d9e876-1e09-44b7-9512-34035a47d21e)


## infra estrutura global da AWS
Um região á disponibilização de uma coleção de recursos da AWS em uma localização deografica, sendo nele composto por um oou mais conjuntos de zonas de disponibilidade.
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/cf6dc02f-184e-4f4d-a91f-c492ed5fe819)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/6c437a58-3aca-4497-91a7-1a343a8cb9a8)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d844e03b-6cd1-4e96-bd48-754747f4f908)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/b8d6120a-5e2a-4f9e-bfde-f2b358ebd2d8)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/9437837d-81a6-4662-b595-9777fc096f56)

Um ponto de presença éuma infraestrutura de servidores, localizado prosimo de uma ZD, que armazena

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/56038b2c-a4cf-4364-973b-cf6e712e92af)


### dICAS PARA O EXAME

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/3bd32f62-156b-4a87-9126-02896a4fe75b)

- REGIÃO - é um conjuno de data centers em uma localização geográfica.
- Cda região possui um conjunto de zonas de disponibilidade
- ZD estão distintos a quilómetros de distâncian uma das outras, conectadas com alta velocidade, com seguramça loca, refrigeração (...)


![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8d25ae10-b187-4990-be88-c9a0ee8c8a78)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/abb3660d-c591-4083-a1c5-8de73267d010)

## recurso Gerenciados
 Um recurso gerenciado é como um serviço ou as configurações da camada anterior Não são admistradas pelo usuário

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/bda760c1-737f-45aa-8fa4-803d38463f21)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/4a4ff84b-e330-435d-b958-fcba4396d13c)
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/dbabf331-5cae-4f99-a9b0-ad2f6c288298)



### Dicas do exame
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ef8231c4-b35e-47fe-af7f-e7199ee9b326)


## well - Architected
principios gerais:
- pare de ficar advinhando a sua capacidade
- teste o seu produto em escala de produção
- 

- 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/2efe031f-a9c4-4adb-a6f8-b95ad5d1ba85)


### pricipios de design
- escalibilidade : vertical & Horizontal
- rescursos descartáveis: nada é para sempre
- Automação: serverless, IaaS, auto scaling
- lose couple: falhas não podem cascatear & não ao monolito
- serviços não servidores: será que não tem um serviço?

  ### seis pilares well architected
  ![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/24af26e8-9128-4bfd-ab69-050cf73e7f26)

  1. operacional exelent
  2. security
  3. reability
  4. performande efficiency
  5. cost Optimization
  6. Sustentabilidade: minimizar os impactos ambientais de excução da carga de trabalho na nuvem


![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/7294e860-b992-42f9-89fe-aa5c05ca2ee7)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/818b9bfb-d40f-47c1-9557-51d0e0aca590)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/5098ec95-32be-4422-aba6-bbaefe747b5e)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/feacef5e-a1e8-4dcb-8ed7-0e1456ea94a9)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/ab970920-3828-4415-9ec5-bd25eb5e6a63)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/a409d660-9a6d-4996-ae54-fe3571512f6a)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/b89361bf-fecb-4c34-9da3-262aa0d08d72)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/a20136c9-f07e-4ca6-b803-f939788a2e5e)










