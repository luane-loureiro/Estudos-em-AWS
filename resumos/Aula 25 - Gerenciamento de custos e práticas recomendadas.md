# Aula 25 - Gerenciamento de Custos e Práticas Recomendadas
Um dos benefícios fundamentais da computação em nuvem é que você paga apenas pelo que precisa, quando precisa. Devido a esse princípio, você pode buscar maneiras de usar seus recursos de nuvem com eficiência e reduzir custos. Você pode usar várias estratégias para atingir esse objetivo

## Custo-benefício da nuvem e oportunidades de redução de custos Custo-benefício da Nuvem AWS:
- Pagar apenas pelo que precisar, quando precisar.
- Criar scripts ou modelos para encerrar ambientes.
- Pode desativar recursos não utilizados
    - Serviços específicos após o horário comercial e durante feriados
    - Ambientes de desenvolvimento ou teste
    - Ambientes de recuperação de desastres (DR)
    - Instâncias marcadas como temporárias

## Ferramentas e serviços de gerenciamento de custos da AWS
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e91e97ce-a152-4df4-9f22-b6bf43a3174c)

### painel de faturamento da AWS
O painel fornece uma página Contas que mostra as informações mais atualizadas sobre seus custos e uso. 
Permite que você visualize o status das despesas da AWS acumuladas no mês. Você também pode usá-lo para identificar os serviços que representam a maior parte das suas despesas gerais.
Você também pode usar a página **Relatórios de custos** e uso da AWS para gerar um relatório que mostra os dados mais detalhados sobre os seus custos e uso da AWS. 
Esse relatório permite que você analise e entenda melhor os custos da AWS e as ofertas de produtos específicos e os valores de uso subjacentes a esses custos.
Você pode acessar várias outras ferramentas de gerenciamento de custos no painel de faturamento. 
Você pode usar essas ferramentas para estimar e planejar seus custos da AWS, incluindo contas da AWS, o AWS Cost Explorer, os orçamentos da AWS e os relatórios de custo e uso da AWS.


### AWS Bills - Faturas
A página AWS Bills lista os custos que você incorreu no último mês para cada serviço da AWS. Ela também inclui um detalhamento adicional por região da AWS e conta vinculada.
Essa ferramenta fornece acesso às informações mais atualizadas sobre seus custos e uso, incluindo sua fatura mensal e a análise detalhada dos serviços da AWS que você usa.


###  O AWS Cost Explorer
uma análise detalhada dos dados de custos e de uso, com o AWS Cost Explorer, para identificar tendências, indicar os fatores determinantes dos custos e detectar anomalias. 
Esse serviço fornece uma interface intuitiva que permite criar rapidamente relatórios personalizados (incluindo gráficos e dados tabulares). 
Você pode usar esses relatórios para analisar seus dados de custo e uso, tanto em alto nível quanto para solicitações específicas.
O AWS Cost Explorer permite visualizar os seus custos e o uso, além de analisá-los para identificar tendências. 
Você pode filtrar e agrupar dados ao longo de várias dimensões, como serviço, tipo de instância e tag. 
O Cost Explorer fornece dois tipos de relatórios padrão:
- **Relatórios de custo e uso** — Esses relatórios permitem que você entenda seus custos e uso de todos os serviços. Por exemplo, o relatório Custos mensais por serviço (exibidos na captura de tela) mostra os custos dos últimos 3 meses, agrupados por serviço. Os cinco principais serviços são mostrados por eles mesmos, e o restante é agrupado em uma barra (rotulada Outros).
- **Relatórios de Instância Reservada (IRS)** — Esses relatórios são específicos para o uso de Instâncias Reservadas. Eles fornecem uma compreensão dos seus custos de utilização comparativos para instâncias reservadas em comparação a instâncias sob demanda.

Você pode visualizar dados até dos últimos 13 meses, prever quanto provavelmente gastará nos próximos 3 meses e obter recomendações sobre quais instâncias reservadas para comprar.
Se você tiver muitas contas e tiver habilitado o faturamento consolidado para o AWS Organizations, poderá usar o AWS Cost Explorer para visualizar os custos em todas as contas vinculadas. 
Você também pode monitorar os gastos individuais diários e mensais de cada conta vinculada.


