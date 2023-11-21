# Aula 15 - AWS Trusted Advisor

## Introdução ao AWS Trusted Advisor

O AWS Trusted Advisor é um recurso on-line que ajuda a reduzir custos, aumentar o desempenho e melhorar a segurança ao otimizar o seu ambiente da AWS. Ele fornece as práticas recomendadas (ou verificações) em cinco categorias:
1. Otimização de custos: como você pode economizar dinheiro na AWS reduzindo recursos não utilizados e ociosos ou assumindo compromissos de capacidade reservada.
2. Desempenho: aprimore o desempenho do serviço verificando os limites de serviço, garantindo a utilização da taxa de transferência provisionada e monitorando instâncias com uso excessivo.
3. Segurança: aprimore a segurança do aplicativo eliminando lacunas, ativando vários recursos de segurança da AWS e analisando suas permissões.
4. Tolerância a falhas: aumente a disponibilidade e a redundância do aplicativo da AWS aproveitando o auto scaling, as verificações de integridade, as várias zonas de disponibilidade e os recursos de backup.
5. Limites de serviço: verifica o uso do serviço acima de 80% do limite de serviço.

O status da verificação é mostrado usando codificação colorida na página do painel: 
- **Vermelho** (ponto de exclamação vermelho): recomenda-se uma ação.
- **Amarelo** (ponto de exclamação amarelo): recomenda-se uma investigação.
- **Verde** (marca de seleção verde): nenhum problema foi detectado

## Usar o AWS Trusted Advisor 
