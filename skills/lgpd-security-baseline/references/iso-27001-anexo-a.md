# ISO/IEC 27001:2022 — Anexo A (93 controles)

O Anexo A da ISO/IEC 27001:2022 lista 93 controles em quatro temas; a ISO/IEC 27002:2022 descreve cada um. As normas são pagas: a lista abaixo traz só o identificador e o nome do controle, para a matriz apontar cada linha; a orientação de implementação é da 27002 e não deve ser copiada. Na coluna "Toca um SaaS?" está a leitura desta skill sobre o que costuma se aplicar a um produto hospedado em nuvem ou VM, sem escritório e sem servidor físico próprio. Ajuste ao caso.

Certificação ISO 27001 exige o sistema de gestão (cláusulas 4 a 10: contexto, liderança, planejamento, apoio, operação, avaliação e melhoria), a Declaração de Aplicabilidade (SoA) e auditoria de organismo acreditado. A matriz cobre o Anexo A; não substitui a SoA nem a auditoria.

## 5. Controles organizacionais (37)

| Id | Controle | Toca um SaaS? | Evidência típica |
|---|---|---|---|
| 5.1 | Políticas de segurança da informação | sim | política aprovada e comunicada |
| 5.2 | Papéis e responsabilidades | sim | seção da política; encarregado |
| 5.3 | Segregação de funções | sim | quem aprova deploy não é quem escreve sozinho; revisão de código; quatro olhos em ação de risco |
| 5.4 | Responsabilidades da direção | sim | aprovação da política pela direção |
| 5.5 | Contato com autoridades | sim | procedimento de comunicação à ANPD e à polícia no runbook de incidente |
| 5.6 | Contato com grupos de interesse especial | parcial | assinatura de avisos de segurança (CERT.br, advisories dos fornecedores) |
| 5.7 | Inteligência de ameaças | parcial | acompanhamento de advisories; Dependabot |
| 5.8 | Segurança em gestão de projetos | sim | checklist de segurança em sprint ou ADR |
| 5.9 | Inventário de informações e ativos | sim | inventário de sistemas, repositórios, domínios, provedores |
| 5.10 | Uso aceitável de informações e ativos | sim | seção de uso aceitável da política |
| 5.11 | Devolução de ativos | sim | checklist de offboarding |
| 5.12 | Classificação da informação | sim | níveis (público, interno, confidencial, dado pessoal, sensível) na política; mapa de PII |
| 5.13 | Rotulagem da informação | parcial | marcação de dado pessoal no schema ou no mapa |
| 5.14 | Transferência de informações | sim | canais permitidos; TLS; nada de dado pessoal por canal aberto |
| 5.15 | Controle de acesso | sim | política de acesso; permissões negam por padrão |
| 5.16 | Gestão de identidade | sim | conta individual; ciclo de vida do vínculo |
| 5.17 | Informações de autenticação | sim | hash de senha, política de senha, segredos fora do código |
| 5.18 | Direitos de acesso | sim | concessão, revisão e revogação; teste de que a saída revoga tudo |
| 5.19 | Segurança nas relações com fornecedores | sim | avaliação de fornecedores (`lgpd-vendor-audit`) |
| 5.20 | Segurança nos acordos com fornecedores | sim | DPA (`lgpd-dpa`) |
| 5.21 | Segurança na cadeia de suprimento de TIC | sim | dependências e imagens fixadas; inventário de componentes |
| 5.22 | Monitoramento e revisão de serviços de fornecedores | sim | revisão periódica das fichas de fornecedor |
| 5.23 | Segurança no uso de serviços em nuvem | sim | ficha do provedor; responsabilidades compartilhadas; região |
| 5.24 | Planejamento e preparação para incidentes | sim | runbook de incidente |
| 5.25 | Avaliação e decisão sobre eventos | sim | critério do Art. 5º da Res. 15/2024 no runbook |
| 5.26 | Resposta a incidentes | sim | runbook; contenção |
| 5.27 | Aprendizado com incidentes | sim | pós-incidente no log; simulado |
| 5.28 | Coleta de evidências | sim | preservação de logs e auditoria; guarda por 5 anos |
| 5.29 | Segurança durante disrupção | sim | plano de continuidade; RPO e RTO |
| 5.30 | Prontidão de TIC para continuidade | sim | backup com prova de restauração; redundância |
| 5.31 | Requisitos legais, estatutários, regulatórios e contratuais | sim | LGPD, Marco Civil, CDC, contratos; `.lgpd/` |
| 5.32 | Direitos de propriedade intelectual | sim | licenças de dependências; avisos de terceiros |
| 5.33 | Proteção de registros | sim | auditoria imutável com retenção; registro de incidentes |
| 5.34 | Privacidade e proteção de dados pessoais | sim | todo o `.lgpd/`; direitos do titular |
| 5.35 | Análise crítica independente | parcial | auditoria de segurança externa ou por outra pessoa; pentest |
| 5.36 | Conformidade com políticas e normas | sim | testes de arquitetura que reprovam regressão; revisão periódica |
| 5.37 | Procedimentos operacionais documentados | sim | runbooks |

## 6. Controles de pessoas (8)

| Id | Controle | Toca um SaaS? | Evidência típica |
|---|---|---|---|
| 6.1 | Seleção (screening) | sim | verificação na contratação, proporcional ao acesso |
| 6.2 | Termos e condições de contratação | sim | cláusulas de sigilo e segurança no contrato de trabalho ou prestação |
| 6.3 | Conscientização, educação e treinamento | sim | programa de treinamento (`lgpd-security-policy`) |
| 6.4 | Processo disciplinar | sim | previsão na política |
| 6.5 | Responsabilidades após encerramento ou mudança | sim | offboarding; sigilo que sobrevive ao contrato |
| 6.6 | Acordos de confidencialidade | sim | NDA |
| 6.7 | Trabalho remoto | sim | regras de dispositivo e rede na política |
| 6.8 | Relato de eventos de segurança | sim | canal de reporte no runbook; treinamento |