### AWS Budget (Orçamentos da AWS)
O Orçamentos da AWS permite que você defina orçamentos personalizados que enviam alertas quando o uso ou os custos excedem (ou têm previsão de exceder) o valor orçado. 
O AWS Budgets usa a visualização de custos fornecida pelo Cost Explorer para mostrar o status dos seus orçamentos e fornecer previsões dos custos estimados. 
Você também pode usar os Orçamentos para criar notificações quando ultrapassarem os valores previstos em orçamento ou quando seus custos previstos ultrapassarem seus orçamentos. 
Os orçamentos podem ser rastreados nos níveis mensal, trimestral ou anual. Você pode personalizar as datas de início e término. 
Os alertas de orçamento podem ser enviados por e-mail ou por meio de um tópico do Amazon Simple Notification Service (Amazon SNS).


### AWS Cost and Usage Reports
A página Relatórios de custo e uso da AWS é um local único para acessar informações abrangentes sobre os custos e o uso da AWS. 
Você pode usá-lo para gerar relatórios que contenham itens de linha para cada combinação exclusiva de produtos da AWS, tipo de uso e operação que você usa na sua conta da AWS. 
Você pode personalizar os relatórios gerados para agregar as informações por hora ou por dia. 
Você também pode publicar seus relatórios de faturamento da AWS em um bucket do Amazon Simple Storage Service (Amazon S3), e a AWS atualizará os relatórios no bucket uma vez por dia.


### Alarmes de Faturamento do Amazon CloudWatch
- Você pode monitorar as suas cobranças de uso com o Amazon CloudWatch.
- Gere um alerta quando as cobranças estimadas excederem um limite especificado
- Habilitado no Console de gerenciamento da AWS
- Deve ser criado na região us-east-1
    - Armazenamento central para todas as métricas de faturamento
- Com base em métricas que incluem cobranças totais e específicas do serviço
- Envie notificações por e-mail por meio de um tópico do Amazon Simple Notification Service (Amazon SNS)


## Projetar para redução de custos 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/5a39a26d-126a-4c6a-a8ca-73e54facdf6f)

Com a ajuda de ferramentas de gerenciamento de custos, você pode criar uma estratégia de redução de custos para seus serviços da AWS. Uma boa estratégia inclui os princípios de otimização de custos listados:
- Defina orçamentos personalizados de custos e uso. Essa prática permite que você siga melhor o Pague apenas pelo que precisar, quando você precisar, princípio de computação na nuvem.
- Instâncias do tamanho certo:
    - Considere o uso de instâncias T2 ou T3 para cargas de trabalho que, ocasionalmente, precisam de intermitência para o desempenho total do núcleo. Tais instâncias são projetadas para fornecer um desempenho de CPU no nível da linha de base com capacidade de intermitência até um nível superior quando for exigido pela carga de trabalho. As instâncias T3 oferecem os mais recentes processadores Intel Xeon Scalable, o que resulta em uma melhoria de preço em relação ao desempenho até 30% melhor que as instâncias T2.
    - Considere a compra de instâncias reservadas para grupos de instâncias de longa execução.
    - Use instâncias spot para tarefas de processamento em lote e para obter o melhor preço. Use relatórios de histórico de instâncias spot para ajustar solicitações de sugestões de preço.
- Considere o uso do AWS Lambda. O modelo sem servidor permite que você execute código sem provisionar ou gerenciar servidores, e você paga apenas pelo tempo de computação consumido. Você não será cobrado quando o código não estiver em execução.
- Use serviços gerenciados Na nuvem, os serviços gerenciados, como o Amazon S3 e o Amazon Relational Database Service (Amazon RDS), eliminam a carga operacional de manter servidores e operar em escala de nuvem. Eles também oferecem um custo menor por transação ou serviço.
- Use o AWS Trusted Advisor para obter conselhos específicos sobre como reduzir custos.

