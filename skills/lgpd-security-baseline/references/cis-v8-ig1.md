# CIS Controls v8 — Grupo de Implementação 1 (IG1)

Os CIS Controls v8 (Center for Internet Security, 2021; v8.1 em 2024) têm 18 controles e 153 salvaguardas, divididas em três grupos de implementação. O **IG1** são as 56 salvaguardas de "higiene cibernética essencial", pensadas para organizações pequenas, sem equipe de segurança dedicada: é o mínimo que o CIS recomenda para todo mundo. O IG2 acrescenta 74 salvaguardas para quem tem equipe e trata dado mais sensível; o IG3, 23 para alto risco. A licença é Creative Commons com atribuição (CC BY-NC-ND 4.0 para o documento; confira o texto da licença na página do CIS). A lista abaixo traz identificador e nome; a descrição de cada salvaguarda está no documento oficial.

Vocabulário do CIS traduzido para um SaaS pequeno: "ativo corporativo" inclui as VMs, containers e os notebooks da equipe; "conta" inclui as contas do provedor de nuvem, do repositório, do painel do produto e do banco; "usuário" é a equipe, não o cliente do produto.

## IG1 (56 salvaguardas)

| Id | Salvaguarda | Evidência típica num SaaS |
|---|---|---|
| 1.1 | Estabelecer e manter inventário detalhado de ativos | lista de VMs, containers, domínios, repositórios, dispositivos da equipe |
| 1.2 | Tratar ativos não autorizados | processo de revisão do inventário |
| 2.1 | Estabelecer e manter inventário de software | `package.json`/lockfile; imagens; SBOM se houver |
| 2.2 | Garantir que o software autorizado tem suporte | versões de Node, Postgres, Redis dentro do suporte; Dependabot |
| 2.3 | Tratar software não autorizado | política de dispositivos; imagens imutáveis |
| 3.1 | Estabelecer e manter processo de gestão de dados | política de classificação; `.lgpd/` |
| 3.2 | Estabelecer e manter inventário de dados | `data-map.md`; mapa de PII |
| 3.3 | Configurar listas de controle de acesso aos dados | permissões; isolamento por inquilino; papel de banco restrito |
| 3.4 | Aplicar retenção de dados | `retention.md`; rotinas de expurgo |
| 3.5 | Descartar dados com segurança | expurgo; anonimização; descarte de mídia |
| 3.6 | Cifrar dados em dispositivos de usuário final | cifra de disco nos notebooks (política) |
| 4.1 | Estabelecer e manter processo de configuração segura | infra como código; validação de ambiente; baseline de imagem |
| 4.2 | Processo de configuração segura para infraestrutura de rede | firewall e portas como código |
| 4.3 | Configurar bloqueio automático de sessão | expiração de sessão no produto; bloqueio de tela nos dispositivos |
| 4.4 | Implementar e gerenciar firewall em servidores | firewall da VM ou do provedor com portas mínimas |
| 4.5 | Implementar e gerenciar firewall em dispositivos de usuário final | política de dispositivos |
| 4.6 | Gerenciar ativos e software com segurança | SSH por chave; sem senha padrão; acesso administrativo por VPN ou IP fixo |
| 4.7 | Gerenciar contas padrão | senhas e contas padrão removidas (banco, painel de admin, provedor) |
| 5.1 | Estabelecer e manter inventário de contas | lista de contas de provedor, repositório, banco e produto (staff) |
| 5.2 | Usar senhas únicas | gerenciador de senhas; política; hash forte no produto |
| 5.3 | Desativar contas dormentes | revisão periódica; expiração de chave de API |
| 5.4 | Restringir privilégios de administrador a contas dedicadas | conta de admin separada da conta do dia a dia; papel de staff próprio |
| 6.1 | Estabelecer processo de concessão de acesso | onboarding com papel mínimo |
| 6.2 | Estabelecer processo de revogação de acesso | offboarding; revogação automática na saída (sessão, vínculo, chaves) |
| 6.3 | Exigir MFA em aplicações expostas externamente | MFA no produto, ao menos para admin; MFA no provedor e no repositório |
| 6.4 | Exigir MFA para acesso remoto à rede | VPN com MFA, se houver |
| 6.5 | Exigir MFA para acesso administrativo | MFA obrigatório para staff e para o console do provedor |
| 7.1 | Estabelecer e manter processo de gestão de vulnerabilidades | política com prazo por severidade |
| 7.2 | Estabelecer e manter processo de remediação | fila de correção; registro |
| 7.3 | Gestão automatizada de patches do sistema operacional | atualizações automáticas na VM; imagens base atualizadas |
| 7.4 | Gestão automatizada de patches de aplicações | Dependabot/Renovate; `audit` no CI |
| 8.1 | Estabelecer e manter processo de gestão de logs de auditoria | política de logs: o que, onde, quanto tempo |
| 8.2 | Coletar logs de auditoria | auditoria da aplicação; logs de acesso; logs do provedor |
| 8.3 | Garantir armazenamento adequado dos logs | retenção definida; espaço; centralização |
| 9.1 | Usar só navegadores e clientes de e-mail suportados | política de dispositivos |
| 9.2 | Usar serviços de filtragem de DNS | DNS com filtragem nos dispositivos (política) |
| 10.1 | Implantar e manter software anti-malware | endpoint da equipe; scan de upload no produto |
| 10.2 | Atualização automática de assinaturas | endpoint |
| 10.3 | Desativar autorun de mídia removível | política de dispositivos |
| 11.1 | Estabelecer e manter processo de recuperação de dados | runbook de restauração com RPO e RTO |
| 11.2 | Fazer backups automatizados | backup contínuo agendado |
| 11.3 | Proteger os dados de recuperação | backup cifrado com acesso restrito |
| 11.4 | Manter instância isolada dos dados de recuperação | repositório de backup separado (outro balde, outra conta ou outro provedor) |
| 12.1 | Manter a infraestrutura de rede atualizada | proxy e firewall atualizados; imagens |
| 14.1 | Estabelecer e manter programa de conscientização | `training.md` |
| 14.2 | Treinar para reconhecer engenharia social | trilha |
| 14.3 | Treinar boas práticas de autenticação | trilha |
| 14.4 | Treinar boas práticas de manuseio de dados | trilha (dado pessoal) |
| 14.5 | Treinar sobre causas de exposição não intencional | trilha |
| 14.6 | Treinar a reconhecer e reportar incidentes | trilha; canal de reporte |
| 14.7 | Treinar a identificar e reportar ativos sem atualização | trilha |
| 14.8 | Treinar sobre perigos de redes inseguras | trilha |
| 15.1 | Estabelecer e manter inventário de provedores de serviço | `vendors/` com todos os terceiros |
| 17.1 | Designar responsável pela resposta a incidentes | runbook: nome e substituto |
| 17.2 | Manter contatos para reporte de incidentes | runbook: ANPD, provedor, jurídico, encarregado |
| 17.3 | Estabelecer processo de reporte de incidentes | runbook; canal interno |

