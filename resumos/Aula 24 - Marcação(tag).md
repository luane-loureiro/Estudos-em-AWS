# Marcação (Tags)

## O que é uma tag?
- É um par de chave-valor que pode ser anexado a um recurso da AWS.
- Permite identificar e categorizar recursos.

Tag é um rótulo que você atribui a um recurso da AWS. Ele permite que você o identifique ou categorize de forma significativa. Uma tag consiste em uma chave e um valor, ambos os quais você define.


## Características de tag 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/43b3c785-eeec-4cda-bd97-864fbf42b17c)


## Exemplos de tags comuns:
- Ambiente (produção, teste)
- Aplicativo 
- Proprietário
- Departamento
- Centro de custos
- Objetivo Pilha

## AWS Config e atribuição de tags 
O AWS Config fornece um mecanismo para impor a atribuição de tags em um recurso:
- Use a regra gerenciada required-tags.
- Especifique a chave de tag necessária (e, opcionalmente, o valor necessário).
- Avalia regras e identifica recursos que não estão em conformidade.

O AWS Config fornece as regras gerenciadas da AWS, que são regras predefinidas e personalizáveis que o AWS Config usa para avaliar se as configurações de recursos da AWS são compatíveis com as práticas recomendadas. 
Você pode personalizar o comportamento de uma regra gerenciada para atender às suas necessidades. 
Por exemplo, você pode usar a regra gerenciada required-tags para avaliar rapidamente se uma tag específica é aplicada aos seus recursos. 
Essa regra permite que você especifique a chave da tag necessária e, opcionalmente, seu valor. 
Depois de ativar a regra, o AWS Config compara seus recursos com as condições definidas e relata quaisquer recursos que não estejam em conformidade. 
A avaliação de uma regra gerenciada pode ocorrer quando um recurso muda ou periodicamente.

## Atribuição de tags na AWS CLI 
Criando uma Tag:

```
export TIMESTAMP=`date`
aws ec2 create-tags
--resources i-1234567890abcdef0
--tags "Key=SecurityCheck,Value=$TIMESTAMP"
```

 Consultar e filtrar com base em uma tag
 
```
aws ec2 describe-instances
--filters
"Name=tag-key,Values=SecurityCheck"
--query
"Reservations[].Instances[].[InstanceId,Tags[?Key=='SecurityCheck'].Value]"
```

## Casos de uso comuns
Casos de uso comuns para atribuição de tag:
- Inicie ou encerre simultaneamente instâncias que têm uma tag específica. Por exemplo, desligue todas as instâncias de desenvolvimento nos fins de semana.
- Imponha requisitos de atribuição de tags para padrões corporativos.
- Marcar ou encerrar (Conformity Monkey)
- Pseudocódigo (mostrado)

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fd8f24e3-8e35-4e14-ab39-6145ec4033c5)

## Impor a atribuição de tags com o IAM 
Você também pode escrever políticas de IAM que imponham o uso de tags específicas. 
Por exemplo, ao criar um recurso, você pode usar uma política do IAM para impor o uso das tags departmento e centro de custo para ajudá-lo a obter relatórios mais precisos para alocação de custos. 
Você também pode escrever políticas do IAM que impõem o uso de tags específicas.
- Bloqueando a exclusão de tags exigidas pelos padrões corporativos
- Desautorizando a criação de novas tags para recursos existentes específicos
- Exigir o uso de criptografia para qualquer volume do EBS criado com um valor de tag específico


## Práticas recomendadas de atribuição de tags
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/6f981f2d-e072-4fbc-8863-57509c4455e6)

ma prática recomendada é usar ferramentas automatizadas para gerenciar tags de recursos, como a Interface de programação de aplicativos (API) de marcação de grupos de recursos. 
Essa API permite o controle programático de tags. Essa prática facilita o gerenciamento, a pesquisa e a filtragem de tags e recursos automaticamente. 
Por exemplo, você pode usar a API para executar as seguintes tarefas:
- Marcar e desmarcar recursos compatíveis.
- Usar filtros baseados em tag para pesquisar recursos.
- Listar todas as chaves de tag existentes.
- Listar todos os valores existentes para chaves especificadas.

