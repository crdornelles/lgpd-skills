---
name: lgpd-security-baseline
description: Build an evidence-backed adherence matrix of the project against the security references for LGPD Art. 46 — ANPD's Guia de Segurança da Informação (ATPP, 2021) plus the complementary ISO/IEC 27001:2022 Annex A, ISO/IEC 27701:2025 (PIMS, Annex A controller and processor tables) and CIS Controls v8 (IG1). Use when user asks "seguimos o guia da ANPD?", "ISO 27001", "ISO 27701", "CIS Controls", "matriz de aderência", "baseline de segurança", "medidas de segurança do Art. 46", "o que falta para dizer que somos seguros", "due diligence de segurança", or when a customer asks "what security standards do you follow". Each control gets a status, an evidence pointer (file, test, ADR, runbook) and an owner (code, operations or process). Never marks a control as met without evidence.
---

# Baseline de segurança — guia da ANPD, ISO 27001/27701 e CIS Controls

Art. 46 LGPD: os agentes de tratamento devem adotar "medidas de segurança, técnicas e administrativas aptas a proteger os dados pessoais". A lei não diz quais. A ANPD aponta, como referência de boa prática, o próprio **Guia Orientativo de Segurança da Informação para Agentes de Tratamento de Pequeno Porte** (2021). A **ISO/IEC 27001** (gestão de segurança da informação), a **ISO/IEC 27701:2025** (sistema de gestão de privacidade, com controles para controlador e operador) e os **CIS Controls** são referências complementares, sem endosso formal da ANPD. Esta skill mede o projeto contra as quatro referências, com evidência.

O resultado responde a duas perguntas que chegam de fora: a do cliente corporativo ("vocês seguem o quê?") e a da ANPD numa fiscalização ("mostrem as medidas do Art. 46"). Sem a matriz, a resposta é adjetivo; com ela, é uma lista de controles com o arquivo, o teste ou a rotina que prova cada um.

## Princípio: nenhum "cumpre" sem evidência

Cada linha da matriz tem quatro colunas obrigatórias:

| Coluna | Valores |
|---|---|
| **Situação** | `cumpre` / `em parte` / `não cumpre` / `não se aplica` |
| **Evidência** | caminho de arquivo + símbolo, nome do teste automatizado, ADR, runbook, configuração de infra, contrato assinado. `não se aplica` exige o motivo |
| **Dono** | `código` (muda com commit), `operação` (infra, deploy, rotina) ou `processo` (política, treinamento, contrato, pessoas) |
| **Lacuna** | o que falta, quando não é `cumpre`; vira item em `.lgpd/gaps.md` |

Regras:

- **Leia o código antes de marcar.** "Tem TLS" não é evidência; `infra/proxy/Caddyfile` com `tls` e o teste que confere o cabeçalho `Strict-Transport-Security` são.
- **Teste automatizado vale mais que leitura.** Quando um controle é protegido por teste de arquitetura (toda rota declara permissão, toda tabela tem RLS, todo acesso passa pelo repositório com escopo), cite o teste: é o que impede a regressão silenciosa.
- **Documento não é controle.** Uma política escrita e nunca aplicada é `em parte`, com a lacuna "sem evidência de aplicação".
- **Separe o que é código do que é processo.** A metade do guia da ANPD (política, treinamento, contratos) não se resolve com commit. Registre o dono certo para o item cair na fila certa.
- **Não force o controle que não se aplica.** Projeto sem escritório e sem servidor próprio marca os controles físicos como `não se aplica`, com o motivo ("hospedagem em provedor; controle físico é do provedor, ver relatório SOC 2 dele").

## Workflow

### 1. Levante a stack e os papéis

Antes de qualquer linha:

- **Papel LGPD** do projeto em cada tratamento: controlador (dados dos próprios usuários e clientes), operador (dados dos clientes dos clientes, num SaaS B2B) ou os dois. Isso decide quais tabelas do Anexo A da ISO 27701:2025 entram (A.1 = controlador, A.2 = operador; A.3 vale para os dois). Se for operador, rode também `lgpd-operator`.
- **Mecanismo de isolamento** (RLS, middleware de tenant, filtro manual), **autenticação** (senha, MFA, sessão), **cifra** (em trânsito, em repouso, por campo), **backup** (ferramenta, frequência, prova de restauração), **logs e auditoria**, **CI e dependências**, **infra** (nuvem gerenciada, VM própria, container), **terceiros** com dado pessoal.
- **Porte:** ATPP (Res. CD/ANPD 2/2022) ou não. O guia da ANPD foi escrito para ATPP; fora dele, as ISO e o CIS pesam mais.

### 2. Colete evidências por tema, não por padrão

Os quatro padrões se sobrepõem. Colete uma vez, por tema, e reaproveite nas quatro tabelas:

| Tema | O que procurar |
|---|---|
| Governança e política | política de segurança, papéis e responsabilidades, encarregado, inventário de ativos, classificação de dados |
| Pessoas | treinamento, onboarding e offboarding, NDA, uso aceitável |
| Controle de acesso | autenticação (hash de senha, MFA, bloqueio, captcha), sessão, autorização que nega por padrão, papéis, chaves de API, privilégios de admin, revogação na saída |
| Criptografia e segredos | TLS e HSTS, cifra em repouso e por campo, chaveiro e rotação, segredos fora do código, validação de ambiente |
| Dados e backup | backup contínuo, cifrado, fora do ambiente, com prova de restauração, RPO e RTO, retenção e expurgo |
| Logs e monitoramento | auditoria imutável, log sem dado pessoal, métricas, alertas com runbook, rastreamento |
| Vulnerabilidades | atualização de dependências, `audit` no CI, SAST, scan de imagem, segredo no histórico, cabeçalhos, rate limit, SSRF, validação de entrada, upload |
| Rede e nuvem | segmentação, portas expostas, proxy, WAF, provedor e região, contrato com o provedor |
| Terceiros | lista de suboperadores, DPA, transferência internacional, avaliação (`lgpd-vendor-audit`) |
| Incidentes e continuidade | runbook, comunicação à ANPD em 3 dias úteis (Res. 15/2024), registro por 5 anos, simulado, plano de continuidade |
| Desenvolvimento seguro | revisão de código, testes de arquitetura contra regressão de segurança, separação de ambientes, dado de produção fora do teste |

