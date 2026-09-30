# Programa de conscientização e treinamento em segurança e proteção de dados

**Organização**: {razão social} | **Responsável**: {função} | **Versão**: v{N} | **Data**: {data}

Base: LGPD Art. 46 e 50; guia de segurança da ANPD (conscientização e treinamento); ISO/IEC 27001 Anexo A 6.3; CIS Controls v8, controle 14.

## Trilhas

### T1. Onboarding (antes do primeiro acesso à produção ou a dado pessoal)

Duração: {1 h}. Conduzida por: {função}.

| Tema | O que a pessoa sai sabendo | Fonte |
|---|---|---|
| A política | onde está, o que muda no dia a dia, onde reportar | política, seção 11 |
| Senhas e MFA | gerenciador de senhas, MFA em tudo, nunca reutilizar | CIS 14.3 |
| Phishing e engenharia social | como reconhecer, o que fazer, exemplos reais do setor | CIS 14.2 |
| Dado pessoal | o que é, o que é sensível, por onde pode circular e por onde não (chat, planilha, IA, log) | CIS 14.4, 14.5; guia ANPD |
| Dispositivos e redes | cifra, bloqueio, atualização, rede pública | CIS 14.8 |
| Incidente | o que conta como incidente, canal, prazo interno, "não apague nada" | CIS 14.6; Res. 15/2024 |
| Acesso | menor privilégio, não compartilhar conta, avisar quando não precisar mais | CIS 6 |

### T2. Quem desenvolve ou administra produção (além da T1)

| Tema | Conteúdo |
|---|---|
| Segredos | fora do código; rotação; o que fazer se vazou |
| Isolamento por inquilino e permissões | como o sistema garante; o que nunca contornar |
| Injeção, validação e SSRF | os padrões do projeto e os testes de arquitetura |
| Dependências | atualização, `audit`, o que fazer com uma vulnerabilidade |
| Dado real | nunca em teste ou máquina local; anonimização |
| Logs e rastreamento | sem dado pessoal; redação |
| Incidente técnico | contenção (revogar chave, derrubar sessão), preservação de evidência, quem chamar |

### T3. Reciclagem anual (todos)

Duração: {1 h}. Revisão da T1 com os incidentes e quase-incidentes do ano, mudanças na política e nas normas.

### T4. Simulado de phishing (se houver ferramenta)

{1 por ano}. Resultado agregado, sem exposição individual; quem cai refaz o módulo de phishing.

## Calendário

| Trilha | Quando | Registro |
|---|---|---|
| T1 | até {5 dias} da entrada, antes do acesso à produção | tabela abaixo |
| T2 | até {30 dias} da entrada, para as funções técnicas | tabela abaixo |
| T3 | {mês} de cada ano | tabela abaixo |
| T4 | {mês} de cada ano | relatório da ferramenta |

## Registro de participação

| Nome | Função | Trilha | Data | Conduzido por |
|---|---|---|---|---|
| | | | | |

## Indicadores

- Pessoas com T1 concluída antes do acesso à produção: {N}/{total}.
- Reciclagem do ano concluída: {N}/{total}.
- Incidentes reportados pela equipe no ano: {N} (um número maior que zero é sinal de que o canal funciona).
