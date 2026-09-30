# Suboperadores de {Produto}

**Versão**: v{N} | **Data**: {data} | **Publicada em**: {URL} | **Aviso de mudança**: {30} dias antes, por {canal}
**Encarregado**: {nome, e-mail}

Suboperador é o terceiro que {Produto} contrata para prestar o serviço e que, para isso, recebe dados pessoais de que {Produto} é operador (dados dos clientes dos nossos clientes). Fornecedor que só recebe dados da conta (cobrança, cadastro) é operador de {Produto} como controlador e aparece na Política de Privacidade, não aqui, salvo quando também toca dados do cliente.

## Lista

| Suboperador | Finalidade | Dados que recebe | País | Base do Art. 33 | Contrato | Certificações | Ficha |
|---|---|---|---|---|---|---|---|
| {Hospedagem} | infraestrutura, banco, armazenamento, backup | todos os dados da conta | {Brasil / país} | {não se aplica / cláusulas-padrão Res. 19/2024} | {DPA assinado em} | {ISO 27001, SOC 2} | `.lgpd/vendors/{slug}.md` |
| {Provedor de mensageria} | envio e recebimento de mensagens | telefone, nome, conteúdo das mensagens | | | | | |
| {Provedor de IA} | respostas e resumos do agente | conteúdo das conversas, nome; {CPF mascarado} | | | | | |
| {E-mail transacional} | e-mails do sistema | e-mail, nome | | | | | |
| {Cobrança} | só se tocar dado do cliente do cliente | | | | | | |
| {Backup fora do ambiente} | cópia de segurança | todos os dados, cifrados | | | | | |

## O que cada suboperador não recebe

{Ex.: o provedor de IA não recebe CPF nem documentos anexados; o provedor de e-mail não recebe conteúdo de conversa; o backup é cifrado antes de sair e o provedor não tem a chave.}

## Histórico

| Versão | Data | Mudança | Aviso enviado em |
|---|---|---|---|
| v1.0 | {data} | lista inicial | {data} |
