# Redes
## Conectividade com a AWS
### Amazon VPC (virtual private cloud)
O Amazon VPC permite que você provisione uma seção isolada da nuvem AWS. 
Por padrão sem conectividade com a internte.
Nessa seção isolada, você pode executar os recursos em uma rede virtual que definir. 
Em uma Virtual Private Cloud (VPC), você pode organizar seus recursos em **sub-redes**. 
Uma sub-rede é uma seção de uma VPC que pode conter recursos como instâncias do Amazon EC2.

### Gateway de internet
Para permitir que o tráfego público da internet acesse sua VPC, é preciso anexar um gateway de internet à VPC.
O gatway é um portão de acesso a internte publica, seja para entrada ou saidade de dado.
Um gateway da internet é uma conexão entre uma VPC e a internet. Você pode pensar em um gateway da internet como sendo semelhante a uma porta que os clientes usam para entrar na cafeteria. 
Sem um gateway da internet, ninguém pode acessar os recursos em sua VPC

### Gateway privado virtual
Para acessar recursos privados em uma VPC, use um gateway privado virtual. 
Veja um exemplo de como um gateway privado virtual funciona. Você pode pensar na internet como o caminho entre sua casa e a cafeteria. 
Suponha que você está viajando com um guarda-costas para proteção. Você ainda usa o mesmo caminho que outros clientes, mas com uma camada extra de proteção. 
O guarda-costas é como uma conexão de rede privada virtual (VPN) que criptografa (ou protege) seu tráfego de internet de todas as outras solicitações ao redor. 
O gateway privado virtual é o componente que permite que o tráfego protegido da internet ingresse na VPC. 
Mesmo que sua conexão com a cafeteria tenha proteção extra, os engarrafamentos são possíveis porque você usa o mesmo caminho que outros clientes. 
Um gateway privado virtual permite estabelecer uma conexão VPN (rede privada virtual) entre a VPC e uma rede privada, como um data center on-premises ou uma rede corporativa interna. 
Um gateway privado virtual permitirá o tráfego na VPC somente se ele for proveniente de uma rede aprovada.

### AWS Direct Connect
É um serviço que permite estabelecer uma conexão privada dedicada entre seu data center e uma VPC.  
Suponha que haja um prédio com um corredor que o liga diretamente à cafeteria. Somente os moradores do prédio podem passar por esse corredor. 
Esse corredor privado estabelece o mesmo tipo de conexão dedicada que o AWS Direct Connect. Os moradores conseguem entrar na cafeteria sem precisar usar a estrada pública compartilhada com outros clientes. 
A conexão privada do AWS Direct Connect ajuda a reduzir os custos de rede e a aumentar a quantidade de largura de banda que pode trafegar pela rede.


## Sub-redes e listas de controle de acesso à rede
Para saber mais sobre a função das sub-redes em uma VPC, veja o exemplo da cafeteria a seguir.
Primeiro, os clientes fazem os pedidos ao operador de caixa. O operador de caixa, em seguida, passa os pedidos para o barista. Esse processo permite que a fila prossiga sem problemas à medida que mais clientes entram. 
Suponha que alguns clientes tentem furar a fila do caixa e fazer os pedidos diretamente ao barista. Isso interrompe o fluxo de tráfego e faz com que os clientes acessem uma parte da cafeteria que é restrita a eles.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/0921608b-3130-4c76-8065-76f6be4a12f7)

Para corrigir isso, os proprietários da cafeteria dividem a área do balcão colocando o operador de caixa e o barista em estações de trabalho separadas. A estação de trabalho do operador de caixa é voltada para o público e projetada para receber clientes. A área do barista é privada. O barista ainda pode receber pedidos do operador de caixa, mas não diretamente dos clientes.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/cf6c30e1-55d1-40e8-9d05-3dc47db1001d)

Isso é semelhante à forma como você pode usar os serviços de redes da AWS para isolar recursos e determinar exatamente como o tráfego de rede flui.
Na cafeteria, você pode pensar na área do balcão como uma VPC. A área do balcão divide-se em duas áreas separadas para a estação de trabalho do operador de caixa e para a estação de trabalho do barista. Em uma VPC, sub-redes são áreas separadas usadas para agrupar recursos.

### Sub-redes
É uma seção de uma VPC na qual você pode agrupar recursos com base em necessidades operacionais ou de segurança. As sub-redes podem ser públicas ou privadas. 
**Sub-redes públicas** contêm recursos que precisam ser acessíveis ao público, como o site de uma loja on-line.
**As sub-redes privadas** contêm recursos que devem ser acessíveis apenas pela sua rede privada, como um banco de dados que contém informações pessoais dos clientes e históricos de pedidos. 
Em uma VPC, as sub-redes podem se comunicar entre si. Por exemplo, um aplicativo que envolve instâncias do Amazon EC2 em uma sub-rede pública que se comunicam com bancos de dados localizados em uma sub-rede privada.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/f29ca690-627c-4dbd-a0b0-351c024a8c44)

### Tráfego de rede em uma VPC
Quando um cliente solicita dados de um aplicativo hospedado na nuvem AWS, essa solicitação é enviada como um pacote. Um pacote é uma unidade de dados enviada pela internet ou por uma rede. 
Ele entra em uma VPC por um gateway de internet. Antes de um pacote poder entrar em uma sub-rede ou sair de uma sub-rede, ele verifica se há permissões. Essas permissões indicam quem enviou o pacote e como ele tenta se comunicar com os recursos em uma sub-rede.
O componente da VPC que verifica as permissões de pacotes das sub-redes é uma **lista de controle de acesso (ACL)** de rede(opens in a new tab).

