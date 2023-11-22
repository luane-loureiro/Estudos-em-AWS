# Aula 15 - AWS Trusted Advisor

## Introdução ao AWS Trusted Advisor

O AWS Trusted Advisor é um recurso on-line que ajuda a reduzir custos, aumentar o desempenho e melhorar a segurança ao otimizar o seu ambiente da AWS. Ele fornece as práticas recomendadas (ou verificações) em cinco categorias:
1. **Otimização de custos:** como você pode economizar dinheiro na AWS reduzindo recursos não utilizados e ociosos ou assumindo compromissos de capacidade reservada.
2. **Desempenho:** aprimore o desempenho do serviço verificando os limites de serviço, garantindo a utilização da taxa de transferência provisionada e monitorando instâncias com uso excessivo.
3. **Segurança:** aprimore a segurança do aplicativo eliminando lacunas, ativando vários recursos de segurança da AWS e analisando suas permissões.
4. **Tolerância a falhas**: aumente a disponibilidade e a redundância do aplicativo da AWS aproveitando o auto scaling, as verificações de integridade, as várias zonas de disponibilidade e os recursos de backup.
5. **Limites de serviço**: verifica o uso do serviço acima de 80% do limite de serviço.

O status da verificação é mostrado usando codificação colorida na página do painel: 
- **Vermelho** (ponto de exclamação vermelho): recomenda-se uma ação.
- **Amarelo** (ponto de exclamação amarelo): recomenda-se uma investigação.
- **Verde** (marca de seleção verde): nenhum problema foi detectado

## Usar o AWS Trusted Advisor 

O AWS Trusted Advisor fornece recomendações populares de desempenho e segurança para todos os clientes da AWS. As seguintes verificações do Trusted Advisor estão disponíveis para todos os clientes sem nenhum custo:
1. Limites de serviço
2. Security groups: portas específicas sem restrição 
3. Uso do AWS Identity and Access Management (IAM) 
4. Autenticação multifator (MFA) em conta raiz 
5. Snapshots públicos do Amazon Elastic Block Store (Amazon EBS) 
6. Snapshots públicos do Amazon Relational Database Service (Amazon RDS)

O conjunto completo de verificações e orientação está disponível nos planos de suporte Business e Enterprise. O AWS Trusted Advisor ajuda você a provisionar seus recursos seguindo as práticas recomendadas. Usando esse recurso, você pode melhorar o desempenho e a confiabilidade do sistema, aumentar a segurança e procurar oportunidades de economizar dinheiro.


## Recursos Do Trusted Advisor
possa personalizar recomendações e monitorar seus recursos da AWS de forma proativa:
- **Notificações do Trusted Advisor:** mantenha-se atualizado com a implantação de recursos da AWS. Você será notificado por uma mensagem de e-mail semanal ao optar por este serviço.
- **AWS Identity and Access Management (IAM):** controle o acesso a verificações ou categorias de verificações específicas.
- **Interface de programação de aplicativo (API) do AWS Support:** recupere e atualize os resultados do Trusted Advisor programaticamente.
- **Links de ação:** hiperlinks em itens em um relatório do Trusted Advisor que o levam diretamente à console. No console, você pode implementar as recomendações do Trusted Advisor.
- **Alterações recentes:** monitore as alterações recentes do status da verificação no painel do console. As alterações mais recentes aparecem na parte superior da lista para chamar sua atenção.
- **Excluir itens:** personalize o relatório do Trusted Advisor. Você pode excluir itens do resultado da verificação se eles não forem relevantes.
- **Atualizar tudo:** atualize verificações individuais ou todas as verificações de uma só vez selecionando Atualizar tudo no canto superior direito do painel de resumo. Uma verificação pode ser atualizada 5 minutos após a ùltima atualização.

