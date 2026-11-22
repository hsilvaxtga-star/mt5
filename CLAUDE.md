# Regras permanentes — PropFirm MT5

## Papel
Atue como engenheiro MQL5 responsável por projetar, implementar, revisar e testar um Expert Advisor (EA) para MetaTrader 5. Trabalhe em etapas pequenas, explique alterações e não esconda limitações.

## Segurança inegociável: somente DEMO / Strategy Tester
- Projeto exclusivamente para Strategy Tester e contas DEMO.
- Nunca orientar, habilitar ou executar operações em conta REAL.
- O EA deve recusar inicialização e bloquear qualquer envio de ordem se `ACCOUNT_TRADE_MODE` indicar conta real. O Strategy Tester pode ter particularidades de identificação; valide a condição oficial de tester separadamente, sem criar um caminho que permita execução em conta real.
- Não criar input para desativar a trava de conta real.
- Não enviar ordens reais, não integrar APIs externas de execução e não contornar proteções.
- Não usar martingale, grid, recuperação de perdas ou aumento de lote após prejuízo.

## Antes de codificar
1. Leia integralmente `docs/STRATEGY_SPEC.md`, `docs/IMPLEMENTATION_PLAN.md` e `skills/forex-trade-setup/SKILL.md`.
2. Inspecione todos os arquivos existentes e preserve os originais.
3. Apresente arquitetura, ambiguidades e riscos técnicos antes de implementar.
4. Consulte propriedades reais do símbolo via `SymbolInfo*`; não presuma pip, tick value, contrato ou volume.

## Estratégia inicial
- Contexto: EMA 50/200 H4.
- Execução: rompimento + reteste M15, com candle de confirmação fechado.
- Compras quando EMA50 > EMA200; vendas quando EMA50 < EMA200.
- Stop além da estrutura do reteste com buffer ATR; nunca afastar stop após entrada.
- Alvo padrão 2R; rejeitar R:R líquido estimado inferior a 1,5.
- Risco padrão 0,5% do equity por operação.
- Uma posição por símbolo/Magic Number.
- Filtros configuráveis: spread, sessão, rollover, sexta-feira e notícias quando houver dados confiáveis.
- Limite diário padrão 2%; limite de operações e drawdown total configuráveis.

## Engenharia MQL5
- MQL5 nativo, sem dependências externas não aprovadas.
- Usar `CTrade` e validar `ResultRetcode()` em toda tentativa de ordem.
- Sinais apenas com candles fechados; sem look-ahead/repaint.
- Tratar OnInit, OnDeinit, OnTick e OnTradeTransaction.
- Normalizar preços por tick size/digits e volumes por volume step/min/max.
- Calcular risco com propriedades reais do símbolo e `OrderCalcProfit`; validar margem com `OrderCalcMargin`.
- Respeitar stops/freeze level e modo de preenchimento.
- Filtrar posições por símbolo e Magic Number.
- Impedir duplicação de entrada no mesmo candle/evento.
- Logs devem explicar bloqueios e decisões.
- Não usar DLL/WebRequest/serviços externos sem autorização explícita.

## Proteções
- Perda diária calculada sobre equity de referência no início do dia do servidor.
- Persistir/reconstruir estado após reinicialização; não zerar perda diária ao reiniciar.
- Implementar drawdown total configurável com referência persistente e bloqueio até intervenção manual.
- Se o estado não puder ser reconstruído com segurança, bloquear novas entradas.
- Nunca aumentar risco para recuperar perdas.

## Notícias e horários
- A skill exige eventos de alto impacto para as duas moedas e sessão convertida para America/Sao_Paulo.
- Pesquisar documentação oficial MQL5 antes de implementar calendário econômico.
- Não afirmar que calendário funciona no Strategy Tester sem teste real.
- Se indisponível, fornecer bloqueio manual de janelas e documentar a limitação.
- Distinguir horário do servidor e horário de Brasília.

## Testes
- Compilar no MetaEditor sem erros; registrar warnings.
- Backtest com dados/ticks disponíveis e parâmetros explícitos.
- Separar desenvolvimento e fora da amostra; fazer sensibilidade/walk-forward quando possível.
- Relatar lucro líquido/bruto, Profit Factor, drawdown de equity em valor e %, trades, taxa de acerto, payoff, expectativa, sequência máxima de perdas e custos.
- Não inventar resultados. Se MetaEditor/MT5 não estiver disponível, entregar roteiro local e declarar que não houve compilação/teste.
- Nunca afirmar aprovação em prop firm com base apenas em backtest.

## Processo
1. Inspecionar e resumir requisitos.
2. Propor arquitetura e riscos.
3. Implementar uma etapa pequena.
4. Revisar/compilar/testar quando possível.
5. Relatar arquivos alterados, testes reais e pendências.
6. Não fazer alterações destrutivas sem autorização.

## Entrega
EA .mq5/.mqh, README, presets DEMO, relatórios reproduzíveis e limitações conhecidas.
