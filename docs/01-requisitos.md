# Requisitos

## Visão geral do produto
Uma versão do Wordle com palavras do português brasileiro, com conta, placar e aviso diário por e-mail.

## Atores
Visitante (sem login), jogador (logado) e sistema/agendador (quem dispara o e-mail)

## Escopo
Cadastro, login, palavra do dia, 6 tentativas, ranking, histórico, e-mail diário, descadastro e deploy.


### Dentro do escopo
### Fora do escopo

## Requisitos funcionais
RF-04 Enviar tentativa
O jogador logado envia uma palavra de 5 letras e recebe o status de cada letra.
Critério: a resposta traz 5 itens (correta, presente ou ausente), o número da tentativa e o estado da partida.

## Requisitos não funcionais
segurança (senha com hash, e-mail criptografado), LGPD, desempenho (por exemplo, resposta de tentativa abaixo de 500 ms), disponibilidade e usabilidade.

## Restrições e premissas
projeto solo, planos gratuitos de hospedagem e Python como linguagem principal.
