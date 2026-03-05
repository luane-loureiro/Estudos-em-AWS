## Overfitting x Underfitting
### Overfitting (exagero):
O modelo “decora” o treino, performa bem no treino e mal no teste (alta variância).

**Associação:** 
É como decorar respostas de um gabarito antigo. Na prova nova, muda um pouquinho e ele erra.
→ Vai muito bem no treino (o gabarito) e mal no teste (a prova nova).

### Underfitting (falta):
o modelo é simples demais e não aprende o padrão (alto viés).

**Associação:** 
É como não estudar o suficiente. Nem o básico a pessoa sabe.
→ Vai mal no treino e mal no teste.

### Como mitigar (rápido):

**Overfitting →** mais dados, regularização (L1/L2), early stopping, dropout (DL), reduzir complexidade, data augmentation.
estudar a ideia geral, treinar com mais exemplos diferentes, parar antes de “decorar demais”, usar “regras” que evitam exagero (chama regularização).

**Underfitting →** aumentar complexidade, reduzir regularização, treinar mais tempo, features melhores.
estudar mais e usar um método mais esperto (um modelo mais forte).

### Ligação com AWS:
SageMaker Debugger e Model Monitor ajudam a detectar overfitting (drifts de performance) e problemas de generalização.


## Bias × Variance (Viés × Variância)
### Bias (viés)
erro por suposições simplificadas demais (modelo “teimoso”).

**Associação:** 
Todas as flechas caem longe do centro, mas juntas (sempre errando pro mesmo lado).<br>
→ O modelo é simples demais (teimoso).

### Variance (variância)
sensibilidade exagerada ao conjunto de treino (modelo “nervoso”).

**Associação:**
As flechas caem espalhadas, às vezes perto, às vezes longe.<br>
→ O modelo é nervoso, muda muito quando troca os dados.

### O segredo:
Ajustar até as flechas ficarem perto do centro e juntinhas.

**Diminuir bias:** usar um modelo mais poderoso (aprender mais).<br>
**Diminuir variance:** treinar com mais dados, usar regras que evitam exagero.

### Dicas de ajuste rápido:
**Alto Bias / Underfitting:** usar modelo mais flexível (polinômios mais altos, mais árvores, NN maior), treinar mais, menos regularização.<br>
**Alta Variance / Overfitting:** mais dados, regularização, early stopping, ensemble, cross-validation.


## Métricas 
- Regreção - precisão de Numeros - Adivinha numeros - "O Vidente"
- Classificaçao - Detector de Tesouros 
- Mapa do Parque - porucos tesouros e muitos lugares vazios
  
### Ligação com AWS:
- SageMaker Clarify (bias, drift)
- Model Monitor (monitorar métricas em produção)
- Autopilot (escolhe métricas).

### Regrçao "O vidente"
**- MAE - Erro médio por um doce 🍬**<br>
Pensa que você está em um jogo de adivinhaçao de Números, cada erro você perde uma bala por ponto errado.
se você erra por 3, perde 3 balas, se erra por 10 perde 10 balas.
é justo com todos os erros, nao castiga erros grandes, mas quando mais distante mais você perde, mas é proporcional ao tamanho do erro.


**- RMSE - "Bomba 💣"** <br>
Aqui erro grande é uma Bomba, quanto maior o erro maior a Bomba, e quanto maior a bomba maior o estragdo.
Castiga MUITO erros grandes (porque “explode” o erro).

👉 Use RMSE quando erros grandes são perigosos (ex.: errar feio no limite de crédito é pior do que vários errinhos pequenos).

#### Resumo
**MAE** → "É uma mãe" - justa com todos os erros
“quantos doces eu pago em média por previsão?”

**RMSE** → bem sensível a erros grandes
“quanto dói em média quando os erros grandes explodem?”


### Classificação - "Detector de Tesouros"<br>
Imagina um campo quase todo vazio, com poucos tesouros escondidos.<br>
**TP (Tesouro Pego):** você disse “tem tesouro” e realmente tinha.<br>
**FP (Falso Alarme):** você gritou “tesouro!” mas era só uma pedra.<br>
**FN (Tesouro Perdido):** tinha tesouro e você não achou.<br>
**TN (Tudo Normal):** você disse “não tem” e realmente não tinha.<br>


#### 🎯 Precisão (Precision) — “Quando eu grito tesouro, eu acerto?”
Entre os positivos previstos, quantos são corretos.<br>
Entre todos os gritos de “ACHEI!”, quantos eram tesouros de verdade?<br>
Se você tem muito falso alarme, a sua Precisão é baixa.<br>
[!TIP]
Use Precision quando acusar errado é caro

<br>

Recall → entre os positivos reais, quantos capturou.
F1 → harmônico, bom com classes desbalanceadas.
ROC-AUC → separabilidade global.
PR-AUC → melhor com desbalanceamento severo.



