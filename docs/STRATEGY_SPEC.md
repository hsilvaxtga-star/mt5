# Especificação funcional — PropFirm_Demo_Test

## Objetivo e escopo
EA para estudo no MetaTrader 5 Strategy Tester e em conta DEMO. Não promete lucro nem aprovação em prop firm. Primeira versão voltada a pares Forex principais e secundários. Não presumir que XAUUSD, índices, cripto-CFDs ou CFDs usem as mesmas especificações; só incluir após validação individual.

## Sinal
### Contexto H4
- EMA rápida 50 e lenta 200.
- Viés comprador quando EMA50 > EMA200; vendedor quando EMA50 < EMA200.
- Sem dados suficientes ou sem direção: não operar.

### Gatilho M15
1. Identificar consolidação/estrutura recente usando candles fechados.
2. Confirmar rompimento por fechamento além do nível.
3. Aguardar reteste dentro de janela configurável.
4. Exigir candle de confirmação fechado na direção do viés.
5. Uma entrada por evento; nunca repetir no mesmo candle.
6. Definir objetivamente consolidação, lookback, tolerância e confirmação por parâmetros documentados. Não usar pivôs futuros.

## Stop e alvo
- Stop além da estrutura do reteste com buffer baseado em ATR M15 (período padrão 14).
- Alvo inicial 2R.
- R:R líquido mínimo 1,5, descontando custos estimáveis.
- Rejeitar stop inválido, muito próximo/distante ou incompatível com regras do símbolo.
- Nunca mover SL para longe da entrada. Break-even e trailing desativados na primeira versão.

## Risco e volume
- Risco padrão 0,5% do equity.
- Inputs para risco percentual, risco monetário máximo e lote máximo de segurança.
- Calcular volume pela perda monetária estimada até o SL, usando OrderCalcProfit quando aplicável.
- Arredondar para baixo ao volume step; se menor que volume mínimo, não operar.
- Validar margem com OrderCalcMargin.
- Uma posição por símbolo + Magic Number.
- Não somar posições de outros EAs como posições próprias; alertar sobre exposição agregada quando possível.
- Proibidos martingale, grid e aumento de lote após perda.

## Proteções
- Bloqueio absoluto de conta real.
- Perda diária máxima padrão 2% do equity de referência no início do dia do servidor.
- Drawdown total máximo configurável; ao atingir, bloquear novas entradas até intervenção manual.
- Limite diário de trades configurável.
- Spread máximo configurável e validado por símbolo.
- Horários configuráveis, bloqueio de rollover e baixa liquidez.
- Última hora de novas entradas na sexta configurável.
- Slippage/deviation configurável.
- Tratar gaps, desconexão, mercado fechado, falta de margem e retcodes.
- Reconstruir estado diário por histórico de deals; se não for possível, falhar de forma segura.

## Notícias
- Investigar calendário econômico oficial MQL5 e disponibilidade no Strategy Tester.
- Não alegar filtro automático funcional sem validação.
- Se indisponível, implementar bloqueio manual por janela de horário e documentar.

## Inputs
MagicNumber, TradeSymbol, RiskPercent (0,5), DailyLossLimitPercent (2), MaxTotalDrawdownPercent, MaxTradesPerDay, MaxSpreadPoints, FastEMA (50), SlowEMA (200), ContextTimeframe (H4), EntryTimeframe (M15), ATRPeriod (14), ATRBufferMultiplier, StructureLookback, RetestToleranceATR, RetestMaxBars, TargetRR (2), MinNetRR (1,5), TradingStartHour, TradingEndHour, FridayLastEntryHour, ManualNewsBlockWindows e MaxDeviationPoints. A trava DEMO não pode ser desativada.

## Métricas
Lucro líquido/bruto, Profit Factor, drawdown máximo de equity em valor/% , total de operações, taxa de acerto, ganho/perda médios, expectativa, maior sequência de perdas, custos e resultados por mês/símbolo/sessão quando viável.

## Critérios de aceite
- Compilação sem erros no MetaEditor.
- Nenhuma ordem em conta real.
- Sem duplicação de entrada.
- Volume respeita min/max/step e risco.
- Limites diário/total bloqueiam corretamente.
- SL/TP respeitam tick size, stops level e regras do símbolo.
- Sinais usam candles fechados.
- Logs explicam bloqueios e decisões.
- Relatórios reproduzíveis e sem números inventados.
