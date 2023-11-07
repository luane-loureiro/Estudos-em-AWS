# Aula 66 - Amazon EBS

## Amazon Elastic Block Store (Amazon EBS) 

### Serviços de armazenamento da AWS
- O armazenamento de instâncias ou armazenamento temporário, é um armazenamento temporário que é adicionado à sua instância do Amazon Elastic Compute Cloud (Amazon EC2).
- O Amazon EBS é um armazenamento persistente e montável. Um volume do EBS pode ser montado como um dispositivo para uma instância do EC2, mas somente se ambos estiverem na mesma zona de disponibilidade.
- Semelhante ao Amazon EBS, o Amazon S3 é um armazenamento persistente. No entanto, ele pode ser acessado de qualquer lugar.

### Armazenamento em nível de bloco em comparação ao armazenamento em nível de objeto
#### Armazenamento em bloco 
- Altere um bloco (parte do arquivo) que contém o caractere.
  
#### Armazenamento de objetos 
- O arquivo inteiro deve ser atualizado.
  
#### Diferença 
- Essa diferença tem um grande impacto na taxa de transferência, na latência e no custo da sua solução de armazenamento

## Amazon Elastic Block Store (Amazon EBS)

### O que é o Amazon EBS?
- O Amazon EBS fornece volumes persistentes de armazenamento em bloco
- Cada volume do EBS é replicado automaticamente na sua Zona de disponibilidade.
- Com o Amazon EBS, você pode aumentar ou diminuir a sua escala de utilização em minutos.

Como mencionado anteriormente, o Amazon EBS fornece volumes persistentes de armazenamento em bloco para uso com instâncias do EC2. 
Lembre-se de que o armazenamento persistente é qualquer dispositivo de armazenamento de dados que retém dados depois que a alimentação desse dispositivo é desligada. Às vezes, também é chamado de armazenamento não volátil.
Cada volume do EBS é replicado automaticamente na sua Zona de disponibilidade para protegê-lo contra falhas de componentes, oferecendo alta disponibilidade e durabilidade. 
Os volumes do EBS oferecem o desempenho consistente e de baixa latência de que você precisa para executar suas cargas de trabalho.

### Amazon EBS O Amazon EBS oferece armazenamento em nível de blocos.
- Você pode usar o Amazon EBS para criar volumes de armazenamento individuais e anexá-los a uma instância do Amazon EC2.
    - Os volumes são replicados automaticamente na sua zona de disponibilidade
    - Pode ser feito backup automaticamente para o Amazon S3
- Usos:
    - Volumes de inicialização e armazenamento para instâncias do Amazon EC2
    - Armazenamento de dados com um sistema de arquivos – Hosts de banco de dados
    - Aplicações empresariais

### Amazon EBS Snapshots, criptografia, elasticidade
#### Snapshots:
- Snapshots pontuais
- Recrie um novo volume a qualquer momento

#### Criptografia:
- Volumes do EBS criptografados
- Sem custo adicional

#### Elasticidade: 
- Aumentar a capacidade
- Alteração para diferentes tipos


### Amazon EBS: custos Snapshots e transferência de dados
Snapshots 
- O custo adicional dos snapshots do Amazon EBS para o Amazon S3 é calculado por GB/mês de dados armazenados

## Tipos de volume do EBS
### Amazon EBS — Volumes e IOPS
#### Volumes
- Os volumes do EBS persistem independentemente da instância.
- Todos os tipos de volume são cobrados pelo valor provisionado por mês.

#### Operações de entrada/saída por segundo (IOPS)
- ****Uso geral (SSD)****
    - Cobrado pelo valor provisionado em GB por mês até que o armazenamento seja liberado

- ****Magnético****
    - Cobrado pelo número de solicitações de volume

- ****IOPS provisionadas (SSD)****
    - Cobrado pelo valor provisionado em IOPS (por porcentagem de dia ou mês usado)
 
### Tipos de volume do Amazon EBS 
Os tipos de volume disponíveis são:

****- SSD de IOPS provisionadas (io1)****
    - Sustentadas por unidades de estado sólido (SSDs) e a opção de armazenamento de maior desempenho do Amazon EBS.
      
****- SSD de uso geral (gp2)****
        - Esse é o tipo de volume do EBS padrão para instâncias do EC2.
 
****- HDD otimizado para taxa de transferência (st1)****
        - Esse tipo de volume é apoiado por unidades de disco rígido (HDDs) e funciona bem para cargas de trabalho com taxa de transferência intensiva e acessadas com frequência, com grandes conjuntos de dados e grandes tamanhos de E/S.

****- HDD inativo (sc1)****
        - Esse tipo de volume é apoiado por unidades de disco rígido (HDDs) e oferece o menor custo por GB de todos os tipos de volume do EBS. Ele funciona menos para cargas de trabalho acessadas com menos frequência com conjuntos de dados grandes e inativos.


