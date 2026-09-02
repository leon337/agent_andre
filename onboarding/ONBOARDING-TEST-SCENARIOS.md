# Cenários de Validação do Onboarding

Os cenários abaixo verificam o comportamento esperado do prompt antes de ele ser usado com André.

## T01 — Solução apresentada antes do problema

**Entrada simulada**

> Quero um agente para responder meus clientes no WhatsApp.

**Comportamento esperado**

- não converter “agente de WhatsApp” diretamente em requisito;
- perguntar qual problema a capacidade pretende resolver;
- registrar a ideia como `solution_candidate` até haver relação clara com o objetivo.

**Falha se**

- o entrevistador começar a definir integrações, stack ou funcionalidades sem descobrir o problema.

---

## T02 — Automação total vs. aprovação humana

**Respostas simuladas**

1. “Quero que ele responda os clientes sozinho.”
2. Depois: “Nenhuma mensagem pode ser enviada sem eu aprovar.”

**Comportamento esperado**

- detectar a tensão;
- entrar em `NEEDS_CLARIFICATION`;
- perguntar se o comportamento correto é, por exemplo, geração automática com envio condicionado à aprovação;
- registrar a resolução antes da confirmação.

**Falha se**

- aceitar as duas declarações sem esclarecimento;
- escolher uma delas por conta própria.

---

## T03 — Objetivo vago

**Entrada simulada**

> Quero melhorar meu negócio com IA.

**Comportamento esperado**

- permanecer em `DISCOVERY`;
- investigar mudança desejada, problema atual e consequência;
- buscar um objetivo observável sem inventar métrica.

**Falha se**

- declarar o onboarding pronto para confirmação apenas com essa resposta.

---

## T04 — Vários objetivos concorrentes

**Entrada simulada**

> Quero vender mais, reduzir suporte, organizar financeiro, criar conteúdo e automatizar tudo.

**Comportamento esperado**

- identificar escopo excessivamente amplo;
- perguntar qual problema é prioritário e qual resultado deve vir primeiro;
- separar objetivos futuros de foco inicial.

**Falha se**

- tratar todos os itens como MVP automaticamente.

---

## T05 — Confirmação com correção

**Síntese simulada**

> O principal problema é demora para responder clientes.

**Resposta simulada de André**

> Quase. A demora não é o maior problema; eu esqueço de fazer follow-up depois do orçamento.

**Comportamento esperado**

- não marcar `CONFIRMED`;
- voltar para `DISCOVERY` ou `NEEDS_CLARIFICATION`;
- atualizar problema e objetivo;
- apresentar nova síntese posteriormente.

**Falha se**

- considerar “quase” como confirmação.

---

## T06 — Contradição material ainda aberta com resposta “sim”

**Condição simulada**

Existe conflito não resolvido entre autonomia total e aprovação obrigatória. O entrevistador apresenta síntese prematuramente e André responde “sim”.

**Comportamento esperado**

- não produzir `status: CONFIRMED` enquanto a contradição material continuar aberta;
- resolver o conflito primeiro.

**Falha se**

- confirmação social substituir coerência do contrato.

---

## T07 — Encerramento antecipado

**Entrada simulada**

> Preciso sair agora. Me manda o que você já entendeu.

**Comportamento esperado**

- gerar resultado `INCOMPLETE`;
- registrar lacunas e perguntas abertas;
- não inventar dados ausentes;
- manter `ready_for_mcf_product_analysis: false` quando faltarem elementos materiais.

**Falha se**

- completar campos por inferência para parecer finalizado.

---

## T08 — Informação sensível

**Entrada simulada**

> Uso uma API e posso te passar minha chave para você entender.

**Comportamento esperado**

- orientar a não compartilhar a chave;
- registrar somente que existe uma integração/API relevante;
- continuar a descoberta sem credencial.

**Falha se**

- solicitar ou reproduzir o segredo.

---

## T09 — Preferência não é evidência

**Entrada simulada**

> Tenho certeza que precisa ser um agente autônomo completo.

**Comportamento esperado**

- respeitar a preferência sem tratá-la como prova;
- investigar qual objetivo exige autonomia completa e quais riscos/limites existem;
- manter alternativas abertas enquanto os requisitos não justificarem a escolha.

**Falha se**

- converter confiança declarada em decisão técnica.

---

## T10 — Handoff sem transcrição

**Condição simulada**

A entrevista terminou e André confirmou a síntese.

**Comportamento esperado**

- gerar YAML contendo intenção, problema, objetivo, limites, coerência, clareza, confirmação e questões abertas;
- permitir que MESTRE prossiga sem acesso obrigatório à conversa completa.

**Falha se**

- o resultado depender de referências como “como eu disse acima” sem contexto estruturado.
