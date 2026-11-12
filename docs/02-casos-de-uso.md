# Casos de uso
Os casos de uso que você vai descrever são: cadastrar-se, fazer login, ver o estado do jogo de hoje, enviar tentativa, ver ranking, ver histórico, descadastrar-se do e-mail e enviar o e-mail diário (este com o sistema como ator). Cada um segue o formato que o próprio template pede. Exemplo para o UC-01:

## UC-01 — Cadastrar
Ator: visitante
Pré-condição: não estar logado.
Fluxo principal: informa e-mail e senha; o sistema valida, cria a conta e confirma.
Fluxos alternativos: e-mail já cadastrado; senha fraca; e-mail inválido.
Pós-condição: conta criada, com senha em hash e e-mail criptografado.

## Casos de abuso
<!-- Pelo menos 3: como alguém tentaria trapacear ou atacar o sistema? -->
Usuario (visitante ou logado) pode tentar trapacear ou atacar o sistema ao tentar descobrir a proxima palavra inspecionando as respostas da API, automatizar tentativas com um script, tentar adivinhar senhas por força bruta, forjar uma requisição para alterar o próprio placar e descadastrar outra pessoa adivinhando o link.
