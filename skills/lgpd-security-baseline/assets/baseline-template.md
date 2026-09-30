# Baseline de segurança — matriz de aderência

**Projeto**: {nome} | **Commit avaliado**: {hash} | **Data**: {data} | **Quem avaliou**: {nome}
**Papéis LGPD**: {controlador / operador / ambos, com a descrição de cada tratamento}
**Porte**: {ATPP (Res. CD/ANPD 2/2022) ou não}
**Hospedagem**: {provedor, região, VM ou gerenciado}
**Edições usadas**: guia da ANPD (2021), ISO/IEC 27001:2022, ISO/IEC 27701:2025, CIS Controls v8 IG1
**Próxima revisão**: {data + 6 meses, ou a cada mudança de arquitetura}

## Legenda

| Situação | Significado |
|---|---|
| `cumpre` | o controle existe, funciona e tem evidência apontada |
| `em parte` | existe, mas com lacuna descrita (sem teste, sem rotina, só documentado) |
| `não cumpre` | não existe |
| `não se aplica` | não cabe ao projeto; o motivo está na evidência |

**Dono**: `código` (muda com commit), `operação` (infra, deploy, rotina) ou `processo` (política, treinamento, contrato, pessoas).

## Resumo

| Padrão | Cumpre | Em parte | Não cumpre | Não se aplica | Total |
|---|---|---|---|---|---|
| Guia de segurança da ANPD | | | | | |
| ISO/IEC 27001 Anexo A | | | | | |
| ISO/IEC 27701:2025 (tabela {A.1 / A.2 / A.1 e A.2}) | | | | | |
| CIS Controls v8 IG1 | | | | | 56 |

**O que impede dizer "seguimos o guia da ANPD" hoje**: {as 3 a 5 lacunas que pesam mais}.

---

## 1. Guia de segurança da ANPD

Itens em `references/anpd-guia-seguranca.md`.

### Medidas administrativas

| Item | Controle | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| A1.1 | Política escrita e aprovada | | | processo | |
| A1.2 | Papéis e responsabilidades | | | processo | |
| A1.3 | Uso aceitável | | | processo | |
| A1.4 | Comunicada e revisada | | | processo | |
| A1.5 | Prevê incidentes e comunicação à ANPD | | | processo | |
| A2.1 | Treinamento inicial e periódico | | | processo | |
| A2.2 | Temas cobertos | | | processo | |
| A2.3 | Registro de participação | | | processo | |
| A3.1 | Contrato com cada fornecedor com dado pessoal | | | processo | |
| A3.2 | Sigilo e comunicação de incidente | | | processo | |
| A3.3 | Instruções e devolução ao fim | | | processo | |
| A3.4 | Sigilo com colaboradores | | | processo | |

### Medidas técnicas

| Item | Controle | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| T1.1 | Conta individual | | | | |
| T1.2 | Menor privilégio | | | | |
| T1.3 | Senha forte, hash, bloqueio | | | | |
| T1.4 | MFA | | | | |
| T1.5 | Revisão e revogação de acesso | | | | |
| T1.6 | Log de acessos e ações administrativas | | | | |
| T1.7 | Bloqueio de sessão | | | | |
| T2.1 | Inventário de onde os dados estão | | | | |
| T2.2 | Cifra em repouso | | | | |
| T2.3 | Backup cifrado fora do ambiente | | | | |
| T2.4 | Prova de restauração | | | | |
| T2.5 | Descarte seguro | | | | |
| T2.6 | Acesso ao banco e aos arquivos | | | | |
| T3.1 | TLS externo, HSTS | | | | |
| T3.2 | Cifra interna e no banco | | | | |
| T3.3 | E-mail e mensagens | | | | |
| T3.4 | Wi-Fi e acesso remoto | | | | |
| T4.1 | Atualização de dependências | | | | |
| T4.2 | Antimalware | | | | |
| T4.3 | Firewall e exposição mínima | | | | |
| T4.4 | Varredura e correção | | | | |
| T4.5 | Configuração segura | | | | |
| T4.6 | Logs para investigação | | | | |
| T5.1 a T5.3 | Dispositivos móveis | | | | |
| T6.1 | Provedor e contrato | | | | |
| T6.2 | Responsabilidades compartilhadas | | | | |
| T6.3 | Localização e transferência | | | | |
| T6.4 | Controles na nuvem | | | | |
| I1 | Plano de resposta | | | | |
| I2 | Comunicação em 3 dias úteis | | | | |
| I3 | Registro por 5 anos | | | | |

## 2. ISO/IEC 27001:2022 — Anexo A

Controles em `references/iso-27001-anexo-a.md`. Uma linha por controle; os físicos (7.x) podem ir numa linha só quando forem todos do provedor.

| Id | Controle | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| 5.1 | | | | | |
| … | | | | | |
| 8.34 | | | | | |

## 3. ISO/IEC 27701:2025 — Anexo A

Controles em `references/iso-27701.md`. Só a tabela do papel do projeto (A.1 controlador, A.2 operador). Os controles de segurança da tabela A.3 ficam na seção 2, na coluna "com dado pessoal?". Matriz feita com a edição de 2019 (cláusulas 7 e 8) é legado: marque aqui e replaneje.

| Id | Controle | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| A.1.2.2 | | | | | |
| … | | | | | |

## 4. CIS Controls v8 — IG1

Salvaguardas em `references/cis-v8-ig1.md`.

| Id | Salvaguarda | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| 1.1 | | | | | |
| … | | | | | |
| 17.3 | | | | | |

### IG2 que se aplica

| Id | Salvaguarda | Situação | Evidência | Dono | Lacuna |
|---|---|---|---|---|---|
| | | | | | |

---

## 5. Achados e encaminhamentos

### Código (`.lgpd/security/findings.md`)

| Id | Prioridade | Controles | Onde | O que falta | Correção | Teste que provaria |
|---|---|---|---|---|---|---|
| SB-01 | P0 / P1 / P2 / P3 | | | | | |

### Operação (runbook ou checklist de produção)

| Id | Controles | O que falta | Onde entra |
|---|---|---|---|
| | | | |

### Processo (documentos a produzir)

| Id | Controles | Documento | Skill |
|---|---|---|---|
| | A1, 5.1 | Política de segurança | `lgpd-security-policy` |
| | A2, 6.3, 14.x | Programa de treinamento | `lgpd-security-policy` |
| | A3, 5.20, A.2.2.2 | Contrato de operador com as contas | `lgpd-operator` |
| | 5.19, 15.1 | Fichas de suboperadores | `lgpd-vendor-audit`, `lgpd-operator` |
| | I1 a I3, 5.24 a 5.28 | Runbook de incidente | `lgpd-incident-response` |

## 6. O que não foi verificado

{Tudo o que a avaliação não conseguiu conferir: produção não existe, contrato não foi visto, treinamento não tem registro. Lacuna que ninguém sabe se existe é lacuna.}

> Aderência não é certificação. A ISO 27001 certifica-se por auditoria de organismo certificador independente; a ANPD não certifica. Este documento diz o que existe, com evidência, e o que falta.
