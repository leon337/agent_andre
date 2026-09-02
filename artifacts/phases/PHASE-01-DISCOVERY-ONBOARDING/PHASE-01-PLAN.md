# PHASE-01 — Plano

Mission ID: `MCF-20260902-AGENT-ANDRE-ONBOARDING`

## Objetivo

Entregar um onboarding conversacional autocontido que capture intenção, problema e objetivo do André, teste coerência, resolva contradições materiais e exija confirmação explícita antes de gerar o handoff para o MCF.

## Escopo

- entrevista de descoberta;
- separação entre problema e solução candidata;
- contexto atual, prioridades, limites e critérios de sucesso;
- revisão de coerência;
- confirmação explícita do entrevistado;
- handoff YAML independente da transcrição completa.

## Fora de escopo

- arquitetura do agente final;
- implementação;
- integrações definitivas;
- deploy ou publicação.

## Critérios de aceite

1. Intenção, problema, objetivo e resultado esperado são campos distintos.
2. Contradições materiais bloqueiam `CONFIRMED` até resolução.
3. Preferências, fatos, hipóteses e lacunas são diferenciados.
4. Soluções iniciais permanecem candidatas até serem justificadas pelo objetivo.
5. A síntese final é apresentada ao André.
6. Confirmação ambígua não é aceita.
7. O handoff pode ser usado pelo MCF sem exigir a transcrição completa.
8. Encerramento antecipado produz `INCOMPLETE` sem inferências inventadas.
9. O arquivo de entrada é autocontido e pode ser usado em um chat novo.

## Agentes selecionados

- Mestre — coordenação e consolidação.
- Leonardo — problema, objetivo, escopo e critérios.
- Miriam — contexto, proveniência e handoff.
- Beatriz — avaliação de comportamento do prompt.
- Augusto — rastreabilidade obrigatória Classe B.
- Júlia — limites, autonomia e governança do onboarding.
- Léo — gate operacional.

## Sequência inicial

`Mestre → Leonardo → Miriam → Beatriz → Augusto → Júlia → Léo`

## Riscos principais

- onboarding induzir solução antes de entender o problema;
- contradição passar despercebida;
- confirmação social ser tratada como coerência;
- prompt depender de arquivo que o chat do André não possui;
- handoff perder contexto importante;
- coleta desnecessária de segredos.

## Estratégia de validação

- revisão estática dos cenários comportamentais;
- verificação do contrato de saída;
- parse real do YAML de exemplo;
- registro explícito de que o comportamento em entrevista real só pode ser validado após execução com André.

## Dependência externa

A conclusão do produto depende de André executar o onboarding e devolver o YAML confirmado. A fase atual entrega apenas o protocolo de descoberta.
