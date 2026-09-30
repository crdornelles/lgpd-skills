# Acordo de Tratamento de Dados Pessoais — {Produto} como Operador

> Anexo ao Contrato Principal / Termos de Uso de {Produto}. Rascunho gerado por `lgpd-operator`; não é peça jurídica pronta. Campos `{…}` precisam de decisão; o documento inteiro precisa de revisão jurídica antes de ir para o cliente.

**OPERADOR**: {razão social do produto}, CNPJ {nº}, com sede em {endereço} ("{Produto}").
**CONTROLADOR**: a pessoa jurídica que contrata {Produto} ("Cliente"), identificada no Contrato Principal.
**Encarregado do Operador**: {nome}, {e-mail} (ver `.lgpd/encarregado.md`).

## 1. Papéis

O Cliente é o **controlador** dos dados pessoais que insere, importa ou recebe em {Produto} (dados dos seus contatos, clientes, leads e equipe), e decide as finalidades e os meios do tratamento. {Produto} é o **operador**, e trata esses dados apenas conforme este Acordo e as instruções do Cliente (LGPD, Art. 5º, VI e VII; Art. 39).

{Produto} é **controlador** dos dados da conta do Cliente (cadastro, autenticação, cobrança, uso do serviço), tratados conforme a Política de Privacidade de {Produto}, e não deste Acordo.

## 2. Objeto

| Campo | Conteúdo |
|---|---|
| Finalidade | prestar o serviço descrito no Contrato Principal: {CRM, atendimento, automação, cobrança…} |
| Categorias de titulares | contatos, clientes e leads do Cliente; equipe do Cliente |
| Categorias de dados | identificação (nome, e-mail, telefone, documento), conversas e mensagens, histórico comercial, {outros} |
| Dados sensíveis (Art. 11) | {não previstos / previstos: quais}. O Cliente não deve inserir dado sensível sem base legal própria |
| Dados de crianças e adolescentes | {não previstos}. O Cliente responde pela base do Art. 14 |
| Duração | enquanto vigorar o Contrato Principal, mais o prazo de devolução e eliminação da cláusula 9 |

## 3. Instruções do Controlador

As instruções do Cliente são: (a) este Acordo; (b) as funções que {Produto} oferece pela interface e pela API, conforme a documentação; (c) as configurações que o Cliente escolhe (retenção, integrações, agentes de IA, {outras}); (d) instruções escritas adicionais aceitas por {Produto}.

{Produto} não trata os dados do Cliente para fins próprios, inclusive marketing, perfilamento ou treinamento de modelos, salvo de forma anonimizada e agregada para operar e melhorar o serviço (ISO/IEC 27701:2025, A.2.2.3 e A.2.2.4).

Se {Produto} entender que uma instrução viola a LGPD, avisa o Cliente e pode suspender aquela instrução (ISO/IEC 27701:2025, A.2.2.5).

## 4. Confidencialidade

{Produto} garante que as pessoas com acesso aos dados do Cliente estão sujeitas a dever de sigilo, limitadas ao necessário para a função, treinadas em proteção de dados, e que o sigilo sobrevive ao fim do vínculo (LGPD, Art. 47).

## 5. Segurança

{Produto} adota as medidas técnicas e administrativas listadas como implementadas e evidenciadas no Anexo I (LGPD, Art. 46). {Ao preencher o Anexo I, inclua apenas controles cuja implementação foi confirmada na matriz de `lgpd-security-baseline`, por exemplo: cifra em trânsito e em repouso, controle de acesso com autenticação forte, isolamento entre contas, registro de auditoria, backup cifrado com prova de restauração, gestão de vulnerabilidades e plano de resposta a incidentes. Controle `em parte` ou `não cumpre` não entra no Anexo I.} A matriz de aderência aos padrões de referência (guia de segurança da ANPD, ISO/IEC 27001 e 27701, CIS Controls) fica disponível ao Cliente mediante pedido.

## 6. Suboperadores

O Cliente autoriza, de forma **geral**, que {Produto} contrate suboperadores para prestar o serviço, listados em {URL pública da lista} (Anexo II), com país, finalidade e dado tratado.

{Produto} avisa o Cliente com **{30} dias** de antecedência sobre inclusão ou troca de suboperador, por {e-mail ao administrador da conta e aviso no painel}. O Cliente pode se opor por escrito nesse prazo; se a objeção não puder ser atendida, o Cliente pode rescindir o Contrato Principal sem multa quanto ao serviço afetado.

{Produto} impõe a cada suboperador obrigações equivalentes às deste Acordo e responde perante o Cliente pelos atos deles (LGPD, Art. 42, § 1º).

## 7. Direitos dos titulares

{Produto} oferece ao Cliente as ferramentas para atender os direitos do Art. 18 nos dados que guarda: confirmação, acesso e exportação, correção, anonimização e exclusão, {revisão de decisão automatizada}, conforme o Anexo III.

