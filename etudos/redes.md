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
