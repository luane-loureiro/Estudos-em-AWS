# Aula 19 - Amazon CloudWatch
## Use a AWS com eficiência e obtenha insights 
- Para usar a AWS de maneira eficiente, você precisa de insights sobre os recursos da AWS:
    - Como você sabe quando deve executar mais instâncias do Amazon Elastic Compute Cloud (Amazon EC2)?
    - O desempenho ou a disponibilidade do aplicativo estão sendo afetados devido à capacidade insuficiente?
    - Quanto da infraestrutura está realmente sendo usada?

## Monitoramento do desempenho dos recursos - Amazon CloudWatch
Você pode capturar essas informações com o Amazon CloudWatch.
Quando você executa seus aplicativos em instâncias do EC2, é essencial monitorar o desempenho da sua carga de trabalho usando o Amazon CloudWatch. Ao monitorar o desempenho da carga de trabalho, você deve se fazer duas perguntas críticas: 

1. Como posso garantir que minha carga de trabalho tenha recursos suficientes do EC2 para atender a requisitos flutuantes de desempenho?
2. Como você pode automatizar o provisionamento de recursos para ocorrer sob demanda?

O CloudWatch ajuda com o monitoramento de desempenho. No entanto, por si só, ele não adicionará nem removerá instâncias do EC2. 
O Amazon EC2 Auto Scaling pode ajudar nessa situação.
Com o Amazon EC2 Auto Scaling, você pode manter a integridade e a disponibilidade da sua frota. 
Você também pode dimensionar dinamicamente suas instâncias do EC2 para atender às demandas durante picos e épocas de baixa demanda


## O que é o Amazon CloudWatch? 
Monitora o estado e a utilização da maioria dos recursos que você pode gerenciar na AWS.
A principal função do Amazon CloudWatch para monitorar o desempenho e a integridade dos seus recursos e aplicativos da AWS. 
Você também pode usar o CloudWatch para coletar e monitorar arquivos de log de instâncias do EC2, AWS CloudTrail, Amazon Route 53 e outras fontes.
O Amazon CloudWatch é um sistema distribuído de coleta de estatísticas. 
Ele coleta e monitora as métricas dos seus aplicativos. 
Você também pode criar e usar suas próprias métricas personalizadas e receber notificações quando um alarme disparar. 
O CloudWatch tem duas opções de monitoramento diferentes: 
- **Monitoramento básico para instâncias do Amazon EC2**: sete métricas pré-selecionadas em uma frequência de 5 minutos e três métricas de verificação de status em uma frequência de 1 minuto, sem custo adicional.
- **Monitoramento detalhado para instâncias do Amazon EC2**: todas as métricas que estão disponíveis para o Monitoramento básico em uma frequência de 1 minuto, por um custo adicional. As instâncias com monitoramento detalhado habilitado fornecem agregação de dados pelo Amazon EC2, ID da Amazon Machine Image (AMI) e tipo de instância.


- Principais conceitos:
    - Métricas padrão
    - Métricas personalizadas
    - Alarmes
    - Notificações
- O agente do CloudWatch coleta métricas no nível do sistema:
    - Instâncias do EC2
    - Servidores locais

## Amazon CloudWatch Exemplos de alarmes
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/98437afd-7696-4a09-950e-3510a55519d8)

## Ações do Amazon CloudWatch 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e0da9229-ffe5-4ca5-bf86-71bce023a0e5)

## Alarmes do Amazon CloudWatch
- Testar uma métrica selecionada em relação a um limite específico (maior ou igual a, menor ou igual a) 
- O estado ALARM não é necessariamente uma condição de emergência

Você pode criar um alarme do CloudWatch que acompanha uma única métrica do CloudWatch ou o resultado de uma expressão matemática baseada em várias métricas do CloudWatch. 
O alarme executa uma ou mais ações com base no valor da métrica ou na expressão relativa a um limite por alguns períodos.
Um alarme tem três estados possíveis: 
- **OK** – A métrica está dentro do limite definido.
- **ALARM** – A métrica esta fora do limite definido.
- **INSUFFICIENT_DATA** – O alarme acabou de ser acionado, a métrica não está disponível ou não há dados suficientes para que a métrica determine o estado do alarme.

