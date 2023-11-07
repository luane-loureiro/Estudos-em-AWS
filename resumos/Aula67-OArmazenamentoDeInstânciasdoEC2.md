# Aula 67 - O armazenamento de instâncias do EC2

Os armazenamentos de instâncias fornecem armazenamento temporário em nível de bloco para a instância. Esse armazenamento está localizado em discos que estão anexados fisicamente ao computador host.

## Armazenamento de instâncias do Amazon EC2
- Fornece armazenamento temporário para suas instâncias do EC2
- Esse armazenamento está fisicamente conectado ao host da instância do EC2.
- Um armazenamento de instâncias é feito de volumes de armazenamento de instâncias também chamados de unidades temporárias (blocos de dados)
- O armazenamento não é persistente: os dados são recuperados quando a instância do EC2 é encerrada
- Um armazenamento de instâncias é dedicado a uma instância específica do EC2
- É um armazenamento rápido e de baixa latência

#### Como fazer interface com a instância do Amazon EC2
- Os volumes de armazenamento de instâncias não têm sua própria interface de programação de aplicativos (API).
- Os volumes de armazenamento de instâncias são especificados usando o recurso de mapeamento de dispositivos de blocos da API do Amazon EC2 e do Console de gerenciamento da AWS.
- Você não pode criar ou destruir volumes de armazenamento de instâncias, mas você pode controlar esses aspectos
    - Se eles estão expostos à instância do EC2
    - Qual nome de dispositivo é usado
 

### Volumes de armazenamento de instâncias Principais recursos e montagem
- Os armazenamentos de instâncias estão disponíveis para vários tipos de instâncias, mas nem todos os tipos de instâncias.

- Número, tamanho e tipo — como unidade de disco rígido (HDD) em comparação à unidade de estado sólido (SSD) — diferem por tipo de instância
    - Os armazenamentos de instâncias que usam Non-Volatile Memory Express (NVMe) têm maior desempenho de E/S.

- Montagem
    - O armazenamento de instâncias deve ser montado antes que você possa acessá-lo
    - Montado automaticamente pelo serviço Microsoft Windows EC2Launch
    - Montado automaticamente ou manualmente no Linux, dependendo do tipo de instância
 
  ## Casos de uso do armazenamento de instância da AWS

  ### Armazenamento de instâncias do Amazon EC2 Padrões de casos de uso
- Armazenamento temporário de informações que estão mudando continuamente.
      - Buffers, caches, dados de rascunho ou outro conteúdo temporário.

- Dados replicados em uma frota de instâncias
      - Exemplo: pool de servidores Web com balanceamento de carga.

