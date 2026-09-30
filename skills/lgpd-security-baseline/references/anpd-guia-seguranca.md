# Guia de Segurança da Informação da ANPD — itens para a matriz

Fonte: ANPD, *Guia Orientativo: Segurança da Informação para Agentes de Tratamento de Pequeno Porte* (outubro de 2021), disponível em gov.br/anpd, seção "Guias orientativos". O guia é orientativo, não vinculante, e foi escrito para ATPP (Res. CD/ANPD 2/2022, Art. 13); a ANPD o cita como referência de "boas práticas" para o Art. 46 da LGPD. **Confira a versão vigente e a numeração das seções no PDF oficial antes de citar; a lista abaixo usa o nome do tema como chave, não o número.**

O guia divide as medidas em **administrativas** (dependem de pessoas e decisões) e **técnicas** (dependem de configuração e código). Para cada tema, os itens que o guia recomenda e o que serve de evidência num projeto de software.

## Medidas administrativas

### A1. Política de segurança da informação

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| A1.1 | Política escrita, simples, aprovada pela direção | `.lgpd/security/policy.md` aprovada, com data e responsável (`lgpd-security-policy`) |
| A1.2 | Define papéis e responsabilidades (quem cuida da segurança, quem é o encarregado) | seção de papéis na política; `.lgpd/encarregado.md` |
| A1.3 | Regras de uso aceitável de sistemas, senhas, e-mail e dispositivos | seção de uso aceitável; termo assinado no onboarding |
| A1.4 | Comunicada a todos e revisada periodicamente | registro de leitura; data da última revisão no cabeçalho |
| A1.5 | Prevê o tratamento de incidentes e a comunicação à ANPD | `.lgpd/incidents/runbook.md` (`lgpd-incident-response`) |

### A2. Conscientização e treinamento

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| A2.1 | Treinamento inicial e periódico em segurança e proteção de dados | programa em `.lgpd/security/training.md` com trilha, periodicidade e registro de presença |
| A2.2 | Temas: senhas e MFA, phishing e engenharia social, uso de dispositivos e redes, manuseio de dado pessoal, como reportar incidente | conteúdo da trilha; simulado de phishing, se houver |
| A2.3 | Registro de quem foi treinado e quando | planilha ou tabela com nome, data, trilha |

### A3. Acordos contratuais (gerenciamento de contratos)

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| A3.1 | Contrato com cada fornecedor que trata dado pessoal, com cláusulas de segurança e proteção de dados | `.lgpd/vendors/{vendor}.md` com DPA assinado (`lgpd-dpa`, `lgpd-vendor-audit`) |
| A3.2 | Cláusula de sigilo e de comunicação de incidente | cláusulas 4 e 8 do DPA |
| A3.3 | Instruções do controlador ao operador e devolução ou eliminação ao fim | cláusulas 3 e 9 do DPA; para SaaS, o contrato com as contas (`lgpd-operator`) |
| A3.4 | Termo de sigilo com colaboradores | NDA no onboarding |

## Medidas técnicas

### T1. Controle de acesso

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T1.1 | Conta individual por pessoa; nada de conta compartilhada | tabela de usuários e vínculos; proibição de conta genérica na política |
| T1.2 | Menor privilégio: cada um acessa só o que precisa | papéis e permissões que negam por padrão; teste de que toda rota declara permissão |
| T1.3 | Senha forte, com hash adequado; bloqueio por tentativas | serviço de senha (Argon2id ou bcrypt), política de tamanho, bloqueio e captcha, com testes |
| T1.4 | Autenticação em dois fatores, ao menos para administradores | MFA disponível; obrigatório para staff e admin |
| T1.5 | Revisão periódica de acessos e revogação imediata na saída | rotina de revisão; teste de que a saída derruba sessão, vínculo e chaves |
| T1.6 | Registro (log) de acessos e de ações administrativas | auditoria de autenticação e de configuração; imutabilidade |
| T1.7 | Bloqueio de sessão por inatividade | expiração do token de acesso e da sessão |