Pedido de titular recebido diretamente por {Produto}, referente a dados do Cliente, é encaminhado ao Cliente em até **{2 dias úteis}**, sem resposta ao titular além da orientação de procurar o controlador, salvo instrução diversa do Cliente. {Se houver: {Produto} disponibiliza uma página pública de pedido do titular por conta, em {URL}, que o Cliente pode divulgar na sua política.}

O Cliente responde pelo prazo legal de resposta ao titular (LGPD, Art. 19).

## 8. Incidentes de segurança

{Produto} comunica ao Cliente, por {canal}, em até **{24 horas}** do conhecimento, todo incidente de segurança que possa afetar dados do Cliente, com: descrição e causa provável, categorias de dados e de titulares afetados, medidas tomadas e recomendadas, contato do encarregado e as informações que forem sendo apuradas. O prazo permite ao Cliente cumprir a comunicação à ANPD e aos titulares em 3 dias úteis (LGPD, Art. 48; Res. CD/ANPD 15/2024, Art. 6º e 9º).

{Produto} mantém registro dos incidentes por no mínimo 5 anos (Res. CD/ANPD 15/2024, Art. 10) e colabora com o Cliente na apuração e na comunicação.

## 9. Devolução e eliminação

No encerramento do Contrato Principal, o Cliente pode exportar todos os seus dados em formato estruturado ({CSV/JSON/ZIP}) por **{30} dias**. Após esse prazo, {Produto} elimina os dados do Cliente em até **{30} dias**, salvo o que precisar guardar por obrigação legal (LGPD, Art. 16, I), e entrega, mediante pedido, declaração de eliminação. Cópias de backup expiram pelo ciclo de retenção do backup, de até **{35 dias / 12 meses}**, e não são restauradas para uso.

## 10. Auditoria

{Produto} disponibiliza ao Cliente, mediante pedido e sob sigilo: a matriz de aderência a padrões de segurança, o registro de operações como operador, relatórios de auditoria ou certificações que possuir (ISO/IEC 27001, 27701, SOC 2), e resposta a questionário de segurança em até **{15} dias úteis**. Auditoria presencial ou por terceiro é possível uma vez por ano, com **{30} dias** de aviso, em horário comercial, às custas do Cliente, sem acesso a dados de outros clientes.

## 11. Responsabilidade

Cada parte responde pelos danos que causar nos termos dos Art. 42 a 45 da LGPD. {Produto} responde solidariamente quando descumprir a lei ou as instruções lícitas do Cliente (Art. 42, § 1º, I). Os limites de responsabilidade do Contrato Principal aplicam-se, exceto {dolo, culpa grave e violação de sigilo}.

## 12. Transferência internacional

Suboperadores fora do Brasil estão indicados no Anexo II com o país e a base do Art. 33 (cláusulas-padrão da Res. CD/ANPD 19/2024, ou outra hipótese). {Produto} mantém as cláusulas assinadas e as apresenta ao Cliente mediante pedido.

## 13. Responsabilidades do Controlador

O Cliente garante que: tem base legal para os dados que insere em {Produto} (Art. 7º e 11); informou os titulares (Art. 9º); obteve consentimento quando exigido, inclusive para mensagens de marketing; não insere dados de que não precisa; configura o serviço (retenção, integrações, agentes) conforme as próprias obrigações; e atende os titulares no prazo legal (ISO/IEC 27701:2025, A.2.2.6).

## 14. Pedidos de autoridades

Se {Produto} receber ordem de autoridade pública ou judicial por dados do Cliente, comunica o Cliente antes de atender, salvo proibição legal, e limita a entrega ao exigido (ISO/IEC 27701:2025, A.2.5.5 e A.2.5.6).

## 15. Vigência e alterações

Este Acordo vigora com o Contrato Principal. Alterações são comunicadas com **{30} dias** de antecedência; a versão vigente e o histórico ficam em {URL}.

---

## Anexo I — Medidas técnicas e administrativas

{Resumo da matriz do `lgpd-security-baseline`: autenticação e MFA, permissões, isolamento entre contas, cifra, backup e restauração, auditoria, vulnerabilidades, incidentes, treinamento. Uma linha por medida, com a situação.}

## Anexo II — Suboperadores

Ver `.lgpd/operator/subprocessors.md` (lista pública em {URL}).

## Anexo III — Ferramentas para os direitos dos titulares

| Direito (Art. 18) | Como o Cliente atende em {Produto} |
|---|---|
| Confirmação e acesso | {busca do contato; exportação em ZIP pela tela X} |
| Correção | {edição da ficha} |
| Anonimização, bloqueio ou eliminação | {anonimizar ou excluir contato, com supressão} |
| Portabilidade | {exportação em formato estruturado} |
| Informação sobre compartilhamento | {lista de integrações da conta; esta lista de suboperadores} |
| Revogação do consentimento | {opt-out por mensagem; marcação na ficha} |
| Revisão de decisão automatizada (Art. 20) | {revisão por pessoa das ações do agente de IA} |

---

**Assinaturas**

{Produto}: ______________________ Data: ____
Cliente: ______________________ Data: ____
