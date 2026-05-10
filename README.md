# -- Assistente Educacional com IA — Upload de PDF/TXT

Aplicação web que utiliza inteligência artificial para auxiliar estudantes e professores na compreensão de conteúdos acadêmicos a partir de arquivos PDF ou TXT.

---

## -- Descrição do Projeto

O usuário faz upload de um PDF ou TXT e recebe automaticamente, via IA:
- Resumo objetivo do conteúdo
- Perguntas de revisão (múltipla escolha)
- Explicações simplificadas de conceitos
- Chat interativo com o documento

---

## -- Estrutura de Pastas

```
meu-projeto/
├── index.html        # Página principal da aplicação
├── css/
│   └── style.css     # Estilização da interface
└── js/
    └── script.js     # Lógica de interação e integração com IA
```

---

## -- Decisões Técnicas — Sprint 1

### 1. Biblioteca de leitura de PDF: pdf.js

Foi escolhida a biblioteca **pdf.js** (Mozilla) para extração de texto dos arquivos PDF enviados pelos usuários.

**Motivos da escolha:**
- Roda 100% no navegador, sem necessidade de backend para leitura do arquivo
- Código aberto, mantido ativamente pela Mozilla
- Suporte a múltiplos formatos de PDF
- Amplamente documentada e com grande comunidade

**Limitação identificada:** PDFs gerados a partir de imagens escaneadas não possuem camada de texto legível. Para o MVP, este tipo de arquivo exibirá mensagem de erro amigável. Suporte a OCR será avaliado em versões futuras.

---

### 2. Estratégia de Chunking

Documentos longos ultrapassam o limite de tokens das APIs de IA gratuitas. Para contornar isso, o texto extraído é dividido em **partes menores (chunks)** antes de ser enviado à API.

**Estratégia adotada:**
- Divisão por limite de tokens (~4000 tokens por chunk)
- Cada chunk é processado separadamente e os resultados são combinados
- Prioridade para os primeiros chunks no MVP (onde costuma estar o conteúdo mais relevante)

**Motivo:** Evitar timeout da API e garantir que documentos extensos sejam processados sem erros.

---

### 3. Estrutura de Pastas do Projeto

A estrutura foi definida para ser simples e compatível com o **Azure Static Web Apps** (plano gratuito):

| Pasta/Arquivo | Função |
|---|---|
| `index.html` | Ponto de entrada da aplicação |
| `css/style.css` | Estilos visuais da interface |
| `js/script.js` | Lógica de upload, extração de texto e chamadas à API |

Critério de decisão: manter o projeto como HTML/CSS/JS puro no MVP, sem frameworks adicionais, para facilitar o deploy e reduzir a complexidade inicial.

---

### 4. Configuração do Repositório GitHub

- **Repositório:** [github.com/pedrojzx/meu-projeto](https://github.com/pedrojzx/meu-projeto)
- **Branch principal:** `main`
- **Visibilidade:** Público (requisito do Azure Static Web Apps gratuito)
- **CI/CD:** Configurado via GitHub Actions — cada push na branch `main` aciona um novo deploy automático

---

## -- Deploy — Azure Static Web Apps

- **URL pública:** `https://yellow-field-06fdaa010.7.azurestaticapps.net`
- **Plano:** Free
- **Pipeline:** push na `main` → GitHub Actions → build → deploy automático

---

## -- Personas do Projeto

| Persona | Perfil | Necessidade |
|---|---|---|
| Lucas Ferreira | Estudante de ADS, 19 anos, pouco tempo livre | Resumir PDFs rapidamente antes das provas |
| Ana Beatriz Souza | Aluna do ENEM, 16 anos | Resumo claro e perguntas objetivas de múltipla escolha |
| Marcos Andrade | Professor de informática, 38 anos | Gerar resumos e questionários prontos a partir de PDFs |

---

## -- Cenários de Falha Conhecidos

| Cenário | Comportamento esperado |
|---|---|
| PDF escaneado (sem texto) | Mensagem de erro amigável orientando o usuário |
| Arquivo corrompido ou protegido | Mensagem de erro clara com instruções |
| Documento muito longo | Chunking automático para evitar timeout |
| Resposta fora do escopo | Prompts com restrições para evitar alucinações |

---

## -- MVP — Funcionalidades Priorizadas

- [x] Upload de arquivo PDF/TXT
- [x] Extração de texto via pdf.js
- [x] Geração de resumo automático via IA
- [x] Geração de perguntas de múltipla escolha
- [x] Explicação simplificada de conceitos
- [ ] Chat interativo com o documento *(simulado no MVP)*
- [ ] Flashcards e simulados *(simulados no MVP)*
- [ ] Funcionalidades do professor *(versão futura)*

---

## -- Como Atualizar o Projeto

```bash
# 1. Faça as alterações nos arquivos localmente
# 2. Abra o terminal na pasta do projeto
cd C:\Users\pedro\Desktop\meu-projeto

# 3. Envie as alterações
git add .
git commit -m "descreva o que mudou"
git push
```

O site atualiza automaticamente em ~2 minutos após o push. ✅
