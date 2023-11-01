# Aula 62 - Visão geral da rede AWS

## Redes na Nuvem AWS
Em sua forma mais básica, uma rede baseada em nuvem é um espaço de endereço IP privado onde você pode implantar recursos de computação.
Na Amazon Web Services (AWS), um componente de virtual private cloud (VPC) fornece esse espaço de rede privado. 
Uma VPC permite que você defina uma rede virtual na sua própria área logicamente isolada dentro da Nuvem AWS. 
Dentro dessa rede virtual, você pode implantar recursos de computação da AWS.

## Componentes das Redes AWS
Uma VPC pode abranger várias zonas de disponibilidade, e seus principais tipos de componentes incluem:
#### • Sub-rede
As sub-redes são segmentos de rede lógicos dentro de sua VPC. Elas permitem que você subdivida sua rede de VPC em redes menores dentro de uma única zona de disponibilidade. 
Uma sub-rede é pública se estiver conectada a um gateway da Internet ou privada se não estiver. Uma sub-rede é necessária para a implantação de uma instância em uma VPC.

#### • Grupo de segurança 
Um grupo de segurança é um conjunto de regras de firewall que protegem instâncias. 
Elas permitem ou bloqueiam o tráfego de entrada e saída em uma instância (com estado).
Se você não especificar um grupo em particular no momento da execução, uma instância será automaticamente atribuída ao grupo de segurança padrão para a VPC. Um grupo de segurança está associado a uma instância.

#### • Interface de rede primária (interface de rede elástica) – 
uma interface de rede elástica é uma interface de rede virtual (NIC) que conecta uma instância a uma rede. Cada instância em uma VPC tem uma interface de rede padrão, a interface de rede primária, que não pode ser desanexada da instância.

#### • Roteador
Um roteador é um componente que roteia o tráfego dentro da VPC.  

#### • Gateway da Internet 
Um gateway da Internet é um componente da VPC que permite a comunicação entre instâncias em uma VPC e a Internet.

#### • Gateway privado virtual
Um gateway privado virtual é o componente definido no lado da AWS de uma conexão de rede privada virtual (VPN). Uma conexão VPN fornece um túnel seguro e criptografado entre dois endpoints de rede.

#### • Gateway do cliente 
um gateway do cliente é um dispositivo físico ou um aplicativo de software definido no lado do cliente de uma conexão VPN.

## Amazon VPC e VPCs
Uma VPC é uma rede virtual provisionada em uma seção logicamente isolada da Nuvem AWS:
- Oferece suporte à separação lógica com sub-redes
- Oferece segurança detalhada
- Oferece suporte a uma rede privada virtual (VPN) de hardware opcional

## Configuração da Amazon VPC: endereçamento IP 
- Ao criar uma VPC, você deve especificar o intervalo permitido de endereços IP. Esse intervalo representa endereços IPv4 e é expresso na forma de um bloco Classless Inter-Domain Routing (CIDR). 
- Esse intervalo exigido é conhecido como o bloco CIDR principal da VPC. Depois que a VPC for criada, você poderá, opcionalmente, adicionar até quatro blocos CIDR secundários a ela.
-  Os intervalos de endereços IP privados válidos são definidos por Request for Comment (RFC) 1918.
-  Em uma VPC, você só pode definir redes entre /16 e /28.

## Notação CIDR (Classless Inter-Domain Routing) 
O formato CIDR (Classless Inter-Domain Routing) é usado para especificar intervalos de endereço IP quando você cria uma VPC ou uma sub-rede. Ele especifica um bloco (conhecido como bloco CIDR) de endereços IP que usam o formato x.x.x.x/n, onde:
- x.x.x.x é um endereço IP. Um endereço IP IPv4 é um número de 32 bits representado como quatro números, separados por pontos. Portanto, cada x é um número de 8 bits (um byte) que pode ter um valor no intervalo de 0 a 255. O endereço IP é dividido logicamente em um prefixo de rede e um identificador de host, que identificam a rede e o host dentro da rede, respectivamente.
-  /n especifica o comprimento em bits da parte do prefixo de rede do endereço IP (começando do bit mais à esquerda). Para um endereço IP IPv4, o valor de n pode estar no intervalo de 0 a 32. Em uma VPC, o valor de n é restrito a 16 — 28. Em geral, quanto maior o valor de n, menor será o tamanho do intervalo, o que resulta em um número menor de endereços IP utilizáveis.

## Endereços IP reservados da Amazon VPC 

| Bloco CIDR | Lógica |
|---------------|--------|
| 10.0.0.0 | Endereço de rede |
| 10.0.0.1 | Reservado pela AWS para o endereço do roteador da VPC |
| 10.0.0.2 |O endereço IP do servidor DNS (Domain Name Server) é sempre a base do intervalo de rede VPC mais dois. No entanto, a VPC também reserva a base de cada intervalo de sub-rede mais dois. |
| 10.0.0.3 | Reservado pela AWS para uso futuro. |
| 10.0.0.255 | Endereço de transmissão de rede. A AWS não oferece suporte à transmissão em uma VPC.

## Amazon VPC 
Principais características de uma VPC:
- As VPCs podem abranger várias Zonas de disponibilidade em uma região da AWS.
- As VPCs possuem um roteador implícito que roteia todo o tráfego na VPC.
- As VPCs têm uma tabela de rotas padrão que especifica as rotas permitidas para fora da VPC. Por padrão, essa tabela define uma rota (regra) que permite que todo o tráfego do intervalo de endereços IP CIDR seja roteado localmente. No exemplo, a VPC tem um intervalo de endereços de 10.0.0.0/16. Portanto, sua tabela de rotas padrão possui uma regra para rotear todo o tráfego destinado a esse intervalo por meio da rota local.