## 7. Controles físicos (14)

Num SaaS sem sede e sem servidor próprio, quase tudo aqui é do provedor de hospedagem: marque `não se aplica` com o motivo e aponte a certificação do provedor (ISO 27001 ou SOC 2) como evidência de que o controle existe lá. O que continua seu: os dispositivos da equipe (7.9, 7.10, 7.14) e a mesa limpa (7.7).

| Id | Controle | Toca um SaaS? |
|---|---|---|
| 7.1 | Perímetros de segurança física | provedor |
| 7.2 | Entrada física | provedor |
| 7.3 | Segurança de escritórios, salas e instalações | provedor / escritório se houver |
| 7.4 | Monitoramento de segurança física | provedor |
| 7.5 | Proteção contra ameaças físicas e ambientais | provedor |
| 7.6 | Trabalho em áreas seguras | provedor |
| 7.7 | Mesa limpa e tela limpa | sim (equipe) |
| 7.8 | Localização e proteção de equipamentos | provedor |
| 7.9 | Segurança de ativos fora das instalações | sim (notebooks e celulares) |
| 7.10 | Mídias de armazenamento | sim (cifra de disco; descarte) |
| 7.11 | Utilidades de apoio | provedor |
| 7.12 | Segurança do cabeamento | provedor |
| 7.13 | Manutenção de equipamentos | provedor |
| 7.14 | Descarte ou reutilização segura de equipamentos | sim (equipe) / provedor |

## 8. Controles tecnológicos (34)

| Id | Controle | Toca um SaaS? | Evidência típica |
|---|---|---|---|
| 8.1 | Dispositivos de endpoint do usuário | sim | política de dispositivos; cifra de disco; bloqueio |
| 8.2 | Direitos de acesso privilegiado | sim | backoffice com papel próprio, MFA obrigatório, impersonação com prazo e motivo |
| 8.3 | Restrição de acesso à informação | sim | permissões; visibilidade por dono e equipe; isolamento por inquilino |
| 8.4 | Acesso ao código-fonte | sim | repositório privado; branch protegida; revisão |
| 8.5 | Autenticação segura | sim | hash de senha, MFA, bloqueio, captcha, sessão com rotação |
| 8.6 | Gestão de capacidade | sim | métricas; alertas de fila e latência |
| 8.7 | Proteção contra malware | parcial | endpoint; scan de upload se o produto aceita arquivos |
| 8.8 | Gestão de vulnerabilidades técnicas | sim | Dependabot; `audit`; scanner de imagem; prazo por severidade |
| 8.9 | Gestão de configuração | sim | infra como código; validação de ambiente; imagens reproduzíveis |
| 8.10 | Exclusão de informações | sim | retenção e expurgo; anonimização; direito de exclusão |
| 8.11 | Mascaramento de dados | sim | redação de PII em log; mascaramento antes de modelo de IA |
| 8.12 | Prevenção de vazamento de dados | parcial | exportação auditada; limites; dado pessoal fora de log e trace |
| 8.13 | Backup das informações | sim | backup contínuo, cifrado, fora do ambiente, com prova |
| 8.14 | Redundância de recursos de processamento | parcial | réplica; múltiplas zonas; RTO |
| 8.15 | Registro de logs (logging) | sim | logs de aplicação e auditoria com retenção |
| 8.16 | Atividades de monitoramento | sim | métricas, alertas com runbook, rastreamento |
| 8.17 | Sincronização de relógio | sim | NTP nos hosts (padrão do provedor) |
| 8.18 | Uso de programas utilitários privilegiados | sim | acesso ao banco só por papel restrito; superusuário fora da aplicação |
| 8.19 | Instalação de software em sistemas operacionais | sim | imagens imutáveis; nada instalado à mão |
| 8.20 | Segurança de redes | sim | portas mínimas; firewall; rede privada entre serviços |
| 8.21 | Segurança de serviços de rede | sim | TLS; proxy |
| 8.22 | Segregação de redes | sim | banco e filas fora da internet |
| 8.23 | Filtragem web | parcial | proxy de saída; bloqueio de rede interna em requisição a endereço do cliente (SSRF) |
| 8.24 | Uso de criptografia | sim | TLS, cifra em repouso e por campo, chaveiro, rotação, hash |
| 8.25 | Ciclo de vida de desenvolvimento seguro | sim | guia de engenharia; regras que não mudam sem ADR |
| 8.26 | Requisitos de segurança de aplicações | sim | requisitos por sprint; testes |
| 8.27 | Arquitetura e engenharia seguras | sim | isolamento por inquilino; negar por padrão; validação de entrada |
| 8.28 | Codificação segura | sim | lint; validação; `safeRequest`; testes de arquitetura |
| 8.29 | Testes de segurança em desenvolvimento e aceitação | sim | testes de isolamento, permissão, RLS no CI |
| 8.30 | Desenvolvimento terceirizado | se houver | contrato e revisão |
| 8.31 | Separação de ambientes | sim | dev, teste, produção separados; dado de produção fora do teste |
| 8.32 | Gestão de mudanças | sim | PR, revisão, CI, migrations versionadas |
| 8.33 | Informações de teste | sim | dados sintéticos; nunca dado real em teste |
| 8.34 | Proteção de sistemas durante auditoria | parcial | acesso do auditor só leitura e com prazo |
