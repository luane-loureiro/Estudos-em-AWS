# Aula 8 - Modelo de Responsabilidade Compartilhada da AWS

## Modelo de Responsabilidade Compartilhada
A segurança é a maior prioridade na AWS. A AWS oferece um ambiente de computação em nuvem dimensionável projetado para oferecer alta disponibilidade e confiabilidade, além de fornecer as ferramentas que permitem executar uma grande variedade de aplicativos.
Depois que o cliente começa a usar a AWS, a Amazon compartilha com ele a responsabilidade de proteger os dados dele na nuvem AWS, o que torna a segurança da AWS uma **responsabilidade compartilhada**. 

### Responsabilidade do Cliente:
- Dados do cliente
- Aplicativos, AWS Identity and Access Management (IAM)
- Sistema operacional, rede e configuração do firewall
- Criptografia e autenticação da integridade de dados no lado do cliente
- Criptografia no lado do servidor (sistema de arquivos ou dados)
- Proteção de tráfego de rede (criptografia/integrid ade/identidade)


### Responsabilidade da AWS
- Serviços fundamentais da AWS
    - Computação
    - Armazenamento
    - Banco de Dados
    - Redes
- Infra estrutura Global da AWS
    - Regiões 
    - Zonas de Disponibilidade
    - Locais de borda

## Responsabilidades de segurança da AWS: segurança DA nuvem
AWS é responsável por proteger a infraestrutura global que executa todos os serviços oferecidos na nuvem AWS, que incluem as Regiões, as Zonas de Disponibilidade e os locais de borda da AWS.
A proteção dessa infraestrutura é a prioridade número um da AWS. 
Não é possível visitar os data centers ou escritórios da AWS para conferir essa proteção pessoalmente.

- Segurança física dos data centers:
    - Acesso controlado e baseado em necessidades

- Infraestrutura de hardware e de software:
    - Desativação de armazenamento, registro em log de acesso ao sistema operacional do host e auditoria

- Infraestrutura de rede:
    – Detecção de intrusão
    - Infraestrutura de virtualização: Isolamento de instância


## Responsabilidades de segurança do cliente: segurança NA nuvem
Embora a infraestrutura de nuvem seja protegida e mantida pela AWS, os clientes são responsáveis pela segurança de tudo o que colocam na nuvem.
Os clientes retêm o controle da segurança que optam por implementar para proteger seus próprios dados, ambiente, aplicativos, configurações do AWS Identity and Access Management (IAM) e sistemas operacionais. Portanto, o modelo de responsabilidade compartilhada muda de acordo com os serviços da AWS usados pelo cliente.


- Sistema operacional da instância do Amazon Elastic Compute Cloud (Amazon EC2)
    * Incluindo aplicação de patches, manutenção
- Aplicativos
    * Senhas, acesso baseado em função e outros
- Configuração do security group
- Firewalls baseados em host ou no sistema operacional
    * Incluindo sistemas de prevenção ou detecção de intrusão
- Configurações de rede
- Gerenciamento de contas
    * Configurações de permissão e login para cada usuário

## Características do serviço e responsabilidade de segurança
### Infraestrutura como serviço (IaaS)
  Infraestrutura como serviço (IaaS) se refere a serviços que fornecem os componentes básicos para a TI em nuvem. Esses componentes básicos geralmente incluem a configuração de rede, os computadores (virtuais ou em hardware dedicado) e o espaço de armazenamento de dados. Os serviços de nuvem que podem ser caracterizados como IaaS fornecem ao cliente o mais alto nível de flexibilidade e controle de gerenciamento sobre recursos de TI
  
    *  O cliente tem mais flexibilidade em relação à configuração de rede e armazenamento
    *  O cliente é responsável por gerenciar mais aspectos da segurança
    *  O cliente configura os controles de acesso

### Plataforma como serviço (PaaS)
  Plataforma como serviço (PaaS) se refere a Serviços que reduzem a necessidade do cliente de gerenciar a infraestrutura subjacente (o hardware, o sistema operacional e outros recursos). 
  Os serviços de PaaS permitem que o cliente se concentre totalmente na implantação e no gerenciamento de aplicativos. 
  Os clientes não precisam se preocupar com a aquisição de recursos, o planejamento de capacidade, a manutenção de software ou a aplicação de patches.
  
    * O cliente não precisa gerenciar a infraestrutura subjacente
    * A AWS gerencia o sistema operacional, a aplicação de patches de banco de dados, a configuração do firewall e a recuperação de desastres (DR)
    * O cliente pode se concentrar no gerenciamento de código ou dados

### Software como serviço (SaaS) Exemplos de SaaS
Software como serviço (SaaS) se refere a serviços que fornecem software hospedado de maneira centralizada que geralmente pode ser acessado por meio de um navegador da web, de um aplicativo móvel ou de uma API. 
O modelo de licenciamento das ofertas de SaaS geralmente é de assinatura ou de pagamento conforme o uso. 
Com as ofertas de SaaS, os clientes não precisam gerenciar a infraestrutura que oferece suporte ao serviço. 

     * O software é hospedado de maneira centralizada.
     * Licenciado em um modelo de assinatura ou pagamento conforme o uso.
     * Os serviços normalmente são acessados por meio de um navegador da web, de um aplicativo móvel ou de uma API
     * Os clientes não precisam gerenciar a infraestrutura que oferece suporte ao serviço