## Componentes da Amazon VPC
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/aafcd4d9-ee93-4840-b91e-57696b807880)

Este diagrama ilustra as seguintes características de sub-redes: 
- As sub-redes podem existir em uma (e apenas uma) Zona de disponibilidade.
- Em uma sub-rede, o intervalo de endereços do bloco CIDR deve ser um subconjunto do intervalo de endereços da VPC. No exemplo, o bloco CIDR para a sub-rede na Zona de disponibilidade A oferece suporte a endereços IP 10.0.10.0 — 10.0.10.255. O bloco CIDR na Zona de disponibilidade B oferece suporte a endereços IP 10.0.20.0 — 10.0.20.255. Ambos os intervalos são subconjuntos do intervalo de endereços da VPC, que oferece suporte a endereços IP 10.0.0.0 — 10.0.255.255.
- Os blocos CIDR de sub-rede dentro de uma VPC não devem se sobrepor. Essa regra é verdadeira no diagrama das duas sub-redes (10.0. 10 ,0/24 em comparação à 10.0.20.0/24).
- O tráfego de e para cada sub-rede flui por meio do roteador implícito da VPC.


## Recurso de atribuição automática de sub-rede IP pública
- Somente instâncias executadas em uma Amazon VPC padrão recebem um endereço IP público durante a criação.
- As instâncias criadas em VPCs personalizadas exigem a substituição da configuração padrão para receber endereços IP públicos.
- Como alternativa, defina as configurações Modificar atribuição automática de IP em sub-redes para atribuir automaticamente endereços IP públicos às instâncias.
- Diferentemente dos endereços IP elásticos, os endereços IP públicos não são estáticos.

## Componentes da Amazon VPC: tabelas de rotas 
- Cada VPC acompanha um roteador implícito que direciona o tráfego entre os recursos em cada sub-rede e fora da sub-rede.
- O roteador usa uma tabela de rotas para determinar os destinos IP válidos de uma sub-rede e o destino correspondente para alcançar o destino.
- Uma tabela de rotas é um mecanismo usado para rotear o tráfego originado de uma sub-rede associada em uma VPC. Ela contém um conjunto de regras (também chamado de rotas) que determinam para onde o tráfego é enviado.
- As rotas em uma tabela de rotas consistem em uma orientação e um destino. O roteador lê a rota assim: "Qualquer tráfego que vai para a orientação deve ser roteado por meio do destino".
- Um destino pode ser um ID de instância específico, um ID de interface de rede elástica, um gateway de Internet ou um gateway privado virtual.
- Quando uma VPC é criada, uma tabela de rotas padrão também é criada. Essa tabela de rotas padrão tem uma regra que roteia o tráfego local para qualquer lugar dentro do intervalo de endereços IP da VPC.
- Você pode adicionar mais rotas à tabela de rotas padrão.
- Quando você cria uma sub-rede, ela é automaticamente associada à tabela de rotas padrão da VPC.

## Componentes da Amazon VPC: interfaces de rede elástica
- Uma interface de rede elástica, também chamada de interface de rede (NIC), é uma interface de rede virtual (NIC) anexada a um EC2 instância. 
- Ela fornece o ponto de conexão que permite que uma instância se comunique com uma rede.
- Cada interface de rede tem um endereço IP primário, além de endereços IP secundários adicionais.
- Ele também tem seu próprio endereço de media access control (MAC) e grupos de segurança.


### Os casos de uso de várias NICs em uma instância incluem: 
- Usando dispositivos de rede e segurança em uma VPC — alguns dispositivos de rede e segurança, como balanceadores de carga, servidores de conversão de endereços de rede (NAT) e servidores proxy, preferem ser configurados com várias NICs. Você pode criar e anexar NICs secundárias a instâncias em uma VPC que executa esses tipos de aplicativos. Em seguida, configure as interfaces adicionais com seus próprios endereços IP públicos e privados e grupos de segurança.
- Criação de uma interface de rede somente de gerenciamento — Para garantir que a largura de banda em uma interface voltada para o cliente não seja afetada pelas atividades de gerenciamento (upload de novas versões de software, download de arquivos de log etc.), uma ENI separada é usada para o trabalho administrativo.


## VPC padrão 
Quando você cria uma conta da AWS, a AWS cria automaticamente uma VPC padrão para você com um bloco CIDR de 172.31.0.0/16. 
Essa VPC fornece até 65.536 endereços IPv4 privados no intervalo 172.31.0.0—172.31.255.255. Essa VPC padrão permite que você comece a usar os recursos da VPC imediatamente.

A AWS também cria automaticamente os seguintes componentes na VPC padrão:
- Um gateway de Internet para permitir a comunicação com a Internet.
- Uma tabela de rotas padrão com regras para enviar tráfego para endereços IP no intervalo de endereços da VPC para uma rota local. Ela também envia tráfego para qualquer outro endereço IP para o gateway da Internet.
- Uma sub-rede pública em cada zona de disponibilidade com um tamanho /20, que fornece até 4.096 endereços. A opção Atribuir IP público automaticamente está habilitada para essas sub-redes. Qualquer instância executada na VPC padrão obtém automaticamente um endereço IP público. Elas são sub-redes públicas porque estão associadas à tabela de rotas padrão, que tem uma regra que permite o tráfego por meio de um gateway da Internet.

## Opções de DNS para uma VPC 
As opções de DNS (Domain Name System) para uma VPC incluem:
- Servidor DNS fornecido pela Amazon (Amazon Route 53 Resolver) 
- O seu próprio servidor DNS 
- Zonas hospedadas privadas do Amazon Route 53