## Encontrar e Eliminar Desperdícios
- Usar métricas do Amazon CloudWatch para encontrar instâncias ociosas de longa execução. – Às vezes, recursos desnecessários ainda estão em execução.
- Usando o AWS Cost Explorer para encontrar os custos associados a projetos ou iniciativas inteiras.

## Usar um Script Stopinator
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/93775869-8ea8-4dc3-a030-c90368576113)

Usar um script stopinator:
- Ativar e desativar recursos selecionados da AWS
- É uma prática recomendada para reduzir custos

Escrever e usar um script stopinator é uma técnica para automatizar o desligamento de instâncias. 
Um stopinator é um termo genérico para qualquer script ou aplicativo escrito na Nuvem AWS e que procura e interrompe instâncias não utilizadas.
Normalmente, esses scripts são configurados para executar durante a noite e nos fins de semana. 
Usar um stopinator pode resultar em economias significativas de custos para uma organização, o que pode liberar seu orçamento de computação na nuvem para novos projetos. 
Ele também é um script utilitário de função dupla útil porque normalmente é projetado para permitir que você inicie recursos quando você precisar deles (por exemplo, no início do dia de trabalho).

### Stopnator sem servidor
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/3e92bd35-991e-4114-8f2b-7c1514011560)

Você não precisa criar ou usar uma instância do Amazon Elastic Compute Cloud (Amazon EC2) para executar um stopinator. 
Um design simples e eficiente é usar uma combinação de uma função do Lambda e um evento do Amazon CloudWatch Events em uma solução sem servidor.
A lógica para interromper e iniciar uma instância é implementada como uma função Lambda. 
Essa função é acionada por um evento do CloudWatch Events conforme a programação desejada.

## Trusted Advisor
### O que é o Trusted Advisor?
erformance e melhorar a segurança ao otimizar o seu ambiente da AWS. O AWS Trusted Advisor analisa seu ambiente da AWS e fornece recomendações para as práticas recomendadas em cinco categorias:
- **Otimização de custos** — Conselhos sobre como você pode economizar dinheiro eliminando recursos não utilizados e ociosos ou assumindo compromissos com a capacidade reservada.
- **Desempenho** — Conselhos sobre como melhorar o desempenho dos seus serviços verificando os limites de serviço, garantindo o uso da taxa de transferência provisionada e monitorando instâncias superutilizadas.
- **Segurança** — Conselhos sobre como melhorar a segurança dos seus aplicativos, fechando lacunas, habilitando vários recursos de segurança da AWS e examinando suas permissões.
- **Tolerância a falhas** — Conselhos sobre como aumentar a disponibilidade e a redundância dos seus aplicativos da AWS usando escalabilidade automática, verificações de integridade, implantação multi-AZ e recursos de backup.
- **Limites de serviço** — Conselhos sobre os serviços cujo uso excede 80% do limite de serviço.

### Recursos de Otmização de Custos do AWS Trusted Advisor
Você pode usar o AWS Trusted Advisor para identificar recursos ociosos, como instâncias do EC2, balanceadores de carga e volumes subutilizados e endereços IP elásticos não utilizados. 
O Trusted Advisor também é uma boa ferramenta para otimização de custos. Ele fornece verificações e recomendações que permitem que você obtenha economia de custos.

- Verificações de otimização de custo de amostra
    - Recursos ociosos, como instâncias do Amazon Elastic Compute Cloud (Amazon EC2), instâncias do Amazon Relational Database Service (Amazon RDS)
    - Load balancers e volumes não utilizados
    - Endereços de IP Elastic não utilizados
- Use as verificações de otimização de custos para obter um nível básico de economia de custos
- Verificações e recomendações principais estão disponíveis para todos os clientes
- Verificações e recomendações adicionais estão disponíveis com os planos Business Support ou Enterprise Supp

### Recomendações do AWS Trusted Advisor
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/07a4f7e4-20a4-4d7e-8318-0b82f2bdc29a)
O AWS Trusted Advisor analisa seu ambiente da AWS e fornece recomendações para as práticas recomendadas. 
As recomendações incluem links para realizar ações diretas. A orientação em tempo real do AWS Trusted Advisor ajuda você a provisionar seus recursos de acordo com as práticas recomendadas da AWS
