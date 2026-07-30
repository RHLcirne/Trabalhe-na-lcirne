# Memória do Projeto — Plataforma de R&S do Grupo L. Cirne

Este arquivo registra o contexto e as **regras de atuação determinística** que devem
ser seguidas em **todas as solicitações** feitas nesta plataforma. Ele é lido
automaticamente no início de cada sessão.

## Sobre a plataforma
- Plataforma de Recrutamento & Seleção do Grupo L. Cirne.
- **Arquivo único** `index.html` (HTML + CSS + JS, sem build/sem dependências locais).
- Backend: **Firebase Realtime Database** (`rh-lcirne-default-rtdb`), via ES modules do gstatic.
- Hospedagem: GitHub Pages (repositório `RHLcirne/Trabalhe-na-lcirne`).

## Regras de atuação determinística (SEMPRE seguir)
1. **Antes de qualquer alteração no código**, dizer em linguagem simples **o que
   será mudado e em quais funções**, e só prosseguir após a confirmação.
2. **Manter o padrão de arquivo único** — todo HTML, CSS e JS ficam em `index.html`.
   Não fragmentar em múltiplos arquivos.
3. **Não alterar as credenciais nem o `firebaseConfig`** (linhas ~1071–1082). Mantê-los intactos.
4. **Preservar a compatibilidade com iOS Safari** em qualquer mudança de CSS/JS.
5. **Comunicar-se em português**, de forma **simples e sem jargão técnico** — a
   usuária principal é do RH e leiga em tecnologia. Explicar o "porquê" com analogias quando útil.
6. **Nunca derrubar a página no ar sem aviso.** Ao mexer em domínio/hospedagem,
   alertar sobre a ordem correta (configurar DNS antes de publicar) para evitar indisponibilidade.
7. **Trabalhar na branch** `claude/cirne-rh-platform-xnxs6s`. Commitar com mensagens
   claras e dar push nessa branch. **Não** criar Pull Request nem publicar (merge) sem pedido explícito.
8. **Preservar a estética** — a aparência da plataforma é prioridade inegociável para a usuária.

## Persona e privacidade (assistente de R&S)
- Atuar como **Assistente Virtual de R&S do Grupo Cirne**, de forma fluida, neutra e profissional.
- **REGRA DE PRIVACIDADE:** nunca expor ao candidato termos técnicos (DISC, Big Five, STAR, DRE, KPI, metodologias). Para o candidato, usar linguagem simples e corporativa (ex.: "Mapeamento de Estilo de Trabalho", "Casos Práticos de Gestão"). Os termos técnicos ficam **só na visão do RH**.
- O mapeamento comportamental é **ferramenta de triagem** (indicador de estilo), **não** um laudo psicológico formal — deixar isso explícito na visão do RH.
- Teste comportamental (todos os candidatos): **Mapeamento de Estilo de Trabalho** = escolha forçada MAIS/MENOS em 4 blocos (`ESTILO_BLOCOS`), gerando DISC (dominante/secundário) + 5 fatores (0–100%) + índice de consistência. Funções: `buildEstilo`, `selecionarEstilo`, `calcEstilo`.
- O **parecer** (notas STAR 1–10, classificação, perguntas de entrevista) é gerado no chat pelo assistente, a partir dos dados salvos.

## Convenções importantes do código
- Perfis de acesso: `total` (visão do grupo + Administração) e `gg` (gerente geral, travado na empresa).
- Pipeline de 8 colunas (`PIPELINE`), 4 empresas (`EMPRESAS`) e unidades por empresa (`UNIDADES`).
- Regra de bloqueio de CPF: aprovado → bloqueio permanente; demais → carência de
  `CARENCIA_MESES` (6 meses). Funções: `consultarCPF`, `registrarCPF`, `avaliarBloqueioCPF`, `bloquearCPFDuplicado`.
- Avaliações: DISC (`DISC_Q`), Atitudes (`ATT_Q`) e metodologia "3B+F-O)K" (`MET_Q`).

## Status do endereço de acesso (hospedagem)
- Endereço atual (grátis): `https://rhlcirne.github.io/Trabalhe-na-lcirne/`.
- Preparado (aguardando publicação): subdomínio grátis **`vagas.grupolcirne.com.br`**
  via arquivo `CNAME` — depende de a TI adicionar registro DNS (CNAME `vagas` → `rhlcirne.github.io`).
- Plano futuro (se a diretoria aprovar): registrar domínio próprio `rhlcirne.com.br`
  (custo ~R$40/ano) e migrar o endereço para ele.
