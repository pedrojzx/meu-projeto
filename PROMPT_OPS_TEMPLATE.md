# 📋 Template — Registro de Prompt Ops
### Assistente Educacional com IA | Sprint 1

---

## Como usar este template

Preencha um bloco abaixo para cada prompt criado ou ajustado pelo squad.
Copie o bloco e adicione ao repositório de prompts do projeto.

---

## PROMPT-[XX] — [Nome curto do prompt]

| Campo | Descrição |
|---|---|
| **ID** | PROMPT-XX (ex: PROMPT-01, PROMPT-06...) |
| **Nome** | Nome curto e descritivo (ex: "Gerar resumo de documento") |
| **Responsável** | Nome do membro do squad que criou ou ajustou |
| **Data** | DD/MM/AAAA |
| **Versão** | v1.0 (incrementar a cada ajuste significativo) |
| **Status** | Em teste / Aprovado / Descontinuado |

---

### -- Objetivo

> Descreva em 1-2 frases o que este prompt deve fazer.

---

### -- Contexto de Uso

> Em qual momento da aplicação este prompt é acionado?
> Ex: "Após o usuário fazer upload do arquivo e clicar em 'Gerar Resumo'"

---

### -- Prompt Completo

```
[Cole aqui o prompt exato que será enviado à IA.
Use {variavel} para indicar os campos dinâmicos.]
```

**Variáveis utilizadas:**

| Variável | O que representa |
|---|---|
| `{texto_documento}` | Texto extraído do PDF/TXT enviado pelo usuário |
| `{termo_ou_trecho}` | Termo ou trecho selecionado pelo usuário |
| `{pergunta_usuario}` | Pergunta digitada pelo usuário no chat |
| `{resumo_gerado}` | Resumo gerado pela IA (usado em validações) |

---

### -- Saída Esperada

> Descreva o formato e conteúdo esperado da resposta da IA.
> Ex: "Resumo em português, em parágrafos curtos, com no máximo 300 palavras."

---

### -- Problemas Conhecidos

| Problema | Solução Aplicada |
|---|---|
| [Descreva o problema] | [Descreva como foi resolvido ou mitigado] |

---

### -- Histórico de Versões

| Versão | Data | O que mudou | Responsável |
|---|---|---|---|
| v1.0 | DD/MM/AAAA | Versão inicial | [Nome] |
| v1.1 | DD/MM/AAAA | [Descreva o ajuste] | [Nome] |

---
---

## -- Prompts Registrados na Sprint 1

| ID | Nome | Status | Responsável |
|---|---|---|---|
| PROMPT-01 | Gerar resumo de documento | Aprovado | Squad |
| PROMPT-02 | Gerar perguntas de múltipla escolha | Aprovado | Squad |
| PROMPT-03 | Explicar conceito de forma simplificada | Aprovado | Squad |
| PROMPT-04 | Chat simples com o documento | Em teste | Squad |
| PROMPT-05 | Validação de uso responsável | Aprovado | Squad |

---

## -- Boas Práticas do Squad (Prompt Ops)

- **Sempre teste o prompt** antes de marcar como "Aprovado"
- **Adicione restrições** quando necessário: ex. "Responda apenas com base no documento"
- **Documente alucinações** detectadas nos testes — elas viram problemas conhecidos
- **Versione os ajustes** — nunca apague uma versão anterior, só adicione nova linha no histórico
- **Chunking obrigatório** para documentos com mais de 4000 tokens
