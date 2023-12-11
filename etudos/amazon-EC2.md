# Amazon EC2 
## Tipos de Instacias Do Amazon EC2
- São otmizados para tarefas diferentes. Ao selecionar um tipo de instância, considere as nececidades específicas de suas cargas de trabalho e suas aplicações.
- Esses recursos podem incluir requisitos para recursos de computação, memória ou armazenamento.

### Instância de uso geral - Equilíbrio
Essas instancias equilibram os recurss de computação, memória e rede.
Você pode usa-las para diversas cargas de trabalho, como:
- Servidores de aplicações
- Servidores de Jogos
- Servidores de back-end para aplicações emporesariais
- Bancos de dados pequenos e médios.

### Instâncias otmizadas para Computação - Alto desepenho de processamento
São ideais para aplicações de computação que usam processadores de alto desempenho. assim como as instâncias de uso geral, você pode usar as intâncias otmizadas para computação para cargas de trabalho, como servidores de web, de aplicações e de jogos.
A diferença é que as aplicações otmizadas para computação ão ideiais para:
- servidores web de alto desempenho
- servidores de aplicações de computação intensiva
- servidores dedicados de jogos.

### Instâncias Otmizadas para memória - carregamento rápido para cargas de trabalho
as inâncias otmizadas para memória permitem que você execute cargas de trabalho com altas nececidades de memoria e tenha um otimo desempenho.
Tem desempenho rapido para cargas de trabalho que processam grandes consuntos de dados na memória. Na computação, a memória é uma área de armazenamento temporário.  Ela contem todos os dados e instruçoes de que uma unidade central de processamento (CPU) precisa para conseguir realizar ações. Antes que um programa de computador ou aplicativo posa ser executado ele é carregado e armazenado para a memória.
suponha que uma carga de trabalho exija o pré-carregameto de muitos dados antes de executar uma ação, como por exemplo:
- banco de dados de alto desempenho
- cargas de trabalho que envolva a execução de processamento em tempo real de uma grande quantidade de dados não estruturado


### Instâncias de computação aceleda - Aceleradores Graficos
usam celeradores de hadware ou co processadores, para executar algumas funçoes de maneira mais eficientes do que é possivel em um software executados em CPUS
exemplos dessas funções são:
- Calculos acelerados de números com virgulas flutuantes
- aplicativos gráficos gráficos
- correspondencias de padroes de dados
- streeming de jogos e de aplicativos

### Instancias otmizadas para armazenamenro - HD
São projetadas para cargas de trabalho que exigem alto acesso sequencial de leitura e gravação de dados no armazenamento local.
Exemplos de cargas de trabalho são:
- armazenamnto de sistemas de arquivos distribuidos
- aplicação de data werehouse
- sistemas de processamentos online de alta frequencia


## Definições de Preços do Amazon EC2
Com o amazon EC2, você paga apenas pelo tempo de computação que usar. O amazon EC2 oferece diversas opções de preço para diferentes casos de uso.

### Sob Demanda
- Ideais para cargas de trabalho irregulares de curto prazo que não podem ser iterrompidas. 
- Custos antecipados ou contratos não se aplicam.
- As instancias são executadas continuamnente até que sejam interrompidas, e você paga apenas pelo tempo de computação usado.

### Instancias Reservadas
- São um desconto de cobrança aplicado ao uso de instâncias sob demanda na sua conta. Há dois tipos disponíveis de instância reservada:
    **-  Standard Reservad Instances** essa opção será adequada se você souber o tipo e tamanho da instancia EC2 de que precisa para suas aplicações com estado pronto em qual Região da aws planeja executa-las. As instancias reservadas exigem que você declare as seguintes qualificações: tipo etamanho da instancia, descricao da plataforma (sistema operacional) e tenancy padrão.
  
    **-  Instâncias reservadas conversiveis** se você precisar executar suas instancias do EC2 em diferentes zonas de disponibilidade ou diferentes zonas de disponibilidade ou diferentes tipos de instancias, as instancias reservadas conversiveis poderão ser adequadas para você.

  No final de um preríodo de vigência de instancia reservada você pode continuar usando a instancia do amazon EC2sem interrupção . No entanto, são cobrados os preços de instancias sob demanda até um dos procedmentos a seguir seja feito:
  - Trminar a Instância
  - Adquirir uma nova instância reservada que corresponda aos atributos de instância (tamanho e familia de instância, região, plataforma e tenancy)


### Savings Plans da Instância EC2
os savings plans reduzem o custo da intância do EC2 quando você assume um compromissso de gasto por hora com uma familia  de instância e uma região por um periodo de um ou três anos.
esse compromisso com o periodo de vigênciaresulta em uma economia de 72% em comparação com as taxas sob demanda. Qualquer uso até o compromisso é cobrado de acordo com o preço de saving plans, quaqluer uso além do compromisso é cobrado de acordo com as normas de instância sob demanda.
Ao contrario das instancias reservadas, no entanto, você não precisa especificar antecipadamente qual tipo e tamanho da instância do EC2, sistema operacional, e tenancy para receber desconto.  Além disso , você você não precisa se comprometer com um determinado numero de instâncias do EC2 durante um periodo de vigencia de um ou três anos.

### Instâncias Spot 
São ideais para cargas de trabalho com horarios de início e termino flexiveis ou que toleram interrupições. As Instâncias spot usam a capacidade de computção não utilizadas do amazon EC2 e tem até 90% de desconto em relação ao preços de instâncias sob demanda.

### Host dedicados
são servodores físicos com capacidade de instancia EC2 totalmente dedicada ao uso do cliente.
você pode usar suas licenças de software por soquete, por nucleo ou por VM para manter a conformidade da licença. Você pode adquirir hosts dedicados sob demanda e reservas de hosts dedicados. De todas as opçoçoes do amazon EC2 que foram abordadas, od hosts dedicados são os mais caros.








