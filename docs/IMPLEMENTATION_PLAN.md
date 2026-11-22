# Plano de implementação

## Etapa 0 — Descoberta
- Confirmar build MT5/MetaEditor, corretora DEMO, símbolos e especificações.
- Definir convenção de horário do servidor.
- Ler skill e especificação.
- Apresentar arquitetura antes de codificar.

## Etapa 1 — Esqueleto seguro
- Criar src/PropFirm_Demo_Test.mq5.
- Implementar trava de conta real em caminho crítico.
- Criar inputs, Magic Number, logs e validação de símbolo.
- Validar bloqueio sem enviar ordens em conta real e inicialização em tester/DEMO.

## Etapa 2 — Indicadores e sinal
- EMA H4, ATR M15 e lógica objetiva de estrutura/rompimento/reteste.
- Somente candles fechados.
- Logs de estados do setup e teste visual no Strategy Tester.

## Etapa 3 — Risco e execução
- Volume pelo risco e distância do SL.
- Validar margem, volume step, stops level, spread e retcodes.
- Uma posição por símbolo/Magic Number.

## Etapa 4 — Proteções
- Limite diário, drawdown total e limite de trades.
- Persistência/reconstrução após reinicialização.
- Horários, sexta-feira, rollover e bloqueio manual de notícias.
- Investigar calendário econômico e documentar limitações no tester.

## Etapa 5 — Validação
- Compilar no MetaEditor.
- Backtest com custos realistas.
- Separar desenvolvimento e fora da amostra.
- Testar sensibilidade sem otimizar apenas lucro máximo.
- Walk-forward quando possível.

## Etapa 6 — Entrega
- Código MQL5, README, presets DEMO, relatórios e limitações.

## Regras
Não pular etapas; não declarar testes não executados; preservar originais; nenhuma conta real.
