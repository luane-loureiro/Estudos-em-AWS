# Aula 26 - Estratégia de construção da AMI
## O que é uma Imagem de máquina da Amazon (AMI)? 
Uma imagem de máquina da Amazon (AMI) fornece as informações necessárias para iniciar uma instância. 
Você deve especificar uma AMI ao iniciar uma instância. Se você precisar de várias instâncias com a mesma configuração, poderá executar várias instâncias a partir de uma única AMI. 
Se você precisar de instâncias com configurações diferentes, poderá usar AMIs diferentes para executar instâncias.

## AMIs personalizadas como uma configuração base
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/03e146c4-7838-4abc-bb26-908c3825542e)
Suponha que sua organização tenha solicitado que todas as instâncias do EC2 executadas na Nuvem AWS tenham um conjunto básico de software pré-instalado nelas. Isso pode incluir utilitários que a organização desenvolve, ferramentas internas para usar os serviços da AWS e software avançado para atividades de escala corporativa, como monitoramento e detecção de intrusões.
Considerando esses requisitos, você pode considerar o desenvolvimento de uma ou mais AMIs personalizadas como uma configuração básica. Para realizar essa tarefa, siga estas etapas: 
1. Execute uma instância do EC2 a partir de uma AMI padrão.
2. Pré-configure todo o software que sua organização exige em uma instância do Amazon EC2.
3. Crie uma AMI personalizada a partir dessa instância.

A nova AMI personalizada se torna a AMI usada para criar todas as novas instâncias na organização.
Para impor a política de que todas as novas instâncias sejam executadas somente a partir da nova AMI base, faça o seguinte: 
- Crie processos que examinam as instâncias do Amazon EC2 em execução na sua conta.
- Encerre todas as instâncias que não estiverem usando as AMIs padrão.

## Configurar instâncias no momento da inicialização 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/e6d75312-165b-4d85-8faf-cbba8a56ceef)

Outra opção é configurar instâncias no momento da inicialização. Um exemplo de configuração de uma instância no momento da inicialização é o uso da opção de dados do usuário para executar um script quando você executa uma instância do EC2.
Conforme mostrado no gráfico, essa abordagem é compatível com a criação de AMIs personalizadas. Muitas organizações adotam uma abordagem híbrida, em que algumas configurações são incorporadas a uma AMI de base personalizada e outras configurações são configuradas dinamicamente no lançamento.
A abordagem ideal normalmente é determinada considerando as compensações entre simplicidade e flexibilidade.
Considere esses fatores:
- **Tempos de compilação** — Uma AMI com pré-requisitos e configurações pré-instaladas aumenta o tempo necessário para produzir uma compilação.
- **Tempos de inicialização** — Uma AMI com uma configuração somente de sistema operacional (SO) leva muito tempo para inicializar quando uma nova instância é inicializada. O empacotamento de pré-requisitos em uma AMI personalizada reduz os tempos de inicialização.
- **Prazo de validade** — Quando você instala mais pré-requisitos em uma AMI, corre um risco maior de que seu aplicativo fique vulnerável a um risco de segurança. O risco existe se a AMI subjacente não for atualizada com frequência com atualizações de segurança ou de aplicativos. Avalie o risco que as atualizações para suas dependências representam.

Em resumo, cada abordagem cria vantagens:
- **AMI completa** — Os aplicativos e todas as dependências são pré-instalados, o que reduz os tempos de inicialização, mas aumenta o tempo de compilação. As AMIs completas geralmente têm uma vida útil mais curta. Considere a sua estratégia de reversão.
- **AMIs parcialmente configuradas** — Somente software e utilitários de pré-requisito são pré-instalados, o que leva a uma vida útil mais longa para a AMI. Essa abordagem fornece um equilíbrio entre a velocidade de inicialização e o tempo de compilação. As reversões se tornam mais fáceis.
- **AMI somente para sistema operacional** — Essa abordagem é totalmente configurável e atualizável ao longo do tempo e reduz os tempos de compilação. No entanto, ela torna as suas instâncias do EC2 lentas para inicializar, pois todas as instalações e configurações necessárias devem ser executadas no momento da inicialização.

## Criar AMIs
Para criar uma AMI, você pode usar qualquer uma das seguintes ferramentas: • Console de Gerenciamento da AWS • AWS Command Line Interface (AWS CLI) • Interface de programação de aplicativos (API) da AWS
Criação de AMIs resulta no seguinte: 
- A AMI resultante está ancorada na região atual da AWS.
- A instância é reinicializada por padrão para garantir a consistência.
- AMIs baseadas no Amazon Elastic Block Store (Amazon EBS) criadas com todos os volumes anexados.

```
aws ec2 create-image
–-instance-id i-1234567890abcdef0
–-name "Our_Base_Image-2018-09-17"
```

## Copiar AMIs para diferentes regiões da AWS
Uma AMI está ancorada no nível da Região. Como resultado, se você quiser executar uma instância do EC2 de uma AMI criada em uma região diferente, deverá primeiro copiar a AMI para a região de destino. 
Você pode copiar uma AMI em uma região da AWS ou em uma região da AWS usando um dos seguintes métodos: 
- Console de Gerenciamento da AWS
- AWS CLI
- API do Amazon EC2
  
