# PLANO — Open Finance

Plano de execução por fases. Cada fase tem **entregáveis** (checklist) e **critérios de pronto** — a fase só termina quando todos os critérios forem atendidos.

**Situação atual (21/10/2026):** nenhuma fase iniciada; o repositório contém apenas documentação.

---

## Fase 0 — Fundação (decisões e esqueleto)

Objetivo: decidir o que trava o resto e deixar o repositório pronto para receber código.

- [ ] **Stack** — confirmar ou trocar a sugestão Tauri 2 + React + TypeScript + SQLite. Registrar a decisão em `docs/decisoes/0001-stack.md` (prós, contras, alternativas avaliadas: Electron, PWA, Flutter).
- [ ] **Licença** — escolher (sugestão: MIT, ou AGPL-3.0 se quiser garantir que derivados continuem abertos) e adicionar `LICENSE`.
- [ ] **Esqueleto do app** — projeto criado, abre uma janela vazia em macOS, Windows e Linux.
- [ ] **Qualidade** — lint + formatter + testes unitários (ex.: ESLint, Prettier, Vitest) e CI no GitHub Actions rodando em cada PR.
- [ ] **Arquivos de projeto** — `.gitignore`, `CONTRIBUTING.md`, templates de issue (bug, sugestão, banco para importar).
- [ ] **Valores monetários** — regra documentada: armazenar em **centavos (inteiro)**, nunca `float`.

**Pronto quando:** `git clone` + 1 comando sobe o app em modo dev; CI verde no `main`; `LICENSE` presente; README atualizado com "Como rodar".

---

## Fase 1 — MVP: contas, transações e importação

Objetivo: substituir uma planilha simples de gastos.

**Modelo de dados (SQLite, com migrações versionadas)**
- [ ] `contas` (nome, tipo, saldo inicial, moeda = BRL)
- [ ] `categorias` (nome, tipo receita/despesa, categoria pai opcional) + conjunto padrão em pt-BR
- [ ] `transacoes` (conta, data, descrição, valor em centavos, categoria, id externo para deduplicação)

**Funcionalidades**
- [ ] CRUD de contas, categorias e transações.
- [ ] Importação **OFX** (OFX 1.x SGML e 2.x XML) e **CSV** com mapeamento de colunas, prévia antes de confirmar e detecção de duplicadas (`FITID` no OFX; data + valor + descrição no CSV).
- [ ] Suporte a formatos brasileiros: `dd/mm/aaaa`, vírgula decimal, encoding `latin1`/`utf-8`.
- [ ] Dashboard: saldo por conta e total, gastos por categoria no mês, gráfico de evolução dos últimos 12 meses.
- [ ] Filtros e busca de transações (período, conta, categoria, texto).
- [ ] Exportação completa dos dados em CSV.

**Pronto quando:**
- Extratos OFX de pelo menos 3 bancos (ex.: Nubank, Itaú, Banco do Brasil) importam sem erro, usando arquivos de teste anonimizados em `fixtures/`.
- Importar o mesmo arquivo duas vezes não cria duplicatas.
- Testes automatizados cobrem parsers OFX/CSV e cálculo de saldo.
- Primeira release (`v0.1.0`) publicada com binários no GitHub Releases.

---

## Fase 2 — Planejamento financeiro

Objetivo: sair de "o que gastei" para "o que vou gastar".

- [ ] **Cartões de crédito** — limite, dia de fechamento e vencimento; transações agrupadas por fatura; pagamento da fatura como transferência entre contas.
- [ ] **Parcelamentos** — compra em N parcelas gera lançamentos nas faturas futuras.
- [ ] **Transferências** entre contas (não contam como receita/despesa).
- [ ] **Recorrências** — regras (mensal, semanal, anual) que geram lançamentos previstos.
- [ ] **Orçamentos** — limite mensal por categoria, com barra de progresso e alerta ao passar de 80% / 100%.
- [ ] **Metas** — valor-alvo e data; acompanhamento de progresso.
- [ ] **Investimentos** — posições manuais (tipo, valor aplicado, valor atual) e evolução do patrimônio.
- [ ] **Dívidas** — saldo devedor, parcelas restantes, juros informados.

**Pronto quando:** fatura do cartão calculada bate com a fatura real em um caso de teste com parcelamentos; patrimônio líquido (contas + investimentos − dívidas) aparece no dashboard; release `v0.2.0`.

---

## Fase 3 — Expansão

- [ ] **Relatórios** — receitas × despesas, por categoria e por período, exportáveis em CSV e PDF.
- [ ] **Backup criptografado** — arquivo exportado cifrado com senha do usuário (ex.: SQLCipher ou age); restauração testada.
- [ ] **App mobile** — avaliar Tauri Mobile × React Native; sincronização opcional e criptografada ponta a ponta entre dispositivos.
- [ ] **Open Finance Brasil** — acesso direto exige ser instituição autorizada pelo Banco Central, então a integração será **via agregador autorizado** (ex.: Pluggy, Belvo). Recurso opcional, desligado por padrão, com consentimento explícito e documentação clara de quais dados saem da máquina.

**Pronto quando:** cada item acima tem release própria e documentação de uso no README.

---

## Fora de escopo (por enquanto)

- Servidor/nuvem próprios do projeto.
- Contas multiusuário ou uso empresarial.
- Cotação automática de investimentos (pode entrar depois da Fase 3).

## Como usar este plano

- Cada item `- [ ]` vira uma issue no GitHub com o rótulo da fase (`fase-0`, `fase-1`…).
- Ao concluir um item, marcar `- [x]` aqui e atualizar a tabela de status no README (🗓️ → 🚧 → ✅).
- Mudanças de rumo relevantes viram um registro em `docs/decisoes/`.