### T2. Segurança dos dados armazenados

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T2.1 | Inventário de onde os dados pessoais estão (sistemas, bancos, arquivos, planilhas) | `.lgpd/data-map.md`; mapa de PII no código |
| T2.2 | Criptografia em repouso, ao menos para dados sensíveis e credenciais | cifra de volume ou TDE; cifra por campo (CPF, tokens, credenciais) com chaveiro e rotação |
| T2.3 | Backup periódico, cifrado, guardado fora do ambiente principal | ferramenta e agenda de backup; repositório separado; cifra do backup |
| T2.4 | Teste de restauração do backup | prova de restauração registrada (data, tempo, resultado) |
| T2.5 | Descarte seguro de dados e mídias | rotina de expurgo e anonimização; retenção por categoria (`lgpd-retention-erasure`) |
| T2.6 | Controle de acesso ao banco e aos arquivos (não expor porta pública, credencial própria da aplicação) | portas presas em localhost ou rede privada; papel de banco da aplicação sem superpoderes; RLS ou isolamento por inquilino |

### T3. Comunicação segura

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T3.1 | HTTPS/TLS em todo tráfego externo, com certificado válido | proxy com TLS; HSTS; teste do cabeçalho |
| T3.2 | Cifra na comunicação entre serviços internos e com o banco quando atravessa rede | TLS no banco e no Redis; VPN ou rede privada |
| T3.3 | E-mail e mensagens com dado pessoal só por canal cifrado | SMTP com TLS; nada de dado pessoal em log ou em canal aberto |
| T3.4 | Wi-Fi e acesso remoto protegidos | política de uso; VPN para administração |

### T4. Gestão de vulnerabilidades

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T4.1 | Atualização de sistemas, bibliotecas e dependências | Dependabot/Renovate; `audit` no CI; imagens com base atualizada |
| T4.2 | Antivírus e proteção contra código malicioso nos dispositivos | política de dispositivos; antivírus no endpoint; scan de upload quando o produto aceita arquivos |
| T4.3 | Firewall e exposição mínima de serviços | portas expostas só as necessárias; firewall da VM ou do provedor |
| T4.4 | Varredura de vulnerabilidades e correção priorizada | scanner de imagem e SAST no CI; processo de correção com prazo por severidade |
| T4.5 | Configuração segura (remover padrões, desligar o que não usa) | validação de ambiente que recusa configuração insegura em produção; imagens sem root |
| T4.6 | Registro de logs para investigar incidente | logs centralizados com retenção definida; auditoria |

### T5. Segurança em dispositivos móveis

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T5.1 | Cifra e bloqueio de tela nos dispositivos que acessam dados | política de dispositivos; MDM, se houver |
| T5.2 | Apagamento remoto em perda ou roubo | política; MDM |
| T5.3 | Separação entre uso pessoal e profissional | política |

Num SaaS sem app móvel próprio, o tema vale para os dispositivos da equipe (notebooks e celulares de quem administra), não para o produto.

### T6. Serviços em nuvem

| Item | O que o guia pede | Evidência típica |
|---|---|---|
| T6.1 | Escolha do provedor com critérios de segurança e contrato com cláusulas de proteção de dados | ficha do provedor em `.lgpd/vendors/`; certificações (ISO 27001, SOC 2) do provedor |
| T6.2 | Clareza sobre responsabilidades compartilhadas (o que é do provedor, o que é seu) | matriz de responsabilidade na política ou no runbook |
| T6.3 | Localização dos dados e transferência internacional | região do provedor; `.lgpd/transfers/` quando fora do Brasil (`lgpd-international-transfer`) |
| T6.4 | Cifra, backup e controle de acesso também na nuvem | mesmos itens de T1 a T3 aplicados à nuvem; MFA na conta do provedor |

## Incidentes

O guia trata a resposta a incidentes junto com a política e a comunicação à ANPD (Art. 48). Use a skill `lgpd-incident-response` e registre na matriz:

| Item | O que se espera | Evidência típica |
|---|---|---|
| I1 | Plano de resposta com responsável, contenção, avaliação e comunicação | `.lgpd/incidents/runbook.md` |
| I2 | Comunicação à ANPD e aos titulares em 3 dias úteis (Res. CD/ANPD 15/2024, Art. 6º e 9º; ATPP em dobro) | modelo de comunicação; teste de mesa anual |
| I3 | Registro de todos os incidentes por no mínimo 5 anos (Res. 15/2024, Art. 10) | `.lgpd/incidents/log.md` |
