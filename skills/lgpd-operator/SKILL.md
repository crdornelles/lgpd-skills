---
name: lgpd-operator
description: LGPD compliance from the processor's side ("operador", Art. 39) — for a SaaS, platform or agency that processes personal data on behalf of its customers (the controllers). Produces the customer-facing data processing agreement (DPA) with the product as processor, the public sub-processor list with change notice, the processor-side ROPA entries, and the customer duties the product must support (subject requests, return or deletion at termination, incident notice). Use when user says "somos operador", "nossos clientes são os controladores", "DPA para os nossos clientes", "termo de tratamento de dados do SaaS", "lista de suboperadores", "subprocessors", "contrato de operador", "cláusula LGPD no contrato com o cliente", "o cliente pediu nosso DPA", or when lgpd-ropa finds processor activities without a contract. Complements lgpd-dpa (which drafts DPAs with the vendors the organization hires).
---

# O produto como operador

Art. 39 LGPD: "O operador deverá realizar o tratamento segundo as instruções fornecidas pelo controlador, que verificará a observância das próprias instruções e das normas sobre a matéria." Art. 42, § 1º: o operador responde solidariamente quando descumpre a lei ou as instruções.

Um SaaS B2B, uma agência ou uma plataforma que guarda dados dos clientes dos seus clientes é **operador** desses dados e **controlador** só dos dados de quem assina (cadastro, cobrança, uso). As skills `lgpd-dpa` e `lgpd-vendor-audit` olham para um lado da cadeia: os fornecedores que a organização contrata. Esta skill olha para o outro: os clientes que contratam a organização e que vão perguntar "qual é o seu DPA?", "quem são seus suboperadores?", "como vocês nos ajudam a atender um titular?".

## O que a skill produz

| Artefato | Onde | Para quê |
|---|---|---|
| Contrato de operador (DPA do produto) | `.lgpd/operator/dpa-{produto}.md` | anexo ao contrato ou aos termos de uso; o cliente assina ou aceita |
| Lista pública de suboperadores | `.lgpd/operator/subprocessors.md` (e uma página pública) | Art. 39, § 1º por analogia e ISO 27701 8.5.6: o cliente sabe para quem o dado vai |
| Entradas do ROPA como operador | seção II do `.lgpd/ROPA.md` | Art. 37: o operador também mantém registro |
| Matriz de deveres para com o controlador | `.lgpd/operator/customer-duties.md` | o que o produto precisa oferecer para o cliente cumprir a LGPD (exportar, corrigir, excluir, avisar) |

## Workflow

### 1. Separe os papéis

Liste cada tratamento e diga quem decide finalidade e meios:

| Tratamento | Papel do produto | Quem é o titular |
|---|---|---|
| Cadastro, login, cobrança, uso do painel | controlador | o cliente (pessoa que assina e a equipe dele) |
| Contatos, conversas, pedidos, notas que o cliente guarda no produto | operador | os clientes do cliente |
| Métricas agregadas do produto | controlador, se anonimizadas; operador, se identificáveis | |
| Modelos de IA que leem dados do cliente | operador (e o provedor de IA é suboperador) | os clientes do cliente |

Regra: o produto não usa o dado de que é operador para fim próprio (marketing, treino de modelo, venda de lista). Se usa, ele virou controlador daquele tratamento e precisa de base legal própria e aviso ao titular (ISO 27701 8.2.2 e 8.2.3).

### 2. Inventarie os suboperadores

Todo terceiro que recebe dado de que o produto é operador: hospedagem, banco gerenciado, storage, e-mail transacional, mensageria (WhatsApp, SMS), provedor de IA, cobrança (quando o dado do cliente do cliente passa por ele), analytics, suporte, backup fora do ambiente. Para cada um, a ficha do `lgpd-vendor-audit` mais: país, dado que recebe, finalidade, base do Art. 33 se for internacional, e se o cliente pode recusar (se não pode, o contrato precisa dizer que a recusa é rescindir).

Preencha `assets/subprocessors-template.md`. Mantenha a lista **pública** e **versionada**: o contrato promete aviso prévio de mudança, e a lista com data é a prova.

### 3. Escreva o DPA do produto

Use `assets/operator-dpa-template.md`. As 12 cláusulas do `lgpd-dpa` continuam, invertidas: o produto é o operador. Diferenças que importam:

