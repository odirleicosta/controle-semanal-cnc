# Controle Semanal — Equipe CNC

Aplicativo web para controle semanal de performance da equipe comercial de máquinas CNC (centros de usinagem e tornos).

Desenvolvido para **OCC Soluções** — Santa Catarina e Paraná.

---

## Funcionalidades

- **Dashboard semanal** — métricas consolidadas da equipe, ranking de visitas e oportunidades, gráfico meta vs. realizado e resumo completo com % de atingimento por vendedor
- **Evolução semanal** — gráficos de linha por vendedor mostrando histórico de visitas, oportunidades e meta vs. realizado ao longo das semanas
- **Comparativo** — tabela automática semana atual vs. semana anterior com indicadores de melhora ou queda por vendedor
- **Registrar semana** — formulário para inserção semanal por vendedor (visitas, oportunidades, meta, realizado e próxima ação planejada)
- **Histórico** — todos os registros com opção de exclusão e exportação em CSV

---

## Equipe

| Vendedor |
|---|
| Odirlei Costa |
| Alexandre Dahmer |
| Willian Rosa |
| Leandro Prada |
| Sérgio Nunes |
| Anderson Canhola |
| Lauro Junior |
| Victor Cestari |
| Felipe Rocha |

---

## Tecnologia

| Camada | Tecnologia |
|---|---|
| Frontend | HTML + CSS + JavaScript puro |
| Banco de dados | Supabase (PostgreSQL) |
| Hospedagem | Vercel |
| Gráficos | Chart.js |
| Ícones | Tabler Icons |
| Fontes | DM Sans + DM Mono (Google Fonts) |

---

## Banco de dados

Tabela `controle_semanal` no Supabase — projeto `suamaquinacnc` (região: São Paulo).

```sql
CREATE TABLE controle_semanal (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  vendedor text NOT NULL,
  semana date NOT NULL,
  visitas integer DEFAULT 0,
  opp integer DEFAULT 0,
  meta numeric(12,2) DEFAULT 0,
  realizado numeric(12,2) DEFAULT 0,
  acao text,
  obs text,
  created_at timestamptz DEFAULT now(),
  updated_at timestamptz DEFAULT now(),
  UNIQUE (vendedor, semana)
);
```

---

## Deploy

O deploy é automático via Vercel. Qualquer push na branch `main` atualiza o app em produção.

**URL de produção:** https://controle-semanal-cnc.vercel.app

---

## Como usar

1. Acesse o link de produção
2. Navegue até **Registrar** no menu lateral
3. Selecione o vendedor, a semana e preencha os dados
4. Clique em **Salvar registro** — os dados são gravados no Supabase em tempo real
5. Qualquer dispositivo com o link acessa os mesmos dados

---

*Projeto interno — OCC Soluções © 2026*
