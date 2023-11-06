# Aula 64 - Segurança e solução de problemas da rede
## Proteção da rede
### Redes em camadas Defesa de rede em camadas para VPCs
Sua rede virtual pode e deve ser protegida em vários níveis diferentes:
1. O nível de segurança com escopo mais amplo está no nível da tabela de rotas. Como você aprendeu anteriormente, ter uma sub-rede privada sem caminho direto para a Internet é uma das melhores maneiras de proteger seus recursos de computação internos contra o acesso não autorizado.
2. O segundo nível são as listas de controle de acesso à rede (ACLs de rede). As ACLs de rede permitem que você defina o comportamento de segurança padrão para suas sub-redes. A segurança da VPC ou da camada de sub-rede geralmente é controlada pela equipe de segurança de rede.
3. No terceiro nível, os security groups podem ser usados para controlar o comportamento no nível de uma instância ou interface de rede elástica.
4. No quarto nível, você pode optar por usar algum tipo de software de detecção baseado em host de terceiros que monitora instâncias individuais do Amazon Elastic Compute Cloud (Amazon EC2) em busca de ameaças específicas (como invasão de malware, bugs conhecidos do sistema operacional e auditoria de segurança).

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/d6c13ae8-7f31-47b4-981f-45d0b5db468a)

### Security groups Regras de saída Tipo
Security groups: 
- Usado para permitir o tráfego de ou para uma interface de rede elástica
- Configurado por padrão para:
    - Negar todo o tráfego de entrada 
    - Permitir todo o tráfego de saída
- Com estado — Se as regras permitirem que o tráfego flua em uma direção, as respostas podem fluir automaticamente na direção oposta.
- Geralmente administrados por desenvolvedores de aplicações

Os security groups são usados para restringir o tráfego de entrada e saída da interface de rede (NICs) que estão associadas a eles. Alguns aspectos importantes a observar em relação aos security groups são:
- Uma VPC possui um security group padrão que permite todo o tráfego de saída, mas nega todo o tráfego de entrada.
- Quando você executa uma instância em uma VPC e não especifica um security group para ela, a instância é automaticamente atribuída ao security group padrão.
- As regras são definidas em duas tabelas de entrada e saída separadas.
- Você pode especificar regras de permissão, mas não regras de negação.
- Todas as regras são avaliadas antes de decidir se o tráfego deve ser permitido.
- Todo o tráfego de saída em resposta a uma solicitação de entrada é permitido.


### Listas de controle de acesso à rede 
#### Listas de controle de acesso à rede (ACLs de rede):
- Permitir ou negar o tráfego de entrada e saída de sub-redes
- A network ACL padrão: – Permite todo o tráfego de entrada e saída
- Sem estado – Mesmo que as regras permitam que o tráfego flua em uma direção, você deve permitir explicitamente que as respostas fluam na direção oposta.
- Fortalece a segurança como um nível secundário de defesa no nível da sub-rede

As listas de controle de acesso à rede (Network ACLs) estão associadas a uma sub-rede em uma VPC. Elas definem regras que permitem ou negam o tráfego de entrada e saída na sub-rede. Elas são sem estado, o que significa que as regras de entrada e saída são independentes umas das outras. Se um tipo de tráfego de solicitação for permitido para a entrada, você deverá definir explicitamente uma regra de saída para o mesmo tipo para permitir o tráfego de resposta.
As regras são definidas como registros com um número de regra em duas tabelas de regras de entrada e saída separadas. Quando elas decidem se desejam permitir o tráfego, as regras em uma tabela são avaliadas em ordem crescente do número da regra. O número de regra especial que é representado por um asterisco (*) é avaliado por último e representa um catchall se nenhuma correspondência com uma regra anterior tiver sido encontrada.
As regras de entrada e saída são definidas assim: 
- Especificar o tipo de regra (por exemplo, TCP personalizado)
- Fornecer um número de regra
- Definir o intervalo de portas que será permitido ou negado para dentro ou para fora
- Especificar o endereço IP ou intervalo de origem ou destino que será permitido ou negado para dentro ou para fora
  
Depois que a network ACL for definida, ela poderá ser associada a uma ou mais sub-redes dentro de uma VPC.


### Host Bastion
#### O host bastion: 
- Fornece acesso a public-subnet-to-private-subnet.
    - Ponto de salto para obter acesso a uma sub-rede privada.
- Não armazene chaves privadas no host bastion.
    - Para instâncias do Linux, use o recurso de encaminhamento de agente do cliente Secure Shell (SSH) para especificar a chave.
    - Para instâncias do Microsoft Windows, descriptografe a senha com a chave no console do Amazon Elastic Compute Cloud (Amazon EC2) e adicione a instância a um domínio
 
Um host bastion serve como um ponto de partida da Internet pública para as instâncias do Amazon Elastic Compute Cloud (Amazon EC2) e outros recursos em uma sub-rede privada. 

Ao usar um bastion host, você pode acessar recursos privados publicamente por meio da Internet de uma forma que ainda minimiza a superfície de ataque da sua sub-rede privada.

A AWS recomenda enfaticamente que você use diferentes pares de chaves públicas/privadas para o host bastion e para os recursos na sub-rede privada. 

As chaves para os recursos de sub-rede privada não devem ser armazenadas no host bastion, porque qualquer usuário não autorizado que acessar seu host bastion teria acesso aos recursos na sua sub-rede privada





