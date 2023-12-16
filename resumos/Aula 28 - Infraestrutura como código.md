# Aula 28 - Infraestrutura como código
## Provisionamento de recursos
O processo de criação de recursos de infraestrutura precisa ser consistente e confiável. 
A infraestrutura como código (IaC) é uma estrutura para implementar tais disciplinas. 
O AWS **CloudFormation** é um serviço para criar infraestrutura usando código.
Aqui estão alguns exemplos de quando implantações repetíveis e consistentes são necessárias: 
- A criação de ambientes de réplica para experimentação de novos serviços, testes em um espelho da infraestrutura de produção ou a implantação rápida de ambientes de recuperação após um desastre.
- A criação de ambientes temporários para demonstrações.
 Normalmente, quando um serviço está sendo demonstrado, ele é feito usando uma infraestrutura que não é um espelho de um ambiente real.
 Com a IaC, uma cópia da produção pode ser rapidamente implantada e usada para a demonstração.
- Para reduzir custos, os ambientes de desenvolvimento para programadores podem ser levantados quando necessário. Então, quando não for necessário, o ambiente poderá ser excluído.
 Essa flexibilidade não apenas economiza dinheiro, mas também garante que os desenvolvedores estejam criando um software que funcionará com os sistemas de produção atuais.

## Gerenciamento de configuração
Depois de provisionar seus recursos de infraestrutura e a infraestrutura estiver ativa e em execução, você deverá atender às necessidades contínuas de gerenciamento de configuração do ambiente.
Considere as seguintes situações:
- Um gerenciador de versões deseja implantar uma versão de um aplicativo em um grupo de servidores. Se forem encontrados problemas, os gerenciadores de versões desejam poder reverter para uma versão funcional.
- Um administrador do sistema recebe uma solicitação para instalar um novo pacote do sistema operacional em ambientes de desenvolvedor, mas para deixar os outros ambientes inalterados.
- Um administrador de aplicativos precisa atualizar periodicamente um arquivo de configuração em todos os servidores que armazenam um aplicativo.

Uma maneira de resolver essas situações é retornar ao estágio de provisionamento, provisionar novos recursos com as alterações necessárias e descartar os recursos antigos.
Essa abordagem, também conhecida como imutabilidade da infraestrutura, garante que os recursos provisionados sejam criados de novo de acordo com a linha de base do código sempre que uma alteração é feita.
Esse processo reduz o desvio de configuração. Um desvio de configuração significa que a configuração real dos recursos difere, ou se desviou, da configuração esperada.
No entanto, há momentos em que você pode querer adotar uma abordagem diferente. Alguns ambientes têm altos níveis de durabilidade nos quais transações ou dados são armazenados permanentemente. 
Portanto, as alterações confirmadas em um banco de dados podem ser recuperadas ou reconstruídas inteiramente. 
Para esses ambientes, talvez seja preferível estabelecer maneiras de fazer alterações incrementais nos recursos atuais em vez de reprovisioná-los. 
Você pode gerenciar essas alterações usando o **AWS Systems Manager** e o **AWS OpsWorks for Chef Automate**.
O AWS Systems Manager oferece aos engenheiros uma visão sobre a infraestrutura da AWS existente. 
Isso inclui automatizar muitas tarefas repetitivas e reduzir o tempo para identificar problemas operacionais. 
O **System Manager** também possui capacidade de automação para ajudar a melhorar a precisão e a eficiência das tarefas de manutenção.
Assim como o System Manager, o AWS Opswoks for Chef Automate pode ajudar a automatizar e melhorar a eficiência de muitas tarefas, fornecendo um servidor Chef gerenciado e ferramentas para ajudar com implantações, testes, segurança, bem como visibilidade e status dos recursos no ambiente de nuvem.


