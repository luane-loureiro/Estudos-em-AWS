# Aula 69 - Amazon Simple Storage Service Glacier
## Amazon S3 Glacier
O Amazon S3 Glacier é uma classe de armazenamento segura, durável e de custo extremamente baixo do Amazon S3 para arquivamento de dados e backup de longo prazo.

## Conceitos do Amazon S3 Glacier
### Principais conceitos do Amazon S3 Glacier: arquivamento Conceitos de modelo de dados
****Arquivo:**** qualquer objeto (como foto, vídeo, arquivo ou documento) armazenado no Amazon S3 Glacier.
- Cada arquivo tem um endereço exclusivo. O formulário geral para endereços de arquivo é o seguinte:

```https://<region-specific endpoint>/<account-id>/vaults/<vault-name>/archives/<archive-id>```

Um exemplo de URI é: 

```https://glacier.us-west-2.amazonaws.com/111122223333/vaults/examplevault/archives/Nk....e1_EXAMPLEArchiveId```

### Principais conceitos do Amazon S3 Glacier: cofre Conceitos de modelo de dados
****Cofre :**** um contêiner para armazenar arquivos. Ao criar um cofre, você especifica o nome do cofre e a Região em que deseja que o cofre esteja localizado.
Um exemplo de URI: 

```https://glacier.us-west-2.amazonaws.com/111122223333/vaults/examplevault```

Explicação do exemplo de URI: 
```
- glacier.us-west-2.amazonaws.com identifica a região Oeste dos EUA (Oregon).
- 111122223333 é o ID da conta da AWS que possui o cofre.
- cofres refere-se à coleção de cofres pertencentes à conta da AWS.
- examplevault identifica um cofre específico na coleção de cofres.
```

### Principais conceitos do Amazon S3 Glacier: política de acesso ao cofre Conceitos de modelo de dados
- ****Política de acesso ao cofre:**** determina quem pode ou não acessar os dados armazenados no cofre. Também determina quais operações os usuários podem ou não realizar. Uma política de permissões de acesso ao cofre pode ser criada para cada cofre para gerenciar permissões de acesso para um cofre específico.
- Você também pode usar uma ****política de bloqueio de cofre**** para ajudar a garantir que um cofre não possa ser alterado. Cada cofre pode ter uma política de acesso ao cofre e uma política de bloqueio de cofre anexada a ele.

### Principais conceitos do Amazon S3 Glacier: trabalho Conceitos de modelo de dados
- ****Trabalho:**** os trabalhos do Amazon S3 Glacier podem realizar uma consulta selecionada em um arquivo, recuperar um arquivo ou obter um inventário de um cofre. Ao executar uma consulta em um arquivo, você inicia um trabalho que fornece uma consulta de linguagem de consulta estruturada (SQL) e uma lista de objetos de arquivamento do Amazon S3 Glacier.

### 





