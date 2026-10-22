# Open Finance 💰

**Gerenciador financeiro pessoal, open source e gratuito — local primeiro, com privacidade.**

> ⚠️ **Status: planejamento.** Ainda não há código neste repositório — apenas este README e o [PLANO.md](PLANO.md). Tudo descrito abaixo é **planejado**; nada está implementado ainda.

---

## Por que este projeto?

Apps de finanças pessoais costumam cobrar assinatura, guardar seus dados bancários na nuvem deles ou travar funções básicas atrás de um plano pago. A proposta do Open Finance é o contrário:

- **Grátis e open source** — sem plano premium, sem anúncios.
- **Local primeiro** — seus dados ficam no seu computador, num banco de dados que é seu.
- **Feito para o Brasil** — importação de extratos dos bancos brasileiros, reais (R$), formatos de data e, no futuro, integração com o Open Finance Brasil.

## Funcionalidades

Legenda: 🗓️ **planejado** · 🚧 em desenvolvimento · ✅ disponível

| Funcionalidade | Status | Fase |
|---|---|---|
| Contas (corrente, poupança, carteira) e saldos | 🗓️ planejado | 1 |
| Receitas e despesas com categorias | 🗓️ planejado | 1 |
| Importação de extratos OFX e CSV | 🗓️ planejado | 1 |
| Dashboard: saldo, gastos por categoria, evolução mês a mês | 🗓️ planejado | 1 |
| Cartões de crédito com faturas | 🗓️ planejado | 2 |
| Transações recorrentes | 🗓️ planejado | 2 |
| Orçamentos mensais e metas de economia | 🗓️ planejado | 2 |
| Investimentos e dívidas | 🗓️ planejado | 2 |
| Relatórios exportáveis (CSV/PDF) | 🗓️ planejado | 3 |
| Backup criptografado | 🗓️ planejado | 3 |
| App mobile | 🗓️ planejado | 3 |
| Integração com Open Finance Brasil (via agregador autorizado) | 🗓️ planejado | 3 |

Detalhes, critérios de pronto e ordem de execução estão no **[PLANO.md](PLANO.md)**.

## Princípios

1. **Privacidade por padrão** — nenhum dado sai da máquina sem ação explícita do usuário.
2. **Seus dados, seu formato** — exportação completa a qualquer momento, sem lock-in.
3. **Simples antes de completo** — cada fase entrega algo utilizável antes de crescer.

## Stack

**A definir** (decisão da Fase 0 do plano). Sugestão inicial: **Tauri + React + TypeScript + SQLite** — app desktop leve, multiplataforma e com dados locais.

## Como rodar

Ainda não há o que rodar. As instruções de instalação e desenvolvimento entram aqui assim que a Fase 1 começar.

## Como contribuir

O projeto está no início — é o melhor momento para opinar:

- Abra uma **issue** com sugestões de funcionalidades, bancos cujo extrato você quer importar ou críticas ao [PLANO.md](PLANO.md).
- Exemplos **anonimizados** de arquivos OFX/CSV do seu banco ajudam muito a fase de importação. Nunca envie extratos reais com dados pessoais.

## Licença

**A definir.** Ainda não há arquivo `LICENSE` no repositório (ver Fase 0 do plano).

---

<sub>README e PLANO.md revisados em 21/10/2026 a partir da visão do André. Itens marcados como **planejado** ainda não existem no código.</sub>
