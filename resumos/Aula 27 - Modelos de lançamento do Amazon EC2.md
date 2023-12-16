# Aula 27 - Modelos de lançamento do Amazon EC2
Os usuários podem executar instâncias usando vários métodos dos quais um modelo de inicialização é um. 
Outros métodos incluem o assistente, usando uma AMI ou um modelo do CloudFormation. As AMIs foram discutidas no módulo anterior.

## Criar um modelo de inicialização
**Modelos de inicialização**
Criar modelos para solicitações de inicialização de instâncias do EC2 
- Contém informações de configuração para executar uma instância do EC2.
- Permitem que você crie modelos para suas solicitações de inicialização.
- Você pode especificar as seguintes configurações: 
    - Tipo de instância
    - Sub-rede na qual iniciar a instância
    - Par de chaves
    - Grupo de segurança
- Especifique o modelo de inicialização a ser usado ao executar instâncias.  Você pode armazenar os parâmetros de inicialização para não precisar especificá-los toda vez que executar uma instância.
- você decide quais opções de inicialização incluir no modelo. Além disso, os modelos de inicialização fornecem os seguintes recursos:
    - Permite que você pré-selecione opções de inicialização do EC2.
    - Suporte ao versionamento.
- Oferecem os seguintes benefícios:
    - Racionalize e simplifique o processo de inicialização para o EC2 Auto Scaling, Spot Fleet, Instâncias Spot e Instâncias Sob Demanda.
    - Reduza o número de etapas necessárias para criar uma instância capturando todos os parâmetros de inicialização em um recurso.
    - Facilite a implementação de padrões e práticas recomendadas.
    - você percebe os seguintes benefícios adicionais
        - Ajuda no gerenciamento de custos
        - Melhora a segurança
        - Minimiza o risco de erros de implantação

## Versões de um modelo de inicialização Você pode criar versões de modelo de inicialização
Para cada modelo de inicialização, você pode criar uma ou mais versões de modelo de inicialização numeradas.
Cada versão pode ter diferentes parâmetros de inicialização.
- Use qualquer versão do modelo de inicialização.
- Defina qualquer versão do modelo de inicialização como a versão padrão.
- Por padrão, o modelo padrão é a primeira versão do modelo.



