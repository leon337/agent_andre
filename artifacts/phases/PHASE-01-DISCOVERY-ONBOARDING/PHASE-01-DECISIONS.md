# PHASE-01 — Decisões

## D-001 — Separar onboarding de construção

**Decisão:** a fase atual não define nem implementa o agente final.

**Motivo:** ainda não existe objetivo do André validado por evidência suficiente.

## D-002 — Tratar solução inicial como candidata

**Decisão:** qualquer “quero um agente para X” será registrado como hipótese/solução candidata até a relação com o problema e objetivo ficar clara.

## D-003 — Confirmação não substitui coerência

**Decisão:** uma resposta afirmativa de André não pode produzir `CONFIRMED` se houver contradição material aberta.

## D-004 — Handoff estruturado em vez de continuidade de sessão

**Decisão:** o estado persistente da descoberta será o YAML final, e não a dependência do mesmo chat.

## D-005 — Prompt autocontido

**Decisão:** `onboarding/ONBOARDING-START.md` é o ponto de entrada canônico.

**Evidência que motivou a decisão:** a primeira versão de `ONBOARDING-PROMPT.md` referenciava um schema externo que não estaria disponível automaticamente no chat do André.

## D-006 — Transcrição opcional

**Decisão:** o YAML deve preservar contexto suficiente para a análise de produto. A transcrição completa só será solicitada se surgir dúvida material não resolvível pelo handoff.

## D-007 — Privacidade mínima

**Decisão:** o onboarding não coleta credenciais. Integrações e dados são registrados por categoria/necessidade, sem segredos.

## D-008 — Validação honesta

**Decisão:** revisão estática pode aprovar estrutura do prompt, mas não será usada para alegar que o comportamento em conversa real já foi validado. Essa evidência depende da entrevista com André.