Controles 13 (monitoramento de rede), 16 (segurança de aplicações) e 18 (teste de invasão) não têm salvaguarda no IG1.

## IG2 que costuma tocar um SaaS

Não são exigidas no IG1, mas um produto que guarda dado pessoal de terceiros normalmente já as cumpre ou precisa delas. Inclua na matriz as que se aplicarem.

| Id | Salvaguarda | Evidência típica |
|---|---|---|
| 3.10 | Cifrar dados sensíveis em trânsito | TLS; HSTS |
| 3.11 | Cifrar dados sensíveis em repouso | cifra de volume ou por campo |
| 3.12 | Segmentar o processamento de dados por sensibilidade | isolamento por inquilino; segredos em namespace próprio |
| 3.14 | Registrar acesso a dados sensíveis | auditoria de exportação e de acesso administrativo |
| 4.8 | Desinstalar ou desativar serviços desnecessários | imagens mínimas; portas mínimas |
| 5.5 | Inventário de contas de serviço | chaves de API, tokens de integração, contas de deploy |
| 6.8 | Controle de acesso baseado em papéis | papéis e permissões |
| 7.5 / 7.6 | Varredura automatizada de vulnerabilidades (interna e externa) | scanner de imagem; SAST; scan externo |
| 8.5 | Coletar logs detalhados | requisição com id, ator e recurso |
| 8.9 | Centralizar logs | agregador de logs |
| 8.10 | Reter logs por ao menos 90 dias | retenção configurada |
| 8.11 | Revisar logs | rotina de revisão ou alertas |
| 13.1 | Centralizar alertas de eventos de segurança | Alertmanager ou equivalente |
| 15.2 a 15.4 | Política, classificação e contrato com provedores | `vendors/` com tier e DPA |
| 16.1 | Processo de desenvolvimento seguro | guia de engenharia; revisão |
| 16.2 | Processo para receber e tratar vulnerabilidades reportadas | `security.txt`; canal de reporte |
| 16.4 / 16.5 | Inventário e atualização de componentes de terceiros | lockfile; Dependabot |
| 16.8 | Separar produção de não produção | ambientes separados; dado sintético em teste |
| 16.11 | Usar módulos e bibliotecas confiáveis para funções de segurança | cripto da plataforma; nada "feito em casa" |
| 16.12 | Verificações de segurança no código | lint de segurança; testes de arquitetura |
| 17.4 a 17.9 | Plano de resposta, papéis, comunicação, exercício anual e pós-incidente | runbook; simulado; log |
| 18.1 a 18.3 | Programa de teste de invasão e correção | pentest periódico |
