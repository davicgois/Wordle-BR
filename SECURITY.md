# Política de segurança

Este é um projeto de portfólio (Wordle em português do Brasil), mantido por uma única pessoa. 
O sistema lida com contas de usuário, senhas e e-mails.

## Versões com suporte

Apenas a versão mais recente da branch `main` recebe correções de segurança.

## Como reportar uma vulnerabilidade

**Não abra uma issue pública** para relatar uma falha de segurança.

Use um destes canais:

1. **Relato privado pelo GitHub (preferido):** aba **Security** do repositório → **Report a vulnerability**.
2. **E-mail:** `goissoaresdavi@gmail.com` (assunto: `[SECURITY] wordle-ptbr`).

Se possível, inclua:

- descrição do problema e o impacto que você enxerga;
- passos para reproduzir, ou uma prova de conceito mínima;
- commit ou versão afetada e, se aplicável, a URL;
- sugestão de correção, se tiver.

## O que esperar

- Confirmação de recebimento em até **7 dias corridos**.
- Avaliação e, se confirmada a falha, correção o mais rápido possível, com aviso quando for publicada.
- Crédito pela descoberta, se você quiser.

O projeto é mantido em regime de melhor esforço: não há SLA formal nem programa de recompensa financeira.

## Escopo

**Dentro do escopo:**

- o código deste repositório;
- a API e o front-end publicados;
- a configuração de CI/CD e de deploy versionada aqui.

**Fora do escopo:**

- serviços de terceiros (hospedagem, banco de dados gerenciado, provedor de e-mail): reporte diretamente a eles;
- engenharia social e ataques físicos;
- ataques de negação de serviço (DoS/DDoS).

## Boas práticas para quem pesquisa

- Não acesse, altere ou apague dados de outras pessoas. Teste só com contas criadas por você.
- Não execute testes automatizados agressivos (força bruta, flood) contra o ambiente de produção.
- Conceda um prazo razoável para a correção antes de divulgar publicamente.

## Segredos no repositório

Este repositório **não deve conter segredos** (chaves, tokens, senhas, dados de usuários). Se você encontrar algum no código ou no histórico, reporte pelos canais acima: isso conta como vulnerabilidade.
