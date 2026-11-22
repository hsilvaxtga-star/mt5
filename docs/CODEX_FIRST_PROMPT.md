# Prompt inicial para Codex

Leia integralmente `CLAUDE.md`, `docs/STRATEGY_SPEC.md`, `docs/IMPLEMENTATION_PLAN.md` e `skills/forex-trade-setup/SKILL.md`.

Você é o engenheiro responsável por desenvolver do zero o EA `PropFirm_Demo_Test` em MQL5, no repositório `hsilvaxtga-star/mt5`.

Antes de escrever código:
1. Inspecione todos os arquivos e o estado da branch.
2. Resuma requisitos e proteções.
3. Apresente arquitetura de módulos e dependências.
4. Explique a trava de conta real, reconstrução do limite diário, cálculo de lote e limitações do calendário econômico.
5. Liste como cada critério de aceite será testado.
6. Comece pela Etapa 1 após apresentar o plano; não implemente a estratégia inteira de uma vez.

Regras absolutas:
- Somente Strategy Tester e DEMO. Bloqueio inegociável para conta REAL.
- Sem martingale, grid, recuperação de perdas ou aumento de risco.
- Sem dados futuros; sinais somente com candles fechados.
- Não inventar resultados, compilação ou backtests.
- Não declarar filtro de notícias funcional sem validar no tester.
- Mudanças pequenas, explicadas e revisáveis; não apagar arquivos existentes.
- Usar MQL5 nativo e verificar retcodes, margem, tick size, volume step e stops level.
- Criar commits pequenos e descritivos na branch `feature/propfirm-ea`.
- Não inserir segredos, tokens ou credenciais no repositório.

Estratégia-base: EMA 50/200 H4 + rompimento e reteste M15, stop estrutural com buffer ATR, alvo 2R, risco 0,5%, limite diário 2%, filtro de spread e uma posição por símbolo/Magic Number.

Objetivo: EA modular, documentado e preparado para validação rigorosa no Strategy Tester e DEMO. Backtest positivo não garante lucro nem aprovação em prop firm.
