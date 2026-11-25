# SlovoFlow — Flashcards de Russo com Repetição Espaçada (SM-2) e TTS

**SlovoFlow** é uma aplicação web de flashcards inspirada no Anki, desenvolvida para o aprendizado de vocabulário e pronúncia em **russo** por falantes de português (`pt-BR`). O projeto combina **HTML5 semântico moderno**, **síntese de voz nativa (`Web Speech API`)** e o **algoritmo de repetição espaçada SM-2**, funcionando 100% no navegador sem dependências externas ou backend.

---

## Principais Funcionalidades

- **Repetição Espaçada (Algoritmo SM-2):** Cálculo dinâmico de intervalos de revisão com 4 níveis de avaliação (*Errei*, *Difícil*, *Bom* e *Fácil*), fator de facilidade (`easeFactor`), contagem de lapsos e persistência automática no `localStorage`.
- **Síntese de Voz em Russo (`ru-RU`):** Integração com a `Web Speech API` (`window.speechSynthesis`) com detecção assíncrona de vozes (`onvoiceschanged`), seletor de voz, controle de velocidade (`0.5x` a `1.3x`), botão de escuta lenta (`0.65x`) e reprodução automática opcional.
- **Tratamento Fonético de Sílaba Tônica (Ударение):** Alternância visual entre grafia padrão (`спасибо`) e grafia acentuada (`спаси́бо` via caractere Unicode `\u0301`), removendo automaticamente os diacríticos antes do envio ao motor TTS para evitar falhas de pronúncia.
- **Espécime Interativo do Alfabeto Cirílico (33 Letras):** Tabela clicável categorizada entre letras idênticas ao alfabeto latino, falsos amigos visuais (`Р`, `В`, `Н`, `С`, `У`, `Х`) e letras exclusivas do cirílico, com pronúncia instantânea ao clique.
- **CRUD Completo + Teclado Cirílico Virtual:** Modal nativo (`<dialog>`) para criação, edição e exclusão de cards com validação HTML5, botão de pré-escuta no formulário e teclado cirílico integrado para digitação em teclados ABNT2.
- **Portabilidade de Dados e Temas:** Exportação e importação de progresso em `.json`, além de alternância entre tema editorial claro (*Papel*) e escuro (*Grafite*).

---

## Destaques Técnicos de HTML5 Semântico

O código foi estruturado para demonstrar o uso prático e acessível de recursos nativos do HTML5 moderno:

| Elemento / Atributo | Aplicação no Projeto |
| :--- | :--- |
| `<header>`, `<nav>`, `<main>`, `<aside>`, `<article>`, `<footer>` | Estruturação semântica completa da interface sem excesso de `<div>` genéricas. |
| `<dialog>` | Modais nativos acessíveis (Cadastro de Card, Alfabeto Cirílico e Configurações) controlados via `.showModal()` e `.close()`. |
| `<details>` e `<summary>` | Acordeão nativo para notas gramaticais e culturais no verso do card sem necessidade de JavaScript. |
| `<progress>` e `<meter>` | Acompanhamento do progresso da sessão atual (`<progress>`) e nível de domínio de cada baralho (`<meter>`). |
| `<kbd>` | Indicação semântica dos atalhos de teclado (`Espaço`, `1`–`4`, `R`, `S`, `E`). |
| `lang="ru"` e `lang="pt-BR"` | Marcação explícita de idioma em termos cirílicos e frases de exemplo para leitores de tela e motores de pronúncia. |
| `aria-live="polite"`, `aria-pressed`, `aria-label` | Feedbacks dinâmicos de status e controles acessíveis por teclado. |

---

## Atalhos de Teclado

| Tecla | Ação |
| :--- | :--- |
| `Espaço` ou `Enter` | Virar o flashcard (Frente / Verso) |
| `1` · `2` · `3` · `4` | Avaliar card (*Errei*, *Difícil*, *Bom*, *Fácil*) |
| `R` | Ouvir pronúncia na velocidade normal |
| `S` | Ouvir pronúncia devagar (`0.65x`) |
| `E` | Ouvir frase de exemplo (no verso do card) |
