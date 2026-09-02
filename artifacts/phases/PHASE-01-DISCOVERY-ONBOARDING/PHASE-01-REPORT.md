# PHASE-01 — Relatório de Execução

Mission ID: `MCF-20260902-AGENT-ANDRE-ONBOARDING`

## Resultado

A fase entregou um protocolo autocontido de onboarding em `onboarding/ONBOARDING-START.md` para André executar em um chat próprio. O protocolo busca captar intenção, problema, objetivo, resultado esperado, contexto, autonomia, limites e critérios de sucesso; testar coerência; e exigir confirmação explícita antes do handoff.

Após a primeira entrega, surgiu feedback direto de usabilidade antes da entrevista completa: a lógica foi considerada adequada, porém o prompt estava excessivamente burocrático e poderia fazer a conversa parecer uma entrevista corporativa. O achado foi aceito como defeito de experiência e gerou uma segunda iteração.

## Execução cronológica registrada

### Mestre — abertura e delimitação

- abriu contrato da missão;
- classificou a missão como Classe B;
- limitou a fase a descoberta/validação de intenção;
- isolou o trabalho em `feat/onboarding-intent-discovery` após bootstrap mínimo do repositório vazio.

### Leonardo — produto e requisitos

- separou intenção, problema, objetivo, resultado e solução candidata;
- definiu critérios para evitar solution-first e escopo prematuro;
- preservou prioridade, contexto e critérios de sucesso como informação necessária ao handoff.

### Miriam — contexto e handoff

- definiu YAML como estado persistente da descoberta;
- tornou a transcrição completa opcional;
- preservou contradições, hipóteses e questões abertas sem depender da memória do chat.

### Beatriz — avaliação do prompt, ciclo 1

- aplicou cenários de solução-first, contradição, objetivo vago, múltiplas prioridades, confirmação ambígua, encerramento antecipado e credenciais;
- identificou falha material: a primeira versão dependia de um schema externo não disponível automaticamente no chat do André.

### Recuperação CAF, ciclo 1

- falha capturada: dependência externa não transportada;
- recuperação: criação de `ONBOARDING-START.md` autocontido com formato de saída incorporado;
- resultado: dependência eliminada.

### Evidência real de usabilidade — ciclo 2

Antes da entrevista completa, André avaliou o material e apontou que a lógica estava boa, mas o prompt estava mais burocrático do que necessário e poderia prejudicar a naturalidade da conversa.

**Classificação do achado:** defeito confirmado de UX conversacional, não falha da lógica de descoberta.

### Beatriz + Leonardo — correção do ciclo 2

`ONBOARDING-START.md` foi refatorado para:

- começar com uma conversa simples e uma pergunta natural;
- fazer normalmente uma pergunta por vez;
- escolher a próxima pergunta com base na resposta anterior;
- impedir exposição de estados internos, checklists e terminologia do MCF ao entrevistado;
- não prolongar a entrevista apenas para preencher campos;
- manter detecção de contradições em linguagem cotidiana;
- preservar síntese e confirmação explícita;
- reduzir o YAML final ao estado realmente necessário para a próxima fase.

Os cenários `T11 — Naturalidade da conversa` e `T12 — Não prolongar sem necessidade` foram adicionados ao contrato de avaliação.

### Augusto — rastreabilidade

- separou feedback de leitura/UX de evidência de entrevista completa;
- registrou a correção sem declarar comportamento ao vivo como validado;
- manteve o pacote Classe B e o checkpoint recuperável.

### Júlia — governança e limites

A simplificação da experiência não removeu os limites materiais:

- não solicitar segredos;
- não decidir contradições por André;
- não converter preferência em requisito técnico automaticamente;
- não emitir `CONFIRMED` com contradição material aberta;
- exigir confirmação explícita da síntese.

### Léo — gate operacional

**Decisão:** `APROVAR_COM_RESSALVAS`.

**Aprovado:** nova versão conversacional do `ONBOARDING-START.md` para entrevista real.

**Ressalva:** ainda falta evidência da execução integral da entrevista e do YAML gerado a partir das respostas reais de André.

## Evidências

- `.mcf/mission.yaml`;
- `onboarding/ONBOARDING-START.md`;
- `onboarding/ONBOARDING-TEST-SCENARIOS.md`;
- feedback de usabilidade recebido antes da entrevista completa;
- `PHASE-01-VALIDATION.txt`;
- `PHASE-01-VALIDATION-FULL.txt`;
- `PHASE-01-SMOKE.txt`.

## Estado

- objetivo estrutural da Fase 01: atendido;
- dependência externa de schema: corrigida;
- problema de burocracia/naturalidade: corrigido na versão atual;
- entrevista completa com André: pendente;
- arquitetura do agente final: não iniciada;
- estado geral: `AGUARDANDO_DEPENDENCIA_EXTERNA`.

## Próxima ação

André deve abrir novamente a versão atual de `onboarding/ONBOARDING-START.md`, colá-la em um chat novo e conversar normalmente. Ao final, deve devolver o bloco `onboarding_result` em YAML. Esse resultado será a evidência para a próxima fase do MCF.
