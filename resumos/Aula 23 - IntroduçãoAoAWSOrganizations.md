# Aula 23 - introdução ao AWS Organizations
O AWS Organizations é um serviço de gerenciamento de contas que permite consolidar várias contas da AWS em uma organização que você cria e gerencia de forma centralizada. O AWS Organizations inclui recursos de faturamento consolidado e gerenciamento de contas, que ajudam a atender melhor às necessidades orçamentárias, de segurança e de compatibilidade da sua empresa.

## Principais recursos e benefícios 
**Gerenciamento baseado em políticas** - 
Crie políticas de controle de serviço (SCPs) que controlam
centralmente os serviços da AWS em várias contas da AWS.

**Gerenciamento de contas do grupo** - 
Crie grupos de contas e, em seguida, anexe políticas a eles.

**Gerenciamento de contas por meio de APIs** - 
Automatize a criação e o gerenciamento de novas contas da AWS

**Faturamento consolidado** - 
Revise uma visão combinada das cobranças incorridas por todas as suas contas

## Segurança com o AWS Organizations
- Controle o acesso com o AWS Identity and Access Management (IAM).
- As políticas do IAM permitem que você permita ou negue acesso aos serviços da AWS para usuários, grupos e funções.
- As políticas de controle de serviço (SCPs) permitem que você permita ou negue acesso aos serviços da AWS para contas individuais ou de grupo em uma unidade organizacional (UO).

O AWS Organizations não substitui a associação de políticas do AWS Identity and Access Management (IAM) a usuários, grupos e funções em uma conta da AWS.
Com o Organizations, você usa políticas de controle de serviço (SCPs) para permitir ou negar acesso a determinados serviços da AWS para contas individuais da AWS ou para grupos de contas em uma UO.
As ações especificadas de uma SCP anexada afetam todos os usuários, grupos e funções do IAM de uma conta, incluindo o usuário raiz da conta da AWS.

## Configuração do AWS Organization
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/16e1726f-184d-4721-9712-67d44cfd21d7)

## Regras de Nomenclatura
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/9cf1425b-5e48-49e4-a7ee-b6113e08b140)

## Acessar o AWS Organizations
O AWS Organizations é disponibilizado para todos os clientes da AWS sem cobranças adicionais. Ele pode ser gerenciado por meio de diferentes interfaces:

**Console de Gerenciamento da AWS** - Interface baseada em navegador que você pode usar para gerenciar sua organização e seus recursos da AWS.

**AWS Command Line Interface (AWS CLI)** - Emita comandos por meio da AWS CLI para executar tarefas do AWS Organizations e da AWS.

**Kits de desenvolvimento de software (SDKs)** - Assine solicitações criptograficamente, gerencie erros e tente novamente Acesso programático ao AWS Organizations e à AWS.

**Consulta HTTPS** - solicitações automaticamente. 

