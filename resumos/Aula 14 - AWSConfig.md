# Aula 14 - AWS Config
## Introdução ao AWS Config
O AWS Config é um serviço totalmente gerenciado que permite avaliar, analisar e fazer auditoria da configuração dos seus recursos da AWS.
- Monitoramento quase contínuo
- Avaliação quase contínua Gerenciamento de alterações]
- Solução de problemas operacionais

## Rastreie as alterações nos recursos
O AWS Config fornece inventário de recursos da AWS, histórico de configuração e notificações de alteração de configuração para proporcionar segurança e governança.
Com o AWS Config, você pode: 
- Descobrir os recursos existentes da AWS
- Exportar um inventário completo de seus recursos da AWS com todos os detalhes de configuração
- Determinar como um recurso foi configurado em qualquer momento

Esses recursos permitem auditoria de conformidade, análise de segurança, rastreamento de alteração de recursos e solução de problemas. De valor específico são:
- **DETECÇÃO**
  - Crie controles de detecção e identifique e analise anomalias.

- **CONFORMIDADE**
  - Crie regras que avaliem a conformidade de recursos e auxiliem no alinhamento com as certificações SOC.
  - Revise as alterações nas configurações e nas relações entre os recursos da AWS

- **CONTROLE DE ACESSO**
  - Crie funções do IAM que concedam permissões do AWS Config para acessar recursos como buckets do S3
  - Crie funções vinculadas ao serviço ligadas ao AWS Config que incluam todas as permissões que o Config exige para chamar outros serviços em nome do usuário.

- **CRIPTOGRAFIA/DADOS EM REPOUSO**
  -  O AWS Config cria um item de configuração sempre que detecta uma alteração em um tipo de recurso que está registrando. Os componentes de um item de configuração incluem metadados, atributos, relações, configuração atual e eventos relacionados.

## Visão geral do AWS Config

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/caedb03c-6199-4f18-829f-27550a168e42)


## Desafio Emprsarial
É comum que um cliente execute centenas, até mesmo milhares, de instâncias do Amazon Elastic Compute Cloud (Amazon EC2) nas contas da AWS. Outros recursos na conta da AWS também podem existir em grande número. A capacidade de gerenciar a configuração de todos esses recursos apresenta um desafio.
Talvez você saiba qual deve ser a configuração atual dos recursos implantados. No entanto, você tem visibilidade sobre os possíveis erros de configuração e tem um sistema para gerenciar e rastrear as alterações de configuração?

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/bc0eb8a4-74f5-4529-90ed-79d25ea37a0f)


## Grenciamento de configuração Usando o AWS Config
O AWS Config também monitora e registra de forma quase contínua suas configurações de recursos da AWS. É possível automatizar a avaliação das configurações registradas em relação às configurações desejadas.
Com o AWS Config, você pode realizar as seguintes tarefas: 
- Recuperar um inventário de recursos da AWS. 
- Descobrir recursos novos e excluídos.
- Registrar as alterações de configuração de forma quase contínua. Determinar a conformidade geral em relação às configurações especificadas pelas diretrizes internas.
- Ser notificado quando as configurações mudarem e analisar os históricos detalhados de configuração de recursos.

  
## Regras do AWS Config
O AWS Config fornece um sistema de regras. Você pode usar as regras existentes da AWS e de parceiros da AWS. Você também pode definir suas próprias regras personalizadas usando o AWS Lambda. O AWS Lambda é um serviço da web que permite executar código sem provisionar ou gerenciar servidores.
É possível direcionar regras a recursos específicos, tipos específicos de recursos ou a recursos marcados de uma forma particular. As regras são executadas quando esses recursos são criados ou alterados e também podem ser avaliadas periodicamente (por hora, diariamente e assim por diante).
Você pode configurar regras para verificar se as alterações de configuração são gravadas. Depois de configurar o AWS Config, ele fornece um painel para visualizar a conformidade. Você também pode usar o painel para identificar alterações nos recursos que possam ser preocupantes.
O AWS Config é invocado automaticamente para que as configurações sejam avaliadas de forma quase contínua.

Use as regras do AWS Config quando:
- Configurar regras para verificar as alterações de configuração registradas.
- Usar regras gerenciadas predefinidas ou criar regras personalizadas.
- Redigir regras personalizadas usando o AWS Lambda.
- Ver um painel para visualizar a conformidade e identificar as alterações que possam ser preocupantes.
- As regras são invocadas automaticamente para uma avaliação quase contínua.




