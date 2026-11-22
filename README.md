# PropFirm MT5 — EA de avaliação em DEMO

Projeto para desenvolver um Expert Advisor (EA) em MQL5 para MetaTrader 5, com foco em controle de risco e avaliação no Strategy Tester/conta DEMO.

**Segurança:** este projeto não deve enviar ordens em contas reais. Não há promessa de lucro ou aprovação em prop firm.

A especificação, as regras para agentes de código e o plano de implementação serão adicionados na branch `feature/propfirm-ea`.

## Estratégia-base proposta
- Tendência: EMA 50/200 no H4.
- Entrada: rompimento e reteste no M15, confirmados por candles fechados.
- Stop: estrutura + buffer ATR.
- Alvo: 2R, com R:R líquido mínimo de 1,5.
- Risco inicial: 0,5% por operação.
- Limite diário inicial: 2%.
- Sem martingale, grid ou recuperação de perdas.

## Estado
Briefing inicial. Ainda não existe EA implementado, compilado ou testado.
