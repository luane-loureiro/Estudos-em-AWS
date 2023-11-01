# Aula 57 - AWS Step Functions
O AWS Step Functions permite coordenar serviços da AWS em fluxos de trabalho sem servidor.
- Os fluxos de trabalho consistem em uma série de etapas.
- A saída de uma etapa é a entrada para a próxima etapa.

 Principais benefícios:
- Criar e atualizar aplicativos distribuídos.
- Escrever menos código.

## Benefícios do AWS Step Functions 
#### Produtividade
- Facilidade para conectar e coordenar componentes e microsserviços distribuídos para criar aplicativos rapidamente
- Você pode ter mais tempo para pensar sobre como inovar a lógica de negócios que torna o aplicativo exclusivo.
- Os aplicativos podem se tornar mais fáceis de operar e mante
 
      
#### Agilidade
- Possibilidade de diagnosticar e depurar problemas mais rapidamente.
- registra um histórico toda vez em que ele é executado, para que você possa revisar todos os eventos na sequência em um único local.
- Você pode dimensionar de um tempo de execução para milhares de tempos de execução simultâneos, especialmente quando ele é usado com outros recursos sem servidor da AWS. Alguns exemplos de recurso incluem o AWS Lambda, o Amazon Simple Storage Service (Amazon S3) e o Amazon DynamoDB.
- Com o Step Functions, você paga apenas pelo que usa, quando usa.

      
#### Resiliência
- Gerenciamento das operações e da infraestrutura da coordenação de serviços para garantir disponibilidade em escala e em caso de falha
- comporta o tratamento automático de erros para oferecer saídas normais.
- Ele opera em escala, e você não precisa configurar nem gerenciar recursos subjacentes.


## Como o AWS Step Functions funciona 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/de9f6f04-63ee-4a58-acc6-802ef4dc2cf9)


- O AWS Step Functions funciona por meio de fluxos de trabalho configurados que você define.
- Você coordena tarefas específicas expressando seu fluxo de trabalho como uma máquina de estado.
- Os estados específicos tomam decisões com base em seus dados de entrada, executam ações e transmitem os dados de saída para outros estados.
- O console do Step Functions fornece uma representação gráfica dessa máquina de estado para ajudar a visualizar a lógica do aplicativo.


## Casos de Uso
### Alguns exemplos de casos de uso do AWS Step Functions
- Processamento de dados: consolide dados de vários bancos de dados em relatórios unificados.
- DevOps e automação de TI: crie ferramentas para integração e implantação contínuas.
- Comércio eletrônico: automatize o atendimento de pedidos e o monitoramento de inventário.
- Aplicativos web: processos de registro de usuários e autenticação de logon

