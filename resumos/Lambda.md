# Lambda

## Computação sem servidor 
| Implantação e operações tradicionais | Implantação e operações sem servidor |
|---------------------------------------|-------------------------------------|
|Provisionar uma instância | |
| Atualizar o sistema operacional (SO) | |
| Instalar plataforma de aplicativos | |
| Criar e implantar aplicativos | Criar e implantar aplicativos |
| Configurar auto scaling e balanceamento de carga| |
| Corrigir, proteger e monitorar servidores regularmente| |
| Monitorar e manter aplicativos | Monitorar e manter aplicativos |


## O que é o lambda ?
- Computação sem servidor totalmente gerenciada
- Invocação orientada por eventos • Medição de frações de segundo
- O tempo de execução de uma função é limitado a no máximo 15 minutos
- Há várias opções de idioma

## AWS Lambda
 - O AWS Lambda permite que você execute código sem provisionar nem gerenciar servidores.
- Execute código para praticamente qualquer tipo de aplicativo ou serviço de back-end. Basta fazer upload de seu código que o Lambda se encarrega de todos os itens necessários para executá-lo e dimensioná-lo com alta disponibilidade.
- Configure seu código para ele ser acionado automaticamente por outros serviços da AWS ou o invoque diretamente de qualquer aplicativo web ou móvel.
- Pague apenas pelo tempo de computação que você consome. Você não paga nada quando seu código não está em execução.
- Com o AWS Lambda, não há novas linguagens, ferramentas ou frameworks para aprender. Você pode usar qualquer biblioteca de terceiros, até mesmo as nativas. O AWS Lambda comporta Java, Node.js, C#, Python e Ruby.

## Exemplo do Lambda AWS Lambda
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/65662ff1-24ef-4c47-b552-68fc0313d595)

## Etapas para implantar o AWS Lambda
1. Defina uma classe de manipulador do Lambda em seu código. O manipulador possibilita que você especifique onde o AWS Lambda pode começar a executar seu código.
2. Crie sua função do AWS Lambda. Você pode pensar na função como o código que deseja executar. Ela inclui seu código, informações de configuração correspondentes e requisitos de recursos.
3. Configure o acesso a recursos com o AWS Identity and Access Management (IAM) e funções do IAM. Você pode usar security groups e listas de controle de acesso à rede (ACLs de rede) para fornecer às funções acesso aos seus recursos.
4. Faça upload de seu código.
5. Teste a função, verifique os resultados e analise os logs.
6. Monitore suas funções do Lambda e métricas de relatórios por meio do Amazon CloudWatch.

## Camadas do Lambda 
Você pode configurar a função do Lambda para englobar o código adicional e o conteúdo em forma de camadas. 
Uma camada é um arquivo zip que contém bibliotecas, um tempo de execução personalizado ou outras dependências. 
Com camadas, você pode usar as bibliotecas em sua função sem a necessidade de incluí-las no pacote de implantação.

As camadas do Lambda permitem que os desenvolvedores:
- Configurem uma função do Lambda para usar bibliotecas que não estão incluídas no pacote de implantação.
    - A camada do Lambda é um arquivo zip com bibliotecas e um tempo de execução personalizado.
- Mantenham o pacote de implantação pequeno.
- Evitem erros de dependência de pacote no código.
- Compartilhem bibliotecas com outros desenvolvedores. 


## Limites do LambdaLimites de recursos por
- Limites de recursos por invocação, como memória, execução e duração
- Limites de conta por Região, como simultaneidade
- Limites de implantação, como tamanho do pacote
- As funções que excederem quaisquer limites apresentarão falha, com a exceção limites excedidos