Para cada evidência anote caminho, símbolo ou nome do teste e a data em que leu. Evidência sem data apodrece.

### 3. Preencha as quatro tabelas

Use `assets/baseline-template.md`. As listas de controles estão em `references/`:

- `references/anpd-guia-seguranca.md` — os itens do guia da ANPD, por medida administrativa e técnica.
- `references/iso-27001-anexo-a.md` — os 93 controles da ISO/IEC 27001:2022 (Anexo A), por tema.
- `references/iso-27701.md` — os controles do Anexo A da ISO/IEC 27701:2025 para controlador (tabela A.1), operador (tabela A.2) e os de segurança compartilhados (tabela A.3), com o identificador da edição de 2019 entre parênteses.
- `references/cis-v8-ig1.md` — as 56 salvaguardas do Grupo de Implementação 1 dos CIS Controls v8, mais as do IG2 que costumam tocar um SaaS.

Ordem sugerida: guia da ANPD primeiro (é o que a autoridade vai perguntar), depois CIS IG1 (é o mais concreto), depois ISO 27001, e por fim ISO 27701 (só as tabelas do papel do projeto).

### 4. Derive achados e o plano

- Cada `não cumpre` ou `em parte` com dono `código` vira **achado com prioridade** (P0 a P3) e caminho de arquivo, no formato que o projeto já usa para auditoria de segurança. Se o projeto não tem formato, use: id, severidade, controle(s) que toca, onde, o que falta, correção, teste que provaria.
- Cada lacuna com dono `processo` vira **rascunho de documento** (política, treinamento, contrato) pela skill correspondente: `lgpd-security-policy`, `lgpd-dpa`, `lgpd-operator`, `lgpd-incident-response`, `lgpd-dpo-encarregado`.
- Cada lacuna com dono `operação` vira item de runbook ou de checklist de produção.
- Registre tudo em `.lgpd/gaps.md`, com responsável e prazo.

### 5. ⏸ CHECKPOINT

Antes de dar a matriz por pronta, mostre ao usuário: os totais por padrão (cumpre / em parte / não cumpre / não se aplica), os P0 e P1, e os controles marcados `não se aplica` com o motivo. É aqui que a pessoa que conhece a operação corrige o que o código não mostra (o contrato com o provedor existe? o treinamento aconteceu?).

## Prioridade quando o tempo é curto

1. Guia da ANPD, medidas técnicas 4 a 7 (acesso, dados armazenados, comunicação segura, vulnerabilidades): é o que mais aparece em incidente.
2. CIS IG1 controles 1 a 6 (inventários, dados, configuração, contas, acesso) e 11 (backup).
3. Guia da ANPD, medidas administrativas (política, treinamento, contratos): dependem de gente, começam cedo.
4. O resto.

## Onde salvar

```
.lgpd/security/
├── baseline.md            ← a matriz (este template)
├── findings.md            ← achados de código, priorizados
└── evidence/              ← opcional: exportações, prints, relatórios de scanner
```

E acrescente ao `.lgpd/STATUS.md`:

```markdown
## F15 — Security baseline ✓
- Matriz em `.lgpd/security/baseline.md` (guia ANPD {a}/{n}, ISO 27001 {b}/{n}, ISO 27701 {c}/{n}, CIS IG1 {d}/{56})
- {N} achados de código (P0: {x}, P1: {y}) em `.lgpd/security/findings.md`
- {M} lacunas de processo encaminhadas: {skills}
- Próximo: lgpd-operator (se o produto for operador) e lgpd-security-policy
```

## Referências normativas

- LGPD, Art. 46 (medidas de segurança), Art. 46 § 2º (desde a concepção), Art. 47 (sigilo), Art. 48 (comunicação de incidente), Art. 49 (sistemas estruturados para os requisitos de segurança), Art. 50 (boas práticas e governança).
- Res. CD/ANPD 2/2022 (ATPP): Art. 13 orienta a adoção do guia de segurança pela ANPD.
- ANPD, *Guia Orientativo: Segurança da Informação para Agentes de Tratamento de Pequeno Porte*, out/2021 (gov.br/anpd, "Guias orientativos"). Confira a versão vigente antes de citar a numeração das seções.
- ISO/IEC 27001:2022 e ISO/IEC 27002:2022 (o Anexo A lista os controles; a 27002 detalha cada um). Normas pagas: cite pelo identificador do controle, nunca copie o texto integral.
- ISO/IEC 27701:2025 (PIMS), edição vigente desde outubro de 2025; substituiu a de 2019, que a ISO retirou (certificados de 2019 migram até outubro de 2028). A numeração mudou: registre qual edição usou e, se for a de 2019, marque a matriz como legado.
- CIS Controls v8 (e v8.1), Center for Internet Security, licença Creative Commons com atribuição. As salvaguardas do IG1 são a "higiene básica" que o CIS recomenda para toda organização.

> Esta skill mede aderência a padrões; não certifica. Certificação ISO exige auditoria de organismo certificador independente (a acreditação dele é opcional, mas é o que dá valor ao certificado), e a ANPD não certifica ninguém. Diga "seguimos" só com a matriz na mão, e diga "somos certificados" só com o certificado.
