# Aula 11 - Security Groups da AWS
Na AWS, os security groups agem como um firewall integrado para seus servidores virtuais. Com esses security groups, você tem controle total sobre o nível de acesso das suas instâncias.
No nível mais básico, um security group é apenas outro método de filtrar o tráfego direcionado às instâncias. Ele fornece controle sobre qual tráfego permitir ou negar. Para determinar quem tem acesso às instâncias, configure uma regra de security group. As regras podem variar, desde manter a instância totalmente privada até totalment 

## Principais recursos 
- Os security groups atuam como um firewall integrado para os servidores virtuais.
- As regras do security group determinam quem tem acesso às instâncias.
- Os security groups são stateful.


## Amazon VPC (Amazon Virtual Private Cloud) e Securityt Groups
A Amazon Virtual Private Cloud (Amazon VPC) fornece vários recursos para aumentar e monitorar a segurança da VPC:
- Os security groups atuam como um firewall para instâncias associadas do Amazon Elastic Compute Cloud (Amazon EC2). Os security groups controlam tanto os tráfegos de entrada como os de saída no nível da instância.
- As listas de controles de acesso à rede (ACLs de rede) atuam como um firewall para sub-redes associadas. Elas controlam o tráfego de entrada e de saída no nível da sub-rede.
- O Amazon EC2 utiliza criptografia de chave pública para criptografar e descriptografar as informações de login. A criptografia de chave pública usa uma chave pública para criptografar uma parte dos dados. O destinatário usa a chave privada para descriptografar os dados. As chaves privada e pública são conhecidas como par de chaves.
- Para fazer login na instância, você deve realizar as seguintes ações:
    - Crie um par de chaves.
    - Especifique o nome do par de chaves ao iniciar a instância pela primeira vez.
    - Forneça a chave privada ao se conectar à instância.
- Os security groups são stateful, mas as ACLs de rede são stateless.
    - ***Stateful*** significa que o computador rastreia o estado da interação, geralmente definindo valores em uma configuração de armazenamento designada para essa finalidade.
    - ***Stateless*** significa que nenhuma informação é retida pelo remetente ou pelo destinatário. Cada solicitação de interação deve ser tratada inteiramente com base nas informações que a acompanham.
