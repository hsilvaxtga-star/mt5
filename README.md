# PropFirm MT5 — projeto de EA para DEMO

Projeto para desenvolver um Expert Advisor em MQL5 para MetaTrader 5, com foco em controle de risco e avaliação no Strategy Tester/conta DEMO.

**Segurança:** o EA deve bloquear execução em contas reais. Não há promessa de lucro nem de aprovação em prop firm.

## Documentos principais
- `CLAUDE.md`: regras permanentes para agentes de código.
- `docs/STRATEGY_SPEC.md`: estratégia e requisitos funcionais.
- `docs/IMPLEMENTATION_PLAN.md`: etapas de desenvolvimento.
- `docs/CODEX_FIRST_PROMPT.md`: prompt pronto para iniciar o trabalho no Codex.
- `docs/TEST_PLAN.md`: plano de validação.
- `docs/ACCEPTANCE_CRITERIA.md`: critérios de aceite.
- `docs/KNOWN_LIMITATIONS.md`: limitações a validar.
- `skills/forex-trade-setup/SKILL.md`: skill de Forex incluída no projeto.

## Estratégia-base
- Tendência: EMA 50/200 no H4.
- Entrada: rompimento e reteste no M15, com candles fechados.
- Stop: estrutura + buffer ATR.
- Alvo: 2R; R:R líquido mínimo 1,5.
- Risco inicial: 0,5% por operação.
- Limite diário inicial: 2%.
- Sem martingale, grid ou recuperação de perdas.

## Estado atual — versão 0.1.0
A estrutura documental e as pastas iniciais foram criadas na branch `feature/propfirm-ea`. **O EA ainda não foi implementado, compilado ou testado.** A implementação deve começar após o Codex revisar o plano e seguir as etapas documentadas.

## Como começar
1. Abra o repositório no Codex.
2. Selecione a branch `feature/propfirm-ea`.
3. Abra e cole o prompt de `docs/CODEX_FIRST_PROMPT.md`.
4. Revise a arquitetura proposta antes de autorizar a implementação.
5. Compile e teste somente no MetaEditor/Strategy Tester ou em conta DEMO.

Resultados de backtest precisam ser reproduzíveis e nunca inventados.