ALARM é apenas um nome que é dado ao estado e não necessariamente sinaliza uma condição de emergência que exija atenção imediata. Isso significa que a métrica monitorada é igual, maior ou menor que um valor limite especificado. Você poderia, por exemplo, definir um alarme que informa quando o CPUCreditBalance para uma determinada instância T2 está ficando em baixa. 

## Componentes de métrica
As métricas são os conceitos fundamentais no CloudWatch. A métrica representa um conjunto ordenado de pontos de dados publicados no CloudWatch. Considere uma métrica como uma variável a ser monitorada, e os pontos de dados que representam os valores dessa variável ao longo do tempo. Por exemplo, o uso da CPU de uma instância do EC2 específica é uma métrica que o Amazon EC2 fornece. Os pontos de dados em si podem ser provenientes de qualquer aplicativo ou atividade de negócios de onde você colete dados. 

| Métrica | Nome e valor |
|----------|------------|
| Namespace | Agrupa métricas relacionadas juntas |
| Dimensões | Pares de nome-valor que categorizam ainda mais as métricas |
| Período | Tempo especificado (em segundos) durante o qual a métrica foi coletada |

 - Um **namespace** é um contêiner para as métricas do CloudWatch. As métricas em namespaces diferentes são isoladas umas das outras, de forma que as métricas de aplicativos diferentes não são agregadas por engano nas mesmas estatísticas. Os namespaces da AWS usam a convenção de nomenclatura AWS/<service>. Por exemplo, o Amazon EC2 usa o namespace AWS/EC2.
- Uma **dimensão** é um par de nome-valor que identifica uma métrica de forma exclusiva. Você pode atribuir até 10 dimensões a uma métrica. Cada métrica tem características específicas que a descrevem, e você pode considerar dimensões como categorias para essas características. As dimensões lhe ajudam a projetar uma estrutura para o seu plano de estatísticas. Você pode usar dimensões para filtrar os resultados retornados pelo CloudWatch. Por exemplo, ao pesquisar por métricas, você pode obter estatísticas para uma determinada instância do EC2, especificando a dimensão InstanceId.
• Um **período** é o tempo associado a uma estatística específica do CloudWatch. Os períodos são definidos pela contagem de segundos. Você pode ajustar como os dados são agregados alterando a extensão do período. O período mais curto pode ser de 1 segundo ou ir até 1 dia (86.400 segundos).

## Métricas padrão e personalizadas
**Métricas padrão:**
- Agrupadas por nome de serviço
- Exibir graficamente para que as métricas selecionadas possam ser comparadas
- Só aparece se você tiver usado o serviço nos últimos 15 meses
- É acessível programaticamente por meio da AWS Command Line Interface (AWS CLI) ou da interface de programação de aplicativos (API)

**Métricas personalizadas:**
-  Agrupadas por namespaces definidos pelo usuário
-  Publique no CloudWatch usando a AWS CLI, uma API ou um agente do CloudWatch

## Monitoramento e segurança
Use o CloudWatch para monitorar atividades suspeitas, como:
– Picos incomuns e prolongados no uso do serviço, como a CPU, atividades de disco, o uso do Amazon Relational Database (Amazon RDS)
– Definir alertas sobre métricas de faturamento (você deve ativar esse recurso nas configurações da conta)

## Painéis automáticos do CloudWatch
Os painéis do Amazon CloudWatch são páginas de início personalizáveis no console do CloudWatch que você pode usar para monitorar os seus recursos em uma única visualização. Você pode criar visualizações personalizadas das métricas e alarmes para os seus recursos da AWS. 

- Dados de superfície sobre o seu ecossistema da AWS em execução
- Pode ser usado por meio de ferramentas de monitoramento existentes

## Ativar o monitoramento detalhado de instâncias
-  Por padrão, as instâncias do Amazon EC2 só relatam dados a cada 5 minutos (nível gratuito da AWS).
    -  Para obter mais informações sobre o nível gratuito da AWS, consulte a página do nível gratuito da AWS.
-  Habilitar o monitoramento detalhado em uma instância para aumentar a frequência de relatórios para uma vez por minuto.
    -  Cobranças adicionais aplicáveis


