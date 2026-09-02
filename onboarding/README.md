# Onboarding de Descoberta e Validação de Intenção

Este diretório contém o protocolo usado para entrevistar André antes de definir o agente que será construído.

## Objetivo

Captar e validar:

- intenção real;
- problema que precisa ser resolvido;
- objetivo concreto;
- resultado esperado;
- contexto e fluxo atual;
- restrições, limites e autonomia desejada;
- critérios de sucesso;
- contradições, lacunas e hipóteses.

O onboarding **não escolhe a solução final** e **não define arquitetura**.

## Fluxo de uso

1. André abre um chat novo no ChatGPT.
2. Cola integralmente o conteúdo de `ONBOARDING-PROMPT.md`.
3. Responde às perguntas progressivamente.
4. O entrevistador testa coerência e esclarece contradições materiais.
5. O entrevistador apresenta uma síntese final para validação.
6. André confirma ou corrige a síntese.
7. Somente após confirmação válida, o entrevistador gera `ONBOARDING_RESULT.yaml` conforme `ONBOARDING-SCHEMA.yaml`.
8. André envia o YAML para Leandro.
9. Leandro entrega o resultado ao MESTRE para continuidade da missão no MCF.

## Regra de fechamento

O status só pode ser `CONFIRMED` quando:

- intenção, problema e objetivo estiverem claros o suficiente para análise de produto;
- contradições materiais tiverem sido resolvidas;
- fatos, hipóteses e preferências estiverem diferenciados;
- André tiver recebido a síntese final;
- André tiver confirmado explicitamente que a síntese representa o que ele quer fazer.

Se André desejar encerrar antes disso, gerar um resultado `INCOMPLETE`, registrando lacunas e perguntas abertas. Nunca preencher respostas ausentes por inferência.

## Handoff

A transcrição completa não é requisito para continuidade. O artefato `ONBOARDING_RESULT.yaml` deve preservar o estado necessário para o MCF analisar o problema sem reconstruir contexto inventado.

## Privacidade

Não solicitar senhas, tokens, chaves de API, documentos pessoais completos ou outros segredos durante o onboarding. Quando uma integração ou dado sensível for relevante, registrar apenas a categoria e a necessidade, não a credencial.
