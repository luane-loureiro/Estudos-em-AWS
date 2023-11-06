# Aula 63 - Opções de conectividade da Amazon VPC 
## Opções de conectividade da Amazon VPC 
O Amazon Web Services (AWS) oferece várias opções para conectar uma Amazon VPC a outras VPCs, pontos de extremidade externos e serviços da AWS.
| Se Você precisar: | Considere o uso de: | Categoria de solução:  |
|------- |--------|--------|
| Conectar uma sub-rede privada à Internet | •Gateway NAT  •Instância NAT | •Conectividade da instância do Amazon Elastic Compute Cloud (Amazon EC2) |
| Conectar uma VPC a outra VPC | •VPC peering | •Amazon VPC para Amazon VPC |
| Conectar uma VPC a uma rede externa |•AWS Site-to-Site virtual private network (VPN)  •AWS Direct Connect plus VPN  •AWS VPN CloudHub | •Rede para a Amazon VPC  •Conectividade da VPN | 
| Conectar uma VPC aos serviços da AWS sem sair da rede da AWS | •AWS PrivateLink  •Endpoint do gateway da VPC | •Amazon VPC para Amazon VPC  •Endpoint do gateway da VPC |
| Conectar uma VPC a várias VPCs e redes externas | •AWS Transit Gateway | •Rede para a Amazon VPC  •Amazon VPC para Amazon VPC |


## Conversão de endereços de rede (NAT)
Considere a situação em que você possui uma instância com um banco de dados autônomo que é executado em uma sub-rede privada. Você deseja aplicar um patch de software ao banco de dados, mas a sub-rede privada impede que você acesse a Internet para fazer download do patch. Você não pode colocar a instância em uma sub-rede pública porque não quer que os clientes da Internet conectem-se à ela. No entanto, você precisa de uma maneira de conectar-se à Internet pela instância. Como você pode fazer isso?
Você pode usar um dispositivo NAT para habilitar uma instância em uma sub-rede privada para se conectar à Internet ou a outros serviços da AWS. Isso também pode impedir a Internet de iniciar conexões com a instância. Um dispositivo NAT encaminha o tráfego da instância que está na sub-rede privada para a Internet ou outros serviços da AWS. Em seguida, ele envia a resposta de volta para a instância. Quando a solicitação vai para a Internet, o endereço IP de origem é substituído pelo endereço do dispositivo NAT. Quando a resposta vai para a instância, o dispositivo NAT converte o endereço de volta para o endereço IP privado da instância.

## Características do gateway NAT e etapas de criação
### Características do gateway NAT 
- erviço gerenciado da AWS
- Redundância integrada dentro de uma zona de disponibilidade
- Exige um endereço IP elástico
- Compatível com os protocolos:
    - Transmission Control Protocol (TCP – Protocolo de controle de transmissão)
    - User Datagram Protocol (UDP)
    - Internet Control Message Protocol (ICMP – Protocolo de mensagem de controle da Internet)
 

## Arquitetura de uma VPC com um gateway NAT 

## Emparelhamento da Amazon VPC 
Por padrão, as VPCs são seções de rede isoladas na Nuvem AWS. Se precisar conectar duas VPCs juntas para trocar tráfego ou dados, você pode criar uma conexão de emparelhamento da VPC.
Uma conexão de emparelhamento da VPC é uma conexão de redes entre duas VPCs que permite que você direcione o tráfego entre elas usando endereços IP privados. As VPCs podem estar na mesma região, em regiões diferentes ou até mesmo em contas diferentes da AWS. Os dados que são trocados atravessam privadamente a estrutura dorsal da AWS, e nenhum gateway será necessário para o emparelhamento funcionar. A conexão é controlada pelas tabelas de rotas, que fazem referência à conexão de emparelhamento como um destino para as rotas. Isso resulta em uma conexão sem ponto único de falhas para comunicação ou gargalos de largura de banda.
Você pode criar uma conexão de emparelhamento da VPC usando o Console de gerenciamento da AWS. O emparelhamento de VPC envolve o estabelecimento de uma conexão bidirecional que ambas as partes devem inicializar e aceitar. Além disso, os proprietários de ambas as VPCs devem estabelecer rotas que permitam que o tráfego seja enviado entre as redes. Essa relação de roteamento significa que as duas redes não devem ter espaços de endereço sobrepostos.


## Criar uma conexão de emparelhamento da VPC Para criar uma conexão de emparelhamento da VPC
1. O proprietário da VPC solicitante envia uma solicitação de conexão da VPC.
2. O proprietário da VPC receptora aceita a solicitação de conexão da VPC.
3. Ambos os proprietários adicionam registros de tabela de rotas em ambas as VPCs participantes.
4. Se necessário, os proprietários ajustam as regras do grupo de segurança nas duas VPCs participantes.
5. Se necessário, os proprietários ativam a resolução de nome de host DNS (Domain Name System) para conexão VPC.

## Comandos da AWS CLI para a conexão de emparelhamento da VPC 
### Comando

```aws ec2 create-vpc-peering-connection --vpc-id vpc-1a2b3c4d --peer-vpc-id vpc-11122233```


 # Continua -->
