# Changelog

Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/).
Versionamento segue [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [1.3.0] - 2026-09-30

### Adicionado
- **`lgpd-security-baseline`**: matriz de aderência às referências que a ANPD reconhece para o
  Art. 46 — guia de segurança da ANPD (2021), ISO/IEC 27001:2022 (Anexo A, 93 controles),
  ISO/IEC 27701:2019 (cláusulas 7 e 8) e CIS Controls v8 (IG1, 56 salvaguardas, mais o IG2 que
  toca um SaaS). Cada controle com situação, evidência, dono (código, operação, processo) e
  lacuna; nada marcado "cumpre" sem evidência. Listas em `references/`, template em `assets/`.
- **`lgpd-security-policy`**: política de segurança da informação e programa de conscientização
  e treinamento (as medidas administrativas do guia da ANPD; ISO 27001 5.1, 6.3; CIS 14), com
  templates e registro de leitura e participação.
- **`lgpd-operator`**: o produto como operador (Art. 39) — DPA voltado aos clientes (o produto é
  o operador, o cliente é o controlador), lista pública de suboperadores com aviso de mudança,
  entradas do ROPA como operador e matriz de deveres do controlador que o produto precisa apoiar
  (ISO 27701, cláusula 8). Complementa `lgpd-dpa`, que olha para os fornecedores contratados.
- `lgpd-audit`: passos F15 a F17 no Pipeline A e L13 e L14 no Pipeline B; roteamento e dependências
  das três skills; seção "Padrões de segurança que a ANPD reconhece" em `normative-reference.md`.
- README: as três skills na árvore, na tabela de gatilhos e em `.lgpd/security/` e `.lgpd/operator/`.

## [1.2.0] - 2026-05-30

### Adicionado
- **Distribuição multi-agente**: manifests nativos para Codex (`.codex-plugin/plugin.json`),
  Cursor (`.cursor-plugin/plugin.json`), Gemini CLI (`gemini-extension.json`) e OpenCode
  (`.opencode/plugins/lgpd-skills.js` + `package.json`).
- `skills/lgpd-audit/references/skill-activation.md` — como ativar sub-skills em cada agente.
- README: seção de instalação com o comando de cada um dos 5 agentes.

### Alterado
- **Reestruturação para o layout canônico agentskills.io**: skills movidas de
  `plugins/lgpd-skills/skills/` para `skills/` na raiz; o repo-raiz passa a ser o plugin.
  `marketplace.json` agora usa `source: "./"`. Instalação via Claude Code permanece igual.

## [1.1.1] - 2026-05-29

### Corrigido
- Adicionados 3 assets referenciados mas ausentes (referências órfãs que quebravam a skill ao rodar):
  - `lgpd-anonymization/assets/anonymization-recipes.md` (receitas SQL/Python)
  - `lgpd-dpa/assets/dpa-template.md` (template das 12 cláusulas Art. 39)
  - `lgpd-vendor-audit/assets/vendor-checklist.md` (checklist de due diligence)
- `lgpd-audit`: `description` enxugada (1023 → 768 chars) para folga sob o limite de 1024 da spec de skills

## [1.1.0] - 2026-05-29

### Adicionado
- Suporte a instalação como **plugin do Claude Code** via marketplace:
  `/plugin marketplace add goul4rt/lgpd-skills` + `/plugin install lgpd-skills@lgpd-skills`
- Manifests `.claude-plugin/marketplace.json` e `.claude-plugin/plugin.json`

### Alterado
- Skills reorganizadas sob `skills/` (auto-descobertas pelo plugin)
- README: instalação via plugin como opção recomendada; instalação manual mantida (`cp -r skills/lgpd-* ...`)

## [1.0.0] - 2026-05-28

### Adicionado
- 1 skill maestro: `lgpd-audit`
- 18 sub-skills cobrindo todo o ciclo de conformidade LGPD
- Pipelines A (Greenfield), B (Legacy retrofit), C (Híbrido), D (Incidente)
- Encode normativo rígido em `lgpd-audit/references/normative-reference.md`
- Templates para ROPA, RIPD, LIA, política de privacidade, notificações ANPD e a titulares
- Schemas Prisma para consent ledger, audit logging encadeado, Guardian/MinorLink (ECA Digital)
- Endpoints DSAR de referência para Next.js + Better Aut h + React Native
- Cobertura: LGPD, Res. ANPD 2/2022, 4/2023, 15/2024, 18/2024, 19/2024, 30/2025, 31/2025
- Cobertura: Lei 15.211/2025 (ECA Digital) em vigor desde 17/03/2026
- README bilíngue (PT-BR principal + visão geral em EN)
- Licença MIT

[1.2.0]: https://github.com/goul4rt/lgpd-skills/releases/tag/v1.2.0
[1.1.1]: https://github.com/goul4rt/lgpd-skills/releases/tag/v1.1.1
[1.1.0]: https://github.com/goul4rt/lgpd-skills/releases/tag/v1.1.0
[1.0.0]: https://github.com/goul4rt/lgpd-skills/releases/tag/v1.0.0
