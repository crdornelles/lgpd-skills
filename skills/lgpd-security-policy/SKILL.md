---
name: lgpd-security-policy
description: Draft the organization's Política de Segurança da Informação and the security awareness and training program that LGPD Art. 46 and ANPD's security guide expect — roles and responsibilities, acceptable use, access control, classification, devices and remote work, backup, incident reporting, disciplinary rules, plus a training track with schedule and attendance log. Use when user asks "política de segurança da informação", "PSI", "política de segurança", "treinamento de segurança", "conscientização", "programa de treinamento LGPD", "onboarding de segurança", or when lgpd-security-baseline reports the administrative measures (policy, training) as missing. Produces drafts for management approval; never presents a draft as an approved policy.
---

# Política de segurança da informação e programa de conscientização

O guia de segurança da ANPD abre pelas medidas administrativas, antes das técnicas: **política de segurança da informação** e **conscientização e treinamento**. A ISO 27001 pede o mesmo (Anexo A 5.1, 5.2, 5.10, 6.3) e o CIS também (controle 14). O motivo é simples: a maior parte dos incidentes começa em gente (senha reutilizada, phishing, notebook sem cifra, acesso que ficou depois da saída), e código não corrige isso.

Esta skill produz dois rascunhos: a política e o programa de treinamento. Os dois dependem de aprovação da direção e de aplicação real; um documento nunca aplicado é `em parte` na matriz do `lgpd-security-baseline`.

## Princípios de escrita

- **Curta e aplicável.** Política de 40 páginas ninguém lê. Para uma equipe pequena, 4 a 8 páginas com regras que cabem no dia a dia. Regra que ninguém vai seguir não entra.
- **Diz quem faz o quê.** Cada seção nomeia o responsável (função, não pessoa, para não apodrecer na primeira saída).
- **Lê o que já existe.** Antes de escrever, levante o que o projeto já implementa (MFA, expiração de sessão, backup, auditoria) e escreva a regra a partir do que o sistema já faz cumprir. A regra que o software aplica sozinho é a mais barata.
- **Cita a norma quando há norma.** Art. 46 (medidas de segurança), Art. 47 (sigilo, inclusive após o fim do tratamento), Art. 48 (incidente), Art. 50 (governança). Res. CD/ANPD 15/2024 para os prazos de incidente.
- **Separa política de procedimento.** A política diz "backup diário, cifrado, com prova de restauração mensal"; o runbook diz como. Não misture.

## Workflow

1. **Levante o contexto**: tamanho da equipe, quem administra a produção, se há escritório, se há dispositivos da empresa ou pessoais, quais sistemas de terceiros a equipe usa (repositório, nuvem, e-mail, chat, gerenciador de senhas), se o projeto é ATPP.
2. **Levante o que o sistema já faz cumprir**: MFA, bloqueio de sessão, hash de senha, revogação na saída, auditoria, backup, retenção. Cada um vira uma regra da política com a evidência ao lado (isso alimenta o `lgpd-security-baseline`).
3. **Preencha `assets/security-policy-template.md`** em `.lgpd/security/policy.md`, marcando `{decisão}` onde a direção precisa escolher (prazo de revisão de acesso, dispositivo pessoal permitido ou não, gerenciador de senhas obrigatório).
4. **Preencha `assets/training-program-template.md`** em `.lgpd/security/training.md`: trilha de onboarding, reciclagem anual, temas do guia da ANPD e do CIS 14, e a tabela de registro.
5. **⏸ CHECKPOINT**: entregue os dois rascunhos e as decisões pendentes. A política só vale depois de aprovada (nome, cargo, data no cabeçalho) e comunicada (registro de leitura).
6. Atualize `.lgpd/STATUS.md` e a matriz do `lgpd-security-baseline` (itens A1, A2 e os controles ISO/CIS correspondentes).

## O que a política precisa cobrir (mínimo)

| Seção | Por quê | Referência |
|---|---|---|
| Objetivo, escopo e aprovação | sem escopo, ninguém sabe se vale para o freelancer | ISO 5.1, 5.4 |
| Papéis: direção, responsável pela segurança, encarregado, todos | guia ANPD A1.2; ISO 5.2; Res. 18/2024 (encarregado) | |
| Classificação da informação, com dado pessoal e sensível como classes próprias | ISO 5.12; LGPD Art. 5º, II | |
| Uso aceitável: contas, senhas, MFA, gerenciador de senhas, e-mail, chat, IA generativa | guia ANPD A1.3; ISO 5.10; CIS 5.2, 6.3 | |
| Controle de acesso: concessão, revisão, revogação; menor privilégio; conta administrativa separada | guia ANPD T1; ISO 5.15 a 5.18, 8.2; CIS 5, 6 | |
| Dispositivos e trabalho remoto: cifra de disco, bloqueio, atualização, rede, dispositivo pessoal | guia ANPD T5; ISO 6.7, 8.1; CIS 3.6, 4.3 | |
| Desenvolvimento e produção: revisão de código, segredos fora do código, ambientes separados, dado real fora do teste, mudança por PR | ISO 8.25 a 8.33 | |
| Dados pessoais: minimização, retenção, exportação e exclusão só pelos caminhos previstos, nada de dado pessoal em log, chat ou ferramenta não aprovada | LGPD Art. 6º, 46; ISO 5.34 | |
| Backup e continuidade: o que, frequência, cifra, prova de restauração, RPO e RTO | guia ANPD T2; ISO 8.13, 5.30; CIS 11 | |
| Terceiros: só com contrato e avaliação; lista de suboperadores | guia ANPD A3; ISO 5.19 a 5.23; CIS 15 | |
| Incidentes: o que é, como reportar (canal, prazo interno), quem decide, comunicação à ANPD em 3 dias úteis | LGPD Art. 48; Res. 15/2024; ISO 5.24 a 5.28, 6.8; CIS 17 | |
| Consequências do descumprimento | ISO 6.4 | |
| Revisão: periodicidade e gatilhos (incidente, mudança de arquitetura, norma nova) | ISO 5.1 | |

## Programa de conscientização (mínimo)

Temas do guia da ANPD (A2.2) e do CIS 14: senhas e MFA; phishing e engenharia social; manuseio de dado pessoal (o que pode ir para onde); dispositivos e redes; como reconhecer e reportar incidente; exposição não intencional (planilha compartilhada, print, log). Para quem desenvolve, acrescente: segredos, injeção, isolamento por inquilino, dependências.

Formato para equipe pequena: sessão de onboarding (1 h, antes do primeiro acesso à produção), reciclagem anual (1 h), leitura da política com registro, e um simulado de phishing por ano se houver ferramenta. Registro: nome, trilha, data, quem conduziu.

## Status update

```markdown
## F17 — Security policy ✓
- Política em `.lgpd/security/policy.md` (rascunho, {N} decisões pendentes da direção)
- Programa de treinamento em `.lgpd/security/training.md`
- Próximo: aprovação e registro de leitura; depois lgpd-operator (se operador) ou lgpd-incident-response
```

> Rascunho não é política. Só vale depois de aprovado pela direção, comunicado à equipe e aplicado. Em pontos trabalhistas (dispositivo pessoal, monitoramento, sanção) ouça o jurídico.
