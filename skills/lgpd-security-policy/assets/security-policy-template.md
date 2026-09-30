# Política de Segurança da Informação

**Organização**: {razão social} | **CNPJ**: {nº}
**Versão**: v{N} | **Aprovada por**: {nome, cargo} em {data} | **Próxima revisão**: {data + 12 meses}
**Responsável pela segurança da informação**: {função} | **Encarregado (LGPD)**: {nome, contato} (ver `.lgpd/encarregado.md`)

> Rascunho gerado por `lgpd-security-policy`. Só vale depois de aprovado, comunicado e aplicado. Campos `{decisão}` precisam de escolha da direção.

## 1. Objetivo e escopo

Esta política define as regras de segurança da informação da {organização}, para proteger os dados que ela trata, em especial os dados pessoais dos seus clientes e dos clientes deles (LGPD, Art. 46). Vale para todas as pessoas com acesso aos sistemas da organização: sócios, empregados, prestadores e estagiários, em qualquer local de trabalho, e para todos os ativos: código, sistemas, contas de terceiros, dispositivos e documentos.

## 2. Papéis e responsabilidades

| Papel | Responsabilidade |
|---|---|
| Direção | aprova esta política, garante recursos, decide sobre incidentes graves |
| Responsável pela segurança ({função}) | mantém a política, o inventário de ativos e acessos, a gestão de vulnerabilidades e o plano de incidentes |
| Encarregado (LGPD) | canal com titulares e ANPD; orienta a equipe; participa da decisão de comunicar incidentes (Res. CD/ANPD 18/2024) |
| Quem administra a produção | aplica os controles técnicos; registra mudanças; guarda evidências |
| Todos | seguem esta política, protegem suas credenciais e reportam incidentes |

## 3. Classificação da informação

| Classe | Exemplos | Regra |
|---|---|---|
| Pública | site, documentação pública | sem restrição |
| Interna | código, roadmap, métricas agregadas | só pessoas da organização; repositório privado |
| Confidencial | contratos, segredos de produção, financeiro | acesso nominal e registrado; cifrado em repouso |
| Dado pessoal | nome, e-mail, telefone, mensagens dos clientes e dos clientes deles | só pelos sistemas e caminhos previstos; nunca em chat, planilha solta, log ou ferramenta não aprovada; retenção definida |
| Dado pessoal sensível | saúde, biometria, origem racial ou étnica, religião, opinião política, vida sexual | só com base legal do Art. 11; cifra por campo, acesso nominal e registrado |
| Dado de criança ou adolescente | dado pessoal de pessoa com menos de 18 anos | todo tratamento observa o melhor interesse (Art. 14); documente a base legal aplicável (Art. 7º ou 11) e as regras do ECA Digital quando o produto for voltado a menores |

## 4. Uso aceitável

- **Contas**: uma conta por pessoa, em todo sistema. Conta compartilhada é proibida.
- **Senhas**: únicas por sistema, guardadas em gerenciador de senhas {decisão: obrigatório ou recomendado}. Mínimo de {12} caracteres. Nunca em chat, e-mail, código ou arquivo.
- **MFA**: obrigatório no repositório de código, no provedor de nuvem, no e-mail corporativo e em toda conta administrativa do produto.
- **E-mail, chat e ferramentas**: só as ferramentas aprovadas ({lista}). Dado pessoal de cliente não circula em chat nem em ferramenta de IA generativa fora das aprovadas.
- **IA generativa**: {decisão: quais ferramentas, com que dados}. Código e dado de cliente só em ferramenta com contrato que proíba treinamento com os dados.
- **Software**: só o necessário, de fonte oficial, atualizado.

## 5. Controle de acesso

- Acesso é concedido no menor privilégio necessário, por função, e registrado ({onde}).
- Acesso administrativo à produção (servidor, banco, provedor, backoffice) é separado do uso do dia a dia e exige MFA.
- Revisão de todos os acessos a cada {decisão: 3 ou 6} meses, com registro.
- Na saída ou na mudança de função, todos os acessos são revogados no mesmo dia: contas, chaves, sessões, dispositivos. Checklist de offboarding em {onde}.
- Sessões expiram por inatividade; dispositivos bloqueiam em {5} minutos.

