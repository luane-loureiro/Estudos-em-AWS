# Elastic Load Balance

## O que é um balanceador de carga? 
- Age como um diretor de tráfego que fica na frente dos servidores e encaminha as solicitações do cliente. 
- Ele encaminha solicitações em todos os servidores que podem atender a essas solicitações de maneira a maximizar a velocidade e a utilização da capacidade.
- Ele garante que nenhum servidor esteja sobrecarregado, o que pode prejudicar o desempenho.
- Se um único servidor ficar inativo, o balanceador de carga redirecionará o tráfego para os servidores on-line restantes.

## Casos de uso
- Seguro - acesso por  meio deumunico ponto
- Desacoplar -  Desacople o ambiente de aplicativos
- Tolerancia d Falhas - Ofereça alta disponibilidade e tolerância falhas
- Expancivo - Aumente a elasticidade e escalibidade

### Classic Load Balancer
#### Casos de uso
- Acesse servidores por meio de um único ponto Desacople o ambiente do aplicativo
- Ofereça alta disponibilidade e tolerância a falhas
- Aumente a elasticidade e a escalabilidade
  
### Balanceador de carga de aplicativo 
#### Casos de Uso
- Roteamento baseado em caminho e baseado em host
- Suporte nativo ao IPv6
- Portas dinâmicas
- Protocolos de solicitação adicionais compatíveis
- Proteção contra exclusão e rastreamento de solicitações
- Métricas aprimoradas e logs de acesso
- Verificações de integridade direcionadas

### Network Load Balancer
#### Caso de uso 
- Padrões de tráfego repentinos e voláteis
- Único endereço IP estático por zona de disponibilidade
- Funciona bem para aplicativos que exigem desempenho extremonetwork

  

