# Limitações conhecidas a validar

- O repositório contém apenas documentação inicial; ainda não existe EA implementado.
- A trava de conta real precisa ser verificada contra o comportamento de ACCOUNT_TRADE_MODE no Strategy Tester e em DEMO, sem abrir exceção para contas reais.
- Calendário econômico MQL5 pode ter limitações de acesso/histórico no Strategy Tester; não afirmar funcionamento antes de validar.
- Conversão de horário servidor/Brasília depende do servidor da corretora e de regras de fuso.
- Métricas detalhadas podem exigir exportação do relatório do Strategy Tester e análise externa.
- Não há compilação ou backtest realizado até este momento.