### ACLs de rede
É um firewall virtual que controla o tráfego de entrada e saída no nível de sub-rede.
Imagine que você está em um aeroporto. No aeroporto, os viajantes estão tentando entrar em outro país. 
Você pode pensar nos viajantes como pacotes e no oficial de controle de passaportes como uma ACL de rede. 
O oficial de controle de passaportes verifica as credenciais dos viajantes quando entram e saem do país. Se um viajante estiver em uma lista aprovada, ele poderá passar. 
No entanto, se ele não estiver na lista aprovada ou estiver explicitamente em uma lista de viajantes proibidos, ele não poderá entrar.
Cada conta AWS tem uma ACL de rede-padrão. Ao configurar sua VPC, você pode usar a ACL de rede comum da sua conta ou criar ACLs de rede personalizadas. 
Por padrão, **a ACL-padrão de rede da conta permite todo o tráfego de entrada e saída**, mas você pode adicionar suas regras. Para ACLs de rede personalizadas, todo o tráfego de entrada e saída é negado até que você adicione regras para especificar qual tráfego permitir. Além disso, todas as ACLs de rede têm uma regra de negação explícita. Essa regra garante que, se um pacote não corresponder a nenhuma das outras regras na lista, ele será negado. 

### Filtragem de pacotes stateless
As ACLs de rede executam a filtragem de pacotes stateless. **Elas não se lembram de nada e verificam os pacotes que atravessam a fronteira** da sub-rede em todos os sentidos: entrada e saída. 
Lembre-se do exemplo anterior de um viajante que quer entrar em outro país. Isso se parece com o envio de uma solicitação de uma instância do Amazon EC2 para a internet.
Quando a resposta de pacote da solicitação volta para a sub-rede, a ACL de rede não se lembra da solicitação anterior. A ACL de rede verifica a resposta do pacote em relação à lista de regras para determinar se permite ou nega.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/db358824-01fa-4aa5-8610-55f5233654bd)

Depois que um pacote entra em uma sub-rede, é necessário verificar as permissões dele nos recursos da sub-rede, como as instâncias do Amazon EC2. 

### Grupos de segurança (security group)
Um grupo de segurança é um firewall virtual que controla o tráfego de entrada e saída de uma instância do Amazon EC2.
Por padrão, **um grupo de segurança nega todo o tráfego de entrada e permite todo o tráfego de saída**. Você pode adicionar regras personalizadas para configurar o tráfego que será permitido
Neste exemplo, suponha que você esteja em um prédio com um porteiro que recebe as visitas no lobby. Você pode pensar nas visitas como pacotes e no porteiro como um grupo de segurança. À medida que as visitas chegam, o porteiro verifica uma lista para garantir que eles podem entrar no edifício. No entanto, o porteiro não verifica a lista novamente quando as visitas saem do edifício
Se você tiver várias instâncias do Amazon EC2 na mesma VPC, poderá associá-las ao mesmo grupo de segurança ou usar grupos de segurança diferentes para cada instância. 

### Filtragem de pacotes stateful
Os grupos de segurança fazem a filtragem de pacotes stateful. **Eles se lembram de decisões anteriores** tomadas para pacotes recebidos.
Considere o mesmo exemplo de envio de uma solicitação de uma instância do Amazon EC2 para a internet. 
Quando a resposta de pacote da solicitação retorna para a instância, o grupo de segurança lembra-se da solicitação anterior. O grupo de segurança permite que a resposta prossiga, independentemente das regras do grupo de segurança de entrada.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/21872024-78d1-4728-9828-b5eb915d8e02)

Com as ACLs de rede e os grupos de segurança, você pode configurar regras personalizadas para o tráfego na sua VPC. Conforme você sabe mais sobre a segurança e a rede da AWS, entenda as diferenças entre ACLs de rede e grupos de segurança.

### Recapitulação de componente da VPC
- **Sub Rede Privada** - Isola bancos de dados contendo informções pessoais de clientes.
- **geteway privado virtal** - cria um conexão VPN entre a VPC e a rede corporativa interna.
- **Sub-rede Pública** - é compativel com o site voltado para o cliente.
- **aws Direct Conect** - Estabelece uma conexão dedicada entre o data center on-premises e a VPC.


## Redes Globais
### Sistema de nomes de domínio (DNS)
Suponha que a AnyCompany tenha um site hospedado na nuvem AWS. Os clientes digitam o endereço da web no navegador e podem acessar o site. Isso acontece devido à resolução do sistema de nomes de domínio (DNS). Na resolução de DNS, o resolvedor DNS do cliente se comunica com um servidor DNS.
Pense no DNS como a lista telefônica da internet. A resolução de DNS é o processo de conversão de um nome de domínio para um endereço IP. 

### Amazon Route 53
O Amazon Route 53(opens in a new tab) é um serviço da web de DNS. 
Oferece aos desenvolvedores e empresas uma maneira confiável de rotear os usuários finais para aplicativos da internet hospedados na AWS. 
O Amazon Route 53 conecta solicitações de usuários à infraestrutura em execução na AWS (como instâncias do Amazon EC2 e balanceadores de carga). Ele pode direcionar os usuários para a infraestrutura fora da AWS.
Outro recurso do Route 53 é a capacidade de gerenciar os registros DNS para nomes de domínio. Você pode registrar novos nomes de domínio diretamente no Route 53. Você também pode transferir registros DNS para nomes de domínio existentes gerenciados por outras empresas de registro de domínio. Isso permite que você gerencie todos os seus nomes de domínio em um único local.