|  | SSD uso Geral | SSD IOPS Provisionadas  | HDD - Otmizada parataxa de transferência | HDD inativo |
|----|----|----|----| ----|
| Tamano maximo de Volume | 16 Tib | 16 Tib | 16 Tib | 16 Tib |
| IOPs/Volume máximo | 10.000 | 32.00 | 500 | 250 |
| Taxa de transferência/ volume máximo | 160 Mib/s | 500 Mib/s | 500 Mib/s | 250 Mib/s |


## Taxa de transferência/ volume máximo
### Volumes do EBS: casos de uso 
![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/fc4367c0-8a8c-43b7-9d95-48291046d674)

## AWS CLI: criar um volume do EBS e anexá-lo a uma instância do EC2
### Criação de um volume do EBS 
- Existe um volume em uma Zona de disponibilidade.
- Exemplo de Interface de linhas de comando da AWS (AWS CLI): –
    - Use o comando create-volume –
    - Use a opção —-availability-zone para especificar a Zona de disponibilidade

```aws ec2 create-volume \ --size 80 \ --availability-zone us-east-1a \ --volume-type gp2```


### Descrevendo um novo volume que acabou de ser criado
Comando da AWS CLI para descrever o volume que foi criado:

```$ aws ec2 describe-volumes \ --volume-ids vol-049df61146c4d7901 vol-1234567890abcdef0```


### Anexando um volume do EBS Resultado esperado:
- Anexar volumes a pontos de montagem lógicos no sistema operacional
- Exemplo da AWS CLI:
    - Use o comando attach-volume. –
    - Use a opção —-device para especificar o ponto de montagem.

```aws ec2 attach-volume --volume-id vol-1234567890abcdef0 --instance-id i-01474ef662b89480 --device /dev/sdf ```

## AWS CLI: criando um snapshot de um volume
### Snapshots incrementais do Amazon EBS
Você pode fazer backup dos dados em um volume do EBS em um snapshot. É crucial tirar snapshots de todos os dados que você possa ter em desenvolvimento, teste ou produção regularmente. O Amazon EBS oferece a capacidade de tirar snapshots de seus volumes para que eles possam ser restaurados caso o hardware subjacente que oferece suporte ao seu volume falhe ou o volume seja excluído acidentalmente.
Os snapshots copiam dados em nível de bloco para a infraestrutura do Amazon S3. Os objetos são armazenados de forma redundante e podem sustentar a perda simultânea de dados em duas instalações. O primeiro snapshot é um snapshot completo do estado do disco no momento em que o snapshot foi criado. Todos os snapshots subsequentes capturarão apenas os deltas (diferenças) em comparação com o snapshot anterior.

![image](https://github.com/luane-loureiro/EscolaDaNuvem-AWS/assets/100947092/205af25d-f7fd-4159-b424-2f0e3a5aaefd)

### Criando um snapshot de um volume do EBS
- Use o comando create-snapshot da AWS CLI. O comando retorna de forma assíncrona.
- Considere interromper a instância ou desmontar o volume primeiro:
    - Para fins de integridade (caso contrário, nenhuma gravação subsequente será capturada.)
    - Ao criar um snapshot para um volume do EBS que serve como dispositivo raiz, interrompa a instância antes de fazer o snapshot.
    - Fundamental para servidores de banco de dados e configurações de Array redundante de discos independentes (RAID)
 
```aws ec2 create-snapshot –-volume-id vol-1234567890abcdef0 --description "This is my root volume snapshot"```

### Copiando um snapshot e uma prova de cópia
#### Comando da AWS CLI: copy-snapshot
```aws ec2 copy-snapshot –-region us-east-1 --source-region us-west-2 –-source-snapshot-id snap-1234567890abcdef0 --description "This is my copied snapshot"```

### Prova de uma cópia 
#### Prova d cópia para uma nova região 
- O novo snapshot tem um ID diferente do origina

```$ aws ec2 describe-snapshots --snapshot-ids snap-0b3c2a7c2a7e4eec6 - -region us-west-2```

## AWS CLI: restaurando um snapshot
### Restaurando umsnapshot Comando da AWS CLI: copiar um snapshot
-  O snapshot é armazenado no Amazon S3, mas não está diretamente acessível. –
    -  Gerenciado pela AWS.
- Encontre o ID do snapshot e restaure o snapshot para um novo volume usando o comando create-volume.
- Os volumes que são restaurados a partir de snapshots têm uma penalidade de primeiro acesso. 
    -  Considere ler todos os blocos para evitar essa penalidade na produção.
 
```aws ec2 create-volume –-size 80 –-availability-zone us-east-1a --volume-type gp2 –-snapshot-id snap-1234567890abcdef0```

### Verificar o status do volume 
#### Comando da AWS CLI: verificar o status do volume
- Esse comando da AWS CLI verifica o status do volume especificado.
- O status do volume fornece o resultado das verificações realizadas nos volumes para determinar eventos que podem prejudicar o desempenho dos volumes.

```aws ec2 describe-volume-status --volume-ids vol-1234567890abcdef0```


## Gerenciando volumes do EBS com uma política de ciclo de vida e a AWS CLI


# CONTINUA -->





