Considerações para copiar AMIs: 
- Copie a AMI explicitamente.
- Use um dos seguintes métodos de cópia:
    - No Console de gerenciamento da AWS, escolha Copiar AMI.
    - Na linha de comando, execute aws ec2 copy-image.

```
aws ec2 copy-image
–-source-image-id ami-1234567890abcdef0
–-source-region us-east-1
–-region ap-northeast-1
–-name "My server"
```

Você pode copiar as AMIs baseadas no Amazon EBS e AMIs com armazenamento de instâncias. Você pode copiar AMIs criptografadas e AMIs com snapshots criptografados.

### Snapshots criptografados
Você pode criptografar snapshots com sua chave mestra de cliente (CMK) padrão do AWS Key Management Service (AWS KMS) ou uma chave personalizada especificada. 
Em todos os casos, você deve ter permissão para usar a chave selecionada. 
Se você tiver uma AMI com snapshots criptografados, poderá optar por criptografá-los novamente com uma chave de criptografia diferente como parte da ação CopyImage.
A CopyImage aceita apenas uma chave por vez e criptografa todos os instantâneos de uma imagem (seja raiz ou dados) para essa chave. 
No entanto, você pode criar manualmente uma AMI com snapshots criptografados com várias chaves


## Detalhes da Craição de Uma AMI
Quando você cria uma AMI, o Amazon EC2 cria snapshots do volume raiz da instância e de quaisquer outros volumes do EBS anexados à sua instância. 
Você é cobrado pelos snapshots até que você cancele o registro da AMI e exclua os snapshots.
Para criar uma AMI do Linux baseada no Amazon EBS, comece de uma instância que você executou de uma AMI do Linux baseada no Amazon EBS existente. 
Essa AMI pode ser uma AMI obtida do AWS Marketplace, uma AMI importada ou qualquer outra AMI que você possa acessar.
Você também pode criar AMIs do Linux diretamente do snapshot do volume raiz da instância do EC2

## Criando AMIs do Microsoft Windows
Práticas recomendadas para criar AMIs do Microsoft Windows:
- Execute a ferramenta Sysprep em uma instância do EC2 antes de criar uma AMI a partir dela.
- Para o Windows Server 2016 ou posterior, execute a Sysprep com o EC2Launch.
- Para versões do Windows Server anteriores a 2016, execute a Sysprep com EC2Config.


A ferramenta **Microsoft System Preparation (Sysprep)** simplifica o processo de duplicar uma instalação personalizada do Windows. 
Recomendamos que você use o Sysprep para criar uma AMI padronizada. Você pode criar novas instâncias do Amazon EC2 para o Windows desta imagem padronizada. 
Também recomendamos que você execute o Sysprep com o EC2Launch (Windows Server 2016 e posterior) ou o serviço EC2Config (antes do Windows Server 2016).


### Inicialização do EC2 
O serviço EC2Launch é iniciado quando a instância é inicializada e executa tarefas durante a inicialização. 
Exemplos de tarefas incluem definir o nome do computador, enviar informações da instância para o console do EC2, definir uma senha aleatória para a conta de usuário do Administrador do Windows e muito mais.

### Configuração do EC2 
As AMIs do Microsoft Windows para Windows Server 2012 R2 e anteriores incluem um serviço opcional, o serviço EC2Config (EC2Config.exe). 
O EC2Config começa quando a instância é inicializada. Ele executa tarefas durante a inicialização e cada vez que você interrompe ou inicia a instância. 
O EC2Config também executa tarefas sob demanda. Algumas dessas tarefas são ativadas automaticamente, enquanto outras devem ser ativadas manualmente. 
Embora esse serviço seja opcional, ele fornece acesso a recursos avançados que não estão disponíveis de outra forma.


No entanto, não use o Sysprep para criar um backup de instância do EC2.
O Sysprep remove informações específicas do sistema. Remover tais informações pode ter consequências indesejadas para um backup de instância. 
O Sysprep é usado para preparar uma imagem do EC2 para criação de AMI removendo as ferramentas específicas da imagem, a configuração e a identificação do usuário no sistema Windows.

## Fases do Sysprep 
O Sysprep é executado nas seguintes fases:
- **Generalizar** — A ferramenta remove informações e configurações específicas da imagem. Por exemplo, o Sysprep remove o identificador de segurança (SID), o nome do computador, os logs de evento e os drivers específicos, entre outros. Após essa fase ser encerrada, o sistema operacional (SO) estará pronto para criar a AMI.
- **Especializar** — O Plug and Play verifica o computador e instala drivers para todos os dispositivos detectados. A ferramenta gera requisitos do sistema operacional, como o nome do computador e o SID. Você pode executar comandos nessa fase.
- **Out-of-Box Experience (OOBE)** — O sistema executa uma versão abreviada da configuração do Windows. Ele solicita que o usuário insira informações como um idioma do sistema, o fuso horário e uma organização registrada. Quando você executa o Sysprep com o EC2Config, o arquivo de resposta automatiza essa fase.






