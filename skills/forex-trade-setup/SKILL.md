---
name: forex-trade-setup
description: "Checklist rígido para analisar e validar um setup de trade em Forex antes de qualquer operação. Use quando o usuário pedir para avaliar, montar ou revisar um setup em pares de moedas (ex.: EURUSD, GBPJPY, XAUUSD), calcular tamanho de lote, stop, alvo, risco/retorno ou checar sessão de liquidez e eventos de notícia. Não use para análise de ações, cripto ou investimento de longo prazo."
---

# Forex Trade Setup

Esta skill é um gate de validação: nenhuma operação é considerada válida até passar por todas as etapas abaixo. Se faltar informação, pergunte. Nunca invente preços, spreads ou datas de notícias.

> Isto é apoio à análise, não recomendação de investimento. Forex com alavancagem pode causar perdas superiores ao capital depositado.

## Entradas necessárias
- Par de moedas e direção (compra/venda)
- Timeframe de execução e timeframe de contexto (ex.: M15 dentro de H4)
- Preço de entrada, stop loss e take profit (ou peça para calcular)
- Saldo da conta, moeda da conta e % de risco por operação
- Spread atual e corretora/tipo de conta (opcional)

## Checklist de validação
### 1. Contexto de mercado
- Tendência no timeframe superior e alinhamento com a operação.
- Níveis relevantes: suportes/resistências, máximas/mínimas anteriores, números redondos.
- Operação contra tendência superior exige justificativa e risco elevado.

### 2. Sessão e liquidez
- Identificar Sydney, Tóquio, Londres, Nova York e sobreposições.
- Verificar adequação do par à sessão.
- Alertar para rollover, abertura de domingo e sexta no fim do dia.
- Converter para America/Sao_Paulo e declarar o fuso usado.

### 3. Notícias e eventos
- Verificar eventos de alto impacto para as duas moedas (payroll, juros, CPI, bancos centrais).
- Confirmar data/hora em calendário atualizado; não afirmar datas de memória.

### 4. Estrutura do trade
- Entrada com gatilho claro.
- Stop em ponto de invalidação, com folga para spread/volatilidade.
- Alvo realista antes de obstáculos relevantes.
- R:R = distância alvo / distância stop; mínimo recomendado 1:1,5.

### 5. Gestão de risco e lote
- Calcular lote a partir do risco, nunca o contrário.
- Considerar moeda da conta, tick/pip value, conversão, margem e alavancagem.
- Somar risco de operações correlacionadas quando possível.
- Incluir spread e comissão no R:R.

### 6. Disciplina
- Verificar aderência ao plano e evitar revanche.
- Respeitar limite diário e número de operações.
- Nunca afastar o stop depois da entrada.

## Formato da resposta
1. Veredito: Aprovado, Aprovado com ressalvas ou Reprovado.
2. Resumo: par, direção, entrada, stop, alvo, R:R, lote e risco monetário.
3. Checklist: estado e motivo das etapas 1 a 6.
4. Até três riscos principais.
5. O que falta confirmar.

## Regras
Seja direto. Nunca prometa lucro, assertividade ou certeza. Mostre contas. Não execute ordens reais; apenas analise e valide.
