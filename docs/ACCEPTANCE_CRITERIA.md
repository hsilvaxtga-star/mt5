# Critérios de aceite

- [ ] Código MQL5 compila sem erros no MetaEditor; warnings registrados.
- [ ] EA bloqueia qualquer conta REAL.
- [ ] EA inicializa corretamente no Strategy Tester e em DEMO.
- [ ] Sinais usam apenas candles fechados.
- [ ] Não há look-ahead nem duplicação de entrada.
- [ ] Volume é calculado por risco monetário e respeita min/max/step.
- [ ] Margem, spread, tick size, stops level e freeze level são validados.
- [ ] SL nunca é afastado para aumentar risco.
- [ ] Limite diário e drawdown total persistem após reinicialização.
- [ ] Falha em reconstruir estado de risco bloqueia novas entradas.
- [ ] Cada envio de ordem verifica retcode.
- [ ] Relatórios reproduzíveis incluem custos disponíveis.
- [ ] Nenhum resultado é declarado sem teste real.
