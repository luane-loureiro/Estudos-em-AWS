# Computação sem Servidor (Serverless)
O termo “sem servidor” significa que o código é executado em servidores, sem que você precise provisionar ou gerenciar esses servidores. 
Com a computação sem servidor, você pode se concentrar na inovação de novos produtos e recursos em vez de manter servidores.
Outro benefício da computação sem servidor é a flexibilidade de dimensionar aplicações sem servidor automaticamente. 
A computação sem servidor pode ajustar a capacidade de aplicativos modificando as unidades de consumo, como taxa de transferência e memória. 

## AWS Lambda
O AWS Lambda é um serviço que permite a execução de códigos sem a necessidade de provisionar ou gerenciar servidores. 
Ao usar o AWS Lambda, você paga apenas pelo tempo de computação consumido. 
As cobranças se aplicam ao tempo em que o código fica em execução. 

Você pode executar códigos para praticamente qualquer tipo de aplicativo ou serviço de back-end sem a necessidade de qualquer gerenciamento. 
Por exemplo, uma função simples do Lambda é o redimensionamento automático de imagens com o upload feito na nuvem AWS. 
Nesse caso, a função é acionada ao fazer upload de uma nova imagem. 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/8046778b-6bf0-467f-868e-8345dce8ffbd)



### AWS Fargate
O AWS Fargate é um mecanismo de computação sem servidor para contêineres. Ele funciona com o Amazon ECS e o Amazon EKS. 

Com o AWS Fargate, você não precisa provisionar nem gerenciar servidores. 
O AWS Fargate gerencia sua infraestrutura de servidor para você. 
Você pode se concentrar em inovar e desenvolver seus aplicativos, pagando apenas pelos recursos necessários para executar os contêineres.

### Amazon Elastic Container Service (Amazon ECS)
O Amazon Elastic Container Service (Amazon ECS)(opens in a new tab) é um sistema de gerenciamento de contêineres altamente dimensionável e de alto desempenho que permite executar e dimensionar aplicações em contêineres na AWS. 
O Amazon ECS é compatível com os contêineres do Docker. 

O **Docker** é uma plataforma de software que permite criar, testar e implantar aplicações rapidamente. 
A AWS é compatível com c Docker Community Edition de código aberto e do Docker Enterprise Edition baseado em assinatura. 
Com o Amazon ECS, você pode usar chamadas de API para iniciar e interromper aplicativos ativados pelo Docker.

### Amazon Elastic Kubernetes Service (Amazon EKS)
O Amazon Elastic Kubernetes Service (Amazon EKS) é um serviço totalmente gerenciado que você pode usar para executar o Kubernetes na AWS. 

O **Kubernetes** é um software de código aberto que permite implantar e gerenciar aplicações em contêineres em grande escala. Uma grande comunidade de voluntários mantém o Kubernetes, e a AWS trabalha ativamente em conjunto com essa comunidade Kubernetes. Conforme novos recursos e funcionalidades são lançados para aplicativos Kubernetes, você pode facilmente aplicar essas atualizações aos aplicativos gerenciados pelo Amazon EKS.