- **Instruções (cl. 3)**: num SaaS as instruções são "o que a interface e a API permitem fazer" e os termos de uso; escreva isso, senão "instruções documentadas" vira letra morta.
- **Suboperadores (cl. 6)**: autorização **geral** com lista pública e aviso prévio de {30} dias com direito de objeção. Autorização específica por suboperador não escala num SaaS.
- **Direitos do titular (cl. 7)**: o produto não responde ao titular no lugar do cliente; ele dá a ferramenta (exportar, corrigir, excluir, anonimizar) e repassa o pedido que receber direto em até {2 dias úteis}. Se o produto tem página pública de pedido do titular por cliente, cite.
- **Incidente (cl. 8)**: prazo do operador para avisar o controlador tem que caber nos 3 dias úteis do controlador (Res. CD/ANPD 15/2024, Art. 6º). {24 horas} do conhecimento é o usual; diga o que o aviso contém (o que aconteceu, dados e titulares afetados, medidas, contato).
- **Devolução e eliminação (cl. 9)**: exportação da conta inteira no encerramento e exclusão em {30} dias, salvo retenção legal; backup expira pela retenção do backup, e o contrato diz isso.
- **Auditoria (cl. 10)**: relatório e evidências (matriz do `lgpd-security-baseline`, certificações) antes de auditoria presencial; auditoria presencial com aviso e custo do cliente.
- **Responsabilidade do controlador (cl. 13, nova)**: base legal, aviso ao titular, consentimento para marketing e uso lícito são do cliente (ISO 27701 8.2.5). O produto pode recusar instrução que viole a lei (8.2.4).
- **Ordem de autoridade (cl. 14, nova)**: pedido de autoridade por dado do cliente é comunicado ao cliente, salvo proibição legal (ISO 27701 8.5.4 e 8.5.5).

### 4. Registre no ROPA como operador

Uma linha "O00N" por tratamento em que o produto é operador (template do `lgpd-ropa`, seção II), apontando o DPA e a lista de suboperadores. Se houver mapa de PII no código, confira que toda tabela com dado do cliente do cliente aparece numa atividade.

### 5. Liste os deveres para com o controlador

Preencha `assets/customer-duties-template.md`: para cada obrigação do cliente (atender titular em 15 dias, corrigir, excluir, informar base legal, comunicar incidente, devolver ao fim), o que o produto oferece hoje (tela, API, rotina), o que falta, e o prazo. O que falta vira achado ou item de roadmap.

### 6. ⏸ CHECKPOINT

Antes de publicar: revisão jurídica do DPA e dos termos; confirmação da lista de suboperadores com quem administra a infraestrutura; decisão sobre os prazos entre chaves. O DPA modelo do produto costuma virar anexo dos termos de uso; a página pública de suboperadores costuma ficar em `/privacidade/suboperadores` ou `/legal/subprocessors`.

## Status update

```markdown
## F18 — Operator ✓
- DPA do produto em `.lgpd/operator/dpa-{produto}.md` (rascunho para revisão jurídica)
- {N} suboperadores em `.lgpd/operator/subprocessors.md` ({M} fora do Brasil, com base do Art. 33)
- {K} atividades como operador no ROPA
- Deveres para com o controlador: {x} atendidos, {y} em falta (roadmap)
- Próximo: publicar a lista; lgpd-international-transfer para os {M}
```

## Referências normativas

- LGPD: Art. 5º, VII (operador); Art. 37 (registro, também do operador); Art. 39 (instruções); Art. 42, § 1º (responsabilidade solidária); Art. 46 e 47 (segurança e sigilo); Art. 48 (comunicação de incidente, pelo controlador); Art. 33 a 36 (transferência internacional).
- Res. CD/ANPD 15/2024 (incidentes, 3 dias úteis do controlador); Res. CD/ANPD 19/2024 (cláusulas-padrão para transferência internacional).
- ISO/IEC 27701:2019, cláusula 8 (controles para operadores): 8.2.1 a 8.2.6, 8.3.1, 8.4.1 a 8.4.3, 8.5.1 a 8.5.8.
- ANPD, *Guia Orientativo para Definições dos Agentes de Tratamento de Dados Pessoais e do Encarregado* (2021, versão 2 em 2022): critérios para distinguir controlador e operador.

> O DPA é peça contratual: passa por advogado antes de ir para o cliente. Prazos entre chaves são sugestões de mercado, não norma; o que a norma fixa é o prazo do controlador (3 dias úteis) e o registro por 5 anos.