## 6. Dispositivos e trabalho remoto

- Todo dispositivo que acessa código ou produção tem disco cifrado, bloqueio de tela, atualização automática e antimalware ativo.
- Dispositivo pessoal: {decisão: proibido para produção / permitido com os mesmos requisitos}.
- Perda ou roubo é incidente: reporte imediato (seção 11).
- Rede pública só com VPN {decisão} ou sem acesso à produção.

## 7. Desenvolvimento e operação

- Segredos ficam fora do código, em variáveis de ambiente ou cofre; nunca no repositório, no histórico ou em imagem. Validação de ambiente recusa configuração insegura em produção.
- Toda mudança em produção passa por PR revisado e pelo CI; migrations versionadas; nada instalado à mão no servidor.
- Ambientes separados: desenvolvimento, teste e produção. Dado real não sai da produção; teste usa dado sintético.
- Dependências atualizadas por rotina ({Dependabot/Renovate}); vulnerabilidade conhecida corrigida em {7} dias (crítica ou alta) ou {30} dias (média).
- Log e rastreamento não guardam dado pessoal; o que precisa ficar é redigido.

## 8. Dados pessoais

- Coleta mínima para a finalidade; retenção definida por categoria (`.lgpd/retention.md`); exclusão e exportação só pelos caminhos do sistema, que registram quem pediu.
- Exportação em massa, acesso administrativo a conta de cliente e mudança de permissão são registrados em auditoria imutável.
- Como operador dos dados dos clientes dos nossos clientes, seguimos as instruções do contrato (`lgpd-operator`) e não usamos esses dados para fins próprios.
- Sigilo sobre dado pessoal continua depois do fim do vínculo (LGPD, Art. 47).

## 9. Backup e continuidade

- Backup {contínuo/diário} do banco e dos arquivos, cifrado, guardado em local separado do ambiente principal, com retenção de {35 dias e 12 meses}.
- Prova de restauração {semanal/mensal}, registrada. RPO de {x}; RTO de {y}. Runbook em {onde}.

## 10. Terceiros

- Fornecedor com acesso a dado pessoal só com contrato de operador ou suboperador (`lgpd-dpa`) e avaliação (`lgpd-vendor-audit`). Lista em `.lgpd/vendors/`.
- Transferência internacional só com base do Art. 33 e cláusulas-padrão (Res. CD/ANPD 19/2024).

## 11. Incidentes

- Incidente é qualquer acesso, perda, alteração ou vazamento indevido de informação, suspeito ou confirmado, inclusive dispositivo perdido, credencial exposta e phishing bem-sucedido.
- Quem perceber reporta em até {1 hora} por {canal}. Não apague nada; não tente resolver sozinho.
- O responsável pela segurança e o encarregado decidem, com registro escrito, se o incidente é comunicável à ANPD e aos titulares (Res. CD/ANPD 15/2024, Art. 5º). Prazo: 3 dias úteis do conhecimento ({6 dias úteis se ATPP}). Runbook em `.lgpd/incidents/runbook.md`; registro por 5 anos em `.lgpd/incidents/log.md`.
- Como operador, avisamos o controlador afetado em até {24 horas}.

## 12. Descumprimento

Descumprir esta política sujeita a medidas proporcionais, de orientação a desligamento, conforme o contrato e a lei, sem prejuízo da responsabilidade civil.

## 13. Revisão

Revisada a cada 12 meses e sempre que houver incidente relevante, mudança de arquitetura, novo suboperador ou norma nova. Toda versão fica registrada abaixo.

## Histórico

| Versão | Data | Mudança | Aprovada por |
|---|---|---|---|
| v1.0 | {data} | primeira versão | {nome} |

## Registro de leitura

| Nome | Função | Data |
|---|---|---|
| | | |
