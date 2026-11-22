# Plano de testes

## Antes dos testes
- Confirmar terminal em Strategy Tester ou conta DEMO.
- Registrar build MT5, corretora, símbolo, moeda da conta, alavancagem, período e modelo de ticks.
- Registrar spread, comissão e swap disponíveis.
- Nunca testar em conta real.

## Testes funcionais
- Trava de conta real.
- Inicialização em tester e DEMO.
- Indicadores e sinais sem candle aberto/look-ahead.
- Uma entrada por evento/candle.
- Cálculo de lote para diferentes moedas e especificações de contrato.
- Volume mínimo/máximo/step e margem insuficiente.
- Stops level, freeze level e tick size.
- Limite diário após perdas e reinicialização.
- Drawdown total persistente.
- Limite de trades, spread e horários.
- Retcodes de ordem e falhas de conexão/mercado fechado.

## Validação estatística
- Período de desenvolvimento e período fora da amostra.
- Sensibilidade dos parâmetros e walk-forward quando possível.
- Não selecionar configuração apenas pelo maior lucro.
- Relatar número de trades, lucro líquido, PF, drawdown equity em valor/% , expectativa, payoff, taxa de acerto, sequência máxima de perdas e custos.

## Modelo de resultado
Preencher apenas com resultados realmente obtidos no MT5. Se não executado, marcar "NÃO TESTADO".
