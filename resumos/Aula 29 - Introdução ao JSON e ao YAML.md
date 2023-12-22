# Aula 29 - Introdução ao JSON e ao YAML

## YAML e JSON: sintaxes para definir a infraestrutura de nuvem
Alguns dos serviços da AWS discutidos posteriormente neste módulo, como o AWS CloudFormation, oferecem suporte ao JavaScript Object Notation (JSON) como um formato de dados. 
O AWS CloudFormation é um serviço para escrever ou alterar modelos que criam e excluem recursos relacionados da AWS juntos como uma unidade (pilha). 
Para provisionar e configurar seus recursos de pilha, você deve entender os modelos do AWS CloudFormation, que são arquivos de texto formatados em JSON ou YAML.


### A linguagem da infraestrutura - JSON & YAML: linguagens declarativas para criar infraestruturas de nuvem
- Infraestrutura como código (IaC) é um método para declarar os recursos necessários na nuvem ao usar arquivos de texto
- As sintaxes JavaScript Object Notation (JSON) e YAML Ain't Markup (YAML) são usadas pela AWS para declarar recursos na nuvem
- Permite a definição de infraestruturas simples a complexas no texto • Compreender as sintaxes de JSON e YAML é necessário para construir a infraestrutura como código


## Introdução ao JSON
### O que é JSON?
JSON é uma sintaxe para armazenar e transportar dados. Ele é um formato baseado em texto e, portanto, é legível por humanos. 
Os documentos JSON são facilmente gravados. Eles armazenam pares de chave-valor e arrays de dados.
Um par de chave-valor é um conjunto de dois itens de dados vinculados: 

- Chave — Identificador exclusivo para um item de dados. 
    
    ````{Key1: “Value1”, Key2: “Value2”}````
          
- Valor — Dados identificados ou um ponteiro para o local desses dados.
    
    ````{Array: [1, 2, 3]}````
    
Os dados podem ser estruturados para que você possa armazenar estruturas de dados muito complexas em um único documento JSON. 
O principal caso de uso para JSON é que ele oferece suporte à simples troca de dados complexos entre sistemas de computador.

### Representação de Dados
Normalmente, você vê dados em um formato colunar, como em uma tabela. No entanto, para armazenar dados de tabela de forma fácil para as máquinas ingerirem, analisarem e distribuírem, eles devem ser armazenados de forma não gráfica.
JSON fornece uma maneira de armazenar objetos de dados em um documento de texto legível por humanos. 

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e2cf924a-0b96-4a61-beff-eba205a07418)


### Vantagens e Desvantagens do JSON
#### Vantagens
- Leve (sintaxe e demonstração mínimas) - bom para interfaces de programação de aplicativos (APIs).
- Fácil para humanos lerem e escreverem.
- Fácil para máquinas analisarem e gerarem.

#### Desvantagens
- Sem suporte nativo para dados binários (como arquivos de imagem)

