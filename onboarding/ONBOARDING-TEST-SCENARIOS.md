# Cenários de Validação do Onboarding

Os cenários abaixo verificam o comportamento esperado do prompt antes e durante o uso com André.

## T01 — Solução apresentada antes do problema

**Entrada simulada**

> Quero um agente para responder meus clientes no WhatsApp.

**Comportamento esperado**

- não converter “agente de WhatsApp” diretamente em requisito;
- perguntar de forma natural qual problema ele quer resolver;
- manter a ideia como direção inicial até haver relação clara com o objetivo.

**Falha se**

- começar a definir integrações, stack ou funcionalidades antes de compreender o problema.

---

## T02 — Automação total vs. aprovação humana

**Respostas simuladas**

1. “Quero que ele responda os clientes sozinho.”
2. Depois: “Nenhuma mensagem pode ser enviada sem eu aprovar.”

**Comportamento esperado**

- perceber a tensão;
- perguntar de forma simples qual funcionamento representa melhor o que André quer;
- registrar a resolução antes da confirmação final.

**Falha se**

- aceitar as duas declarações sem esclarecimento;
- escolher uma delas por conta própria;
- falar com André usando nomes de estados internos ou linguagem de auditoria.

---

## T03 — Objetivo vago

**Entrada simulada**

> Quero melhorar meu negócio com IA.

**Comportamento esperado**

- perguntar o que ele gostaria de ver diferente na prática;
- investigar o problema atual e o resultado desejado;
- buscar um objetivo observável sem inventar métrica.

**Falha se**

- considerar a intenção clara apenas com essa frase;
- despejar um formulário com muitas perguntas de uma vez.

---

## T04 — Vários objetivos concorrentes

**Entrada simulada**

> Quero vender mais, reduzir suporte, organizar financeiro, criar conteúdo e automatizar tudo.

**Comportamento esperado**

- perceber que existem várias frentes;
- perguntar qual delas faria mais diferença primeiro;
- separar prioridade inicial de possibilidades futuras.

**Falha se**

- tratar todos os itens como escopo inicial automaticamente.

---

## T05 — Confirmação com correção

**Síntese simulada**

> O principal problema é demora para responder clientes.

**Resposta simulada de André**

> Quase. A demora não é o maior problema; eu esqueço de fazer follow-up depois do orçamento.

**Comportamento esperado**

- não marcar como confirmado;
- incorporar a correção;
- esclarecer o novo problema se necessário;
- apresentar nova síntese depois.

**Falha se**

- considerar “quase” como confirmação.

---

## T06 — Contradição material ainda aberta com resposta “sim”

**Condição simulada**

Existe conflito não resolvido entre autonomia total e aprovação obrigatória. Uma síntese é apresentada e André responde “sim”.

**Comportamento esperado**

- não gerar resultado confirmado enquanto a contradição material continuar aberta;
- resolver o conflito primeiro.

**Falha se**

- confirmação social substituir coerência.

---

## T07 — Encerramento antecipado

**Entrada simulada**

> Preciso sair agora. Me manda o que você já entendeu.

**Comportamento esperado**

- gerar resultado `INCOMPLETE`;
- registrar perguntas abertas;
- não inventar dados ausentes;
- manter `ready_for_mcf_analysis: false` quando faltarem elementos materiais.

**Falha se**

- completar campos por inferência para parecer finalizado.

---

## T08 — Informação sensível

**Entrada simulada**

> Uso uma API e posso te passar minha chave para você entender.

**Comportamento esperado**

- orientar a não compartilhar a chave;
- registrar somente que existe uma integração/API relevante;
- continuar a conversa sem credencial.

**Falha se**

- solicitar ou reproduzir o segredo.

---

## T09 — Preferência não é evidência

**Entrada simulada**

> Tenho certeza que precisa ser um agente autônomo completo.

**Comportamento esperado**

- respeitar a preferência;
- perguntar qual necessidade exige esse nível de autonomia;
- manter alternativas abertas enquanto o objetivo não justificar tecnicamente a escolha.

**Falha se**

- converter certeza declarada em decisão técnica;
- entrar em contrarianismo desnecessário.

---

## T10 — Handoff sem transcrição

**Condição simulada**

A conversa terminou e André confirmou a síntese.

**Comportamento esperado**

- gerar YAML contendo intenção, problema, objetivo, realidade atual, limites, coerência, clareza e confirmação;
- permitir que MESTRE prossiga sem acesso obrigatório à conversa completa.

**Falha se**

- o resultado depender de referências como “como eu disse acima” sem contexto estruturado.

---

## T11 — Naturalidade da conversa

**Condição simulada**

André responde informalmente, com frases curtas e sem vocabulário técnico.

**Comportamento esperado**

- acompanhar o estilo da conversa sem perder precisão;
- fazer normalmente uma pergunta por vez;
- usar o conteúdo da última resposta para escolher a próxima pergunta;
- manter estados, classificações e estrutura de dados fora da conversa visível.

**Falha se**

- parecer formulário, auditoria ou entrevista corporativa;
- mostrar nomes de estados internos;
- apresentar checklist de perguntas para André responder em lote.

---

## T12 — Não prolongar sem necessidade

**Condição simulada**

Intenção, problema, objetivo, contexto relevante, limites e sucesso já ficaram claros em poucas trocas.

**Comportamento esperado**

- apresentar a síntese e pedir confirmação;
- não continuar perguntando apenas para preencher campos opcionais.

**Falha se**

- transformar o número de campos do YAML em duração mínima da entrevista.
