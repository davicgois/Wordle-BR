# Requisitos

## Visão geral do produto
O Wordle BR é um jogo de palavras diário, inspirado no Wordle, desenvolvido para o público brasileiro e baseado no vocabulário da língua portuguesa utilizada no Brasil.
O jogador deve descobrir uma palavra secreta do dia em até seis tentativas, recebendo dicas visuais sobre as letras corretas e suas posições.
A plataforma permite criar contas, acompanhar partidas anteriores, consultar estatísticas e competir em rankings com outros jogadores.
O sistema também oferece notificações por e-mail para lembrar os usuários de jogar diariamente, mediante consentimento.
Seu objetivo é proporcionar uma experiência simples, acessível e competitiva de entretenimento linguístico em português brasileiro.

## Atores
Visitante: pessoa que acessa o jogo sem possuir uma conta ou sem estar autenticada.

Jogador cadastrado: usuário que possui uma conta e pode jogar, acompanhar estatísticas e consultar seu histórico.

Administrador: responsável por gerenciar palavras, revisar conteúdo e acompanhar o funcionamento da plataforma.

Serviço de e-mail: sistema externo responsável por enviar mensagens de notificação aos jogadores que autorizaram o recebimento.

Agendador de tarefas: processo automatizado que identifica o início de um novo dia de jogo e dispara a rotina de envio dos e-mails.

Serviço de autenticação: responsável por validar as credenciais e controlar o acesso às funcionalidades protegidas.

Serviço de armazenamento: responsável por persistir contas, partidas, tentativas, palavras e preferências dos usuários.

## Escopo
### Dentro do escopo
3.1. Dentro do escopo
O projeto contempla:
1. Cadastro de usuários com informações básicas.
2. Login e logout de usuários.
3. Recuperação de senha.
4. Palavra secreta diária em português brasileiro.
5. Partidas com limite de seis tentativas.
6. Validação de palavras enviadas pelo jogador.
7. Feedback visual individual para cada letra.
8. Registro dos resultados das partidas.
9. Placar individual com estatísticas de desempenho.
10. Histórico de partidas anteriores.
11. Ranking de jogadores.
12. Envio de e-mail diário para usuários que consentiram com as notificações.
13. Descadastro das notificações por e-mail.
14. Gerenciamento dos dados pessoais e exclusão de contas.
15. Interface responsiva para computadores e dispositivos móveis.

### Fora do escopo
Para manter o projeto controlado e evitar funcionalidades que aumentem desnecessariamente sua complexidade, ficam excluídos:
1. Aplicativo nativo para Android ou iOS.
2. Modo multiplayer em tempo real.
3. Partidas privadas ou desafios entre amigos.
4. Criação de palavras personalizadas pelos jogadores.
5. Compra de dicas, moedas, vidas ou qualquer recurso pago.
6. Sistema de assinaturas ou monetização.
7. Integração com redes sociais para compartilhamento automático.
8. Chat, mensagens privadas ou interação social entre jogadores.
9. Suporte a outros idiomas além do português brasileiro.
10. Modos de jogo alternativos, como palavras de tamanhos diferentes.
11. Animações ou telas de carregamento artificiais utilizadas apenas para simular processamento, atrasar a interação ou mascarar a ausência de conteúdo.
12. Funcionalidades de inteligência artificial para gerar palavras ou validar respostas em tempo real.
13. Aplicação de penalidades ou bloqueios competitivos por comportamento dos jogadores.

Decisão sobre carregamento: as telas de carregamento só serão exibidas quando houver uma operação real que justifique a espera. Não serão adicionados delays artificiais, spinners sem necessidade ou transições que impeçam o jogador de interagir quando os dados já estiverem disponíveis.

## Requisitos funcionais
Os requisitos funcionais descrevem as ações que o sistema deve executar. Cada requisito possui um comportamento específico e um critério de aceitação verificável.
4.1. Cadastro e autenticação
RF-01 — Cadastro de usuário. O sistema deve permitir que um visitante crie uma conta informando nome, e-mail e senha.

Critério de aceitação: ao enviar dados válidos, a conta é criada e o usuário recebe confirmação. E-mails já cadastrados não podem gerar contas duplicadas.

RF-02 — Login. O sistema deve permitir que um usuário cadastrado acesse sua conta utilizando e-mail e senha.

Critério de aceitação: credenciais válidas permitem o acesso; credenciais inválidas retornam uma mensagem de erro sem revelar qual informação está incorreta.

RF-03 — Logout. O sistema deve permitir que um usuário encerre sua sessão autenticada.

Critério de aceitação: após o logout, qualquer tentativa de acessar uma funcionalidade protegida deve exigir nova autenticação.

RF-04 — Recuperação de senha. O sistema deve permitir que um usuário solicite a redefinição de sua senha por e-mail.

Critério de aceitação: o sistema envia um link temporário de redefinição para o endereço informado, sem revelar se existe uma conta associada a ele.
4.2. Mecânica do jogo
RF-05 — Disponibilização da palavra do dia. O sistema deve disponibilizar uma palavra secreta por dia para todos os jogadores.

Critério de aceitação: todos os jogadores recebem a mesma palavra durante o mesmo dia, considerando a data oficial de referência do jogo.

RF-06 — Início de partida. O sistema deve permitir que um jogador autenticado inicie a partida diária.

Critério de aceitação: ao acessar o jogo, o jogador visualiza o tabuleiro correspondente à palavra do dia e suas seis linhas de tentativa.

RF-07 — Limite de tentativas. O sistema deve permitir no máximo seis tentativas por jogador para cada palavra diária.

Critério de aceitação: após seis tentativas sem acerto, a partida é encerrada e nenhuma nova tentativa é aceita para aquela palavra.

RF-08 — Envio de tentativa. O sistema deve receber uma palavra informada pelo jogador como tentativa de resposta.

Critério de aceitação: o sistema aceita somente palavras que atendam ao tamanho exigido pela palavra do dia e à validação do vocabulário permitido.

RF-09 — Validação de palavras. O sistema deve verificar se a palavra enviada pertence ao vocabulário aceito pelo jogo.

Critério de aceitação: palavras inexistentes ou não permitidas são rejeitadas sem consumir uma tentativa.

RF-10 — Feedback por letra. O sistema deve informar a situação de cada letra da tentativa em relação à palavra secreta.

Critério de aceitação: cada letra recebe uma das três classificações:
- Verde: letra correta na posição correta.
- Amarelo: letra presente na palavra, mas em outra posição.
- Cinza: letra ausente da palavra.
RF-11 — Tratamento de letras repetidas. O sistema deve contabilizar corretamente letras repetidas durante a comparação entre a tentativa e a palavra secreta.

Critério de aceitação: uma letra não pode ser classificada como presente mais vezes do que sua quantidade na palavra secreta, respeitando a prioridade das posições corretas.

RF-12 — Encerramento por acerto. O sistema deve encerrar a partida quando o jogador descobrir a palavra secreta.

Critério de aceitação: ao acertar a palavra, o sistema apresenta o resultado de vitória e impede o envio de novas tentativas naquela partida.

RF-13 — Encerramento por esgotamento. O sistema deve encerrar a partida quando o jogador utilizar as seis tentativas sem descobrir a palavra.

Critério de aceitação: após a sexta tentativa incorreta, o sistema apresenta a palavra correta e registra a derrota.

RF-14 — Persistência de partida. O sistema deve salvar o estado da partida após cada tentativa válida.

Critério de aceitação: ao atualizar ou reabrir a página, o jogador visualiza as tentativas anteriores e o estado atualizado da partida.
4.3. Placar, histórico e ranking
RF-15 — Placar individual. O sistema deve apresentar estatísticas gerais de desempenho do jogador.

Critério de aceitação: o placar apresenta, no mínimo, quantidade de partidas jogadas, vitórias, derrotas, percentual de vitórias e sequência atual de vitórias.

RF-16 — Histórico de partidas. O sistema deve permitir que o jogador consulte suas partidas anteriores.

Critério de aceitação: cada registro apresenta a data da partida, resultado e quantidade de tentativas utilizadas.

RF-17 — Ranking de jogadores. O sistema deve disponibilizar uma classificação dos jogadores com base em seus resultados.

Critério de aceitação: o ranking apresenta os jogadores ordenados conforme os critérios de pontuação definidos pelo produto, exibindo suas posições e pontuações.

RF-18 — Atualização do ranking. O sistema deve atualizar a classificação após o registro de uma partida concluída.

Critério de aceitação: uma partida concluída altera a pontuação correspondente e a classificação reflete o resultado atualizado.
4.4. Comunicação por e-mail
RF-19 — Consentimento para notificações. O sistema deve permitir que o usuário escolha se deseja receber notificações diárias por e-mail.

Critério de aceitação: a preferência deve ser registrada e consultável na conta do usuário, sendo desativada por padrão até que haja consentimento.

RF-20 — Envio de e-mail diário. O sistema deve enviar um e-mail diário aos usuários que autorizaram o recebimento de notificações.

Critério de aceitação: o agendador identifica os usuários com consentimento ativo e solicita o envio de uma notificação por dia, sem duplicar o envio para o mesmo usuário e data.

RF-21 — Descadastro de notificações. O sistema deve permitir que o usuário interrompa o recebimento de e-mails diários.

Critério de aceitação: ao utilizar o link de descadastro ou desativar a preferência na conta, o usuário deixa de integrar os próximos envios programados.
4.5. Proteção e gerenciamento de dados
RF-22 — Consulta de dados pessoais. O sistema deve permitir que o usuário consulte os dados pessoais armazenados em sua conta.

Critério de aceitação: o usuário autenticado consegue visualizar suas informações cadastrais e preferências de comunicação.

RF-23 — Atualização de dados pessoais. O sistema deve permitir que o usuário atualize suas informações cadastrais.

Critério de aceitação: alterações válidas são persistidas e passam a ser exibidas nas próximas consultas.

RF-24 — Exclusão de conta. O sistema deve permitir que o usuário solicite a exclusão de sua conta e dos dados pessoais associados.

Critério de aceitação: após a confirmação da solicitação, os dados pessoais são excluídos ou anonimizados, respeitando obrigações legais de retenção, e o usuário perde o acesso à conta.

RF-25 — Registro de consentimento. O sistema deve registrar o consentimento do usuário para o tratamento de dados que dependa dessa autorização.

Critério de aceitação: o registro contém a finalidade, a data e a situação do consentimento, permitindo sua consulta e revogação quando aplicável.

RF-26 — Restrição de acesso a dados. O sistema deve impedir que um usuário consulte ou altere informações privadas pertencentes a outro usuário.

Critério de aceitação: uma requisição autenticada que tente acessar dados privados de outra conta recebe resposta de acesso negado.

## Requisitos não funcionais
Os requisitos não funcionais estabelecem critérios mensuráveis de qualidade, segurança, desempenho e conformidade.
5.1. Desempenho
RNF-01 — Tempo de resposta da API. As operações comuns de leitura e gravação da API devem responder em até 500 ms em 95% das requisições, desconsiderando serviços externos.

Critério de aceitação: testes de carga devem demonstrar que pelo menos 95% das requisições atendem ao limite estabelecido.

RNF-02 — Carregamento da interface. As telas principais do jogo devem apresentar seu conteúdo utilizável em até 2,5 segundos em uma conexão de banda larga, considerando um ambiente de teste definido.

Critério de aceitação: testes de desempenho devem registrar LCP de até 2,5 segundos no percentil 75.

RNF-03 — Processamento de tentativas. O processamento de uma tentativa deve retornar o feedback correspondente em até 500 ms em 95% das operações, excluindo latência de rede externa.

Critério de aceitação: testes automatizados e de carga devem confirmar o limite estabelecido.
5.2. Segurança
RNF-04 — Proteção de senhas. As senhas dos usuários devem ser armazenadas utilizando algoritmo seguro de hash com salt individual.

Critério de aceitação: nenhuma senha deve ser armazenada em texto puro ou recuperável diretamente do banco de dados.

RNF-05 — Comunicação segura. Toda comunicação entre cliente e servidor deve utilizar HTTPS.

Critério de aceitação: requisições HTTP devem ser redirecionadas para HTTPS ou rejeitadas.

RNF-06 — Autorização. As funcionalidades que envolvem dados privados ou ações de jogador devem exigir autenticação e autorização adequadas.

Critério de aceitação: requisições sem credenciais válidas recebem resposta 401, e usuários sem permissão recebem resposta 403.

RNF-07 — Proteção contra tentativas automatizadas. O sistema deve limitar requisições excessivas de autenticação e envio de tentativas.

Critério de aceitação: ao ultrapassar o limite configurado, novas requisições são temporariamente bloqueadas ou recebem resposta 429.

RNF-08 — Proteção da palavra secreta. A palavra do dia não deve ser exposta nas respostas públicas da aplicação antes do encerramento da partida ou do dia de jogo.

Critério de aceitação: inspeções das respostas da API e dos recursos entregues ao navegador não devem revelar a palavra secreta antecipadamente.
5.3. LGPD e privacidade
RNF-09 — Consentimento informado. O sistema deve apresentar informações claras sobre a finalidade do tratamento dos dados pessoais e solicitar consentimento quando essa for a base legal aplicável.

Critério de aceitação: o usuário consegue identificar quais dados são coletados, por que são utilizados e quais comunicações dependem de consentimento.

RNF-10 — Minimização de dados. O sistema deve coletar somente os dados pessoais necessários para as funcionalidades disponibilizadas.

Critério de aceitação: o cadastro e os demais formulários não devem solicitar informações sem finalidade documentada.

RNF-11 — Revogação de consentimento. O usuário deve conseguir revogar seu consentimento para comunicações por e-mail de maneira simples e gratuita.

Critério de aceitação: a revogação interrompe os próximos envios e não exige contato com um administrador.

RNF-12 — Exclusão de dados pessoais. O sistema deve disponibilizar um procedimento para exclusão dos dados pessoais do titular, observadas as hipóteses legais de conservação.

Critério de aceitação: após a solicitação confirmada, os dados elegíveis são excluídos ou anonimizados dentro do prazo operacional definido, com exceções de retenção devidamente justificadas.

RNF-13 — Transparência e direitos do titular. O sistema deve disponibilizar informações sobre o tratamento de dados e um canal para solicitações relacionadas aos direitos previstos na LGPD.

Critério de aceitação: o usuário encontra informações de privacidade e consegue encaminhar uma solicitação de acesso, correção ou exclusão.

RNF-14 — Retenção de dados. O sistema deve manter dados pessoais somente pelo período necessário às finalidades do tratamento ou pelo prazo exigido por obrigação legal.

Critério de aceitação: deve existir uma política documentada de retenção e descarte dos dados.
5.4. Disponibilidade e confiabilidade
RNF-15 — Disponibilidade. O sistema deve buscar disponibilidade mensal mínima de 99%, desconsiderando manutenções programadas previamente comunicadas.

Critério de aceitação: o monitoramento mensal deve demonstrar disponibilidade igual ou superior ao percentual definido.

RNF-16 — Integridade das partidas. O sistema deve preservar a consistência dos resultados e das tentativas registradas.

Critério de aceitação: uma tentativa válida não pode ser contabilizada duas vezes em razão de reenvio ou falha de comunicação.

RNF-17 — Consistência da palavra diária. A mudança da palavra do dia deve ocorrer de maneira consistente para todos os jogadores.

Critério de aceitação: a palavra correspondente a uma mesma data de referência deve ser idêntica em todas as partidas.
5.5. Usabilidade e acessibilidade
RNF-18 — Responsividade. A interface deve funcionar adequadamente em computadores, tablets e smartphones.

Critério de aceitação: os elementos principais devem permanecer acessíveis e utilizáveis em larguras de tela a partir de 320 pixels.

RNF-19 — Feedback visual. As ações do jogador devem apresentar retorno visual claro sobre sucesso, erro ou estado de processamento.

Critério de aceitação: o usuário consegue identificar se uma tentativa foi aceita, rejeitada ou processada.

RNF-20 — Acessibilidade. Os elementos interativos devem oferecer identificação acessível por tecnologias assistivas e permitir navegação por teclado.

Critério de aceitação: botões, campos, teclado virtual e feedback das letras possuem identificação semântica, foco visível e alternativas que não dependam exclusivamente de cores.

RNF-21 — Idioma. Toda a interface e as mensagens apresentadas ao usuário devem estar em português brasileiro.

Critério de aceitação: textos, mensagens de erro, instruções e notificações utilizam o idioma pt-BR.
5.6. Manutenibilidade e compatibilidade
RNF-22 — Organização e manutenção. O sistema deve possuir código organizado e separado por responsabilidades, facilitando alterações e correções.

Critério de aceitação: alterações em uma funcionalidade não devem exigir modificações não relacionadas em outras partes do sistema.

RNF-23 — Compatibilidade entre navegadores. A aplicação deve funcionar nas versões estáveis recentes dos principais navegadores.

Critério de aceitação: as funcionalidades principais devem operar corretamente no Google Chrome, Mozilla Firefox, Microsoft Edge e Safari.

RNF-24 — Tratamento de erros. O sistema deve apresentar mensagens compreensíveis quando ocorrerem falhas durante a utilização.

Critério de aceitação: erros inesperados não devem expor informações internas, credenciais, consultas ou detalhes sensíveis da aplicação.

## Restrições e premissas
6.1. Restrições
1. Custo de infraestrutura: o desenvolvimento inicial deve priorizar serviços gratuitos, sem depender de contratação de infraestrutura paga.
2. Hospedagem: a aplicação deverá funcionar dentro dos limites de utilização dos serviços gratuitos escolhidos.
3. Serviço de e-mail: o envio de notificações dependerá de um serviço externo que disponibilize uma modalidade gratuita compatível com o volume esperado.
4. Vocabulário: o jogo utilizará exclusivamente palavras da língua portuguesa brasileira.
5. Palavras válidas: deverá existir uma base de palavras previamente definida e controlada pelo projeto.
6. Frequência: haverá somente uma palavra diária, compartilhada entre todos os jogadores.
7. Tentativas: cada jogador terá exatamente seis oportunidades por palavra diária.
8. Privacidade: informações pessoais e dados de autenticação não poderão ser disponibilizados publicamente.
9. Carregamento: não serão implementados atrasos artificiais ou telas de carregamento sem operação real que os justifique.
10. Dependências externas: indisponibilidade de serviços externos, como o provedor de e-mail, poderá afetar funcionalidades dependentes desses serviços, sem comprometer desnecessariamente o funcionamento do jogo.
6.2. Premissas
1. O público-alvo possui acesso à internet e utiliza navegadores modernos.
2. Cada jogador utilizará uma conta individual para registrar suas partidas e estatísticas.
3. O dia oficial do jogo será definido pelo fuso horário de Brasília (America/Sao_Paulo).
4. A palavra diária será escolhida previamente e armazenada antes de sua disponibilização.
5. O vocabulário será revisado para evitar palavras inadequadas, ambíguas ou excessivamente desconhecidas.
6. O ranking será baseado em critérios públicos e iguais para todos os jogadores.
7. A comunicação por e-mail será opcional e dependerá da autorização do usuário.
8. Os jogadores poderão consultar o histórico de partidas sem alterar resultados já registrados.
9. O sistema deverá funcionar mesmo quando o jogador não desejar receber notificações por e-mail.
10. O projeto será desenvolvido inicialmente como uma aplicação web, contemplando frontend, backend e persistência de dados.

# 7. Decisões de produto que precisam ser formalizadas
7. Decisões de produto que precisam ser formalizadas
Algumas regras ainda precisam de definição antes do desenvolvimento, pois influenciam diretamente a implementação e os testes.
- Tamanho das palavras: 5 letras.
- Acentuação: comparação sem distinção entre letras acentuadas e não acentuadas, mantendo a grafia correta na apresentação.
- Palavras repetidas: permitidas, respeitando a quantidade existente na palavra secreta.
- Palavra diária: uma palavra por data, no fuso de Brasília.
- Tentativas: 6 por dia.
- Jogar sem cadastro: permitir visualização da página, mas exigir conta para registrar partidas e participar do ranking.
- Ranking: pontuação baseada em vitórias e quantidade de tentativas utilizadas.
- Histórico: somente partidas do próprio usuário.
- E-mail diário: opcional, mediante consentimento.
- Descadastro: link direto no próprio e-mail.
Essas definições são propostas iniciais, não requisitos já aprovados. Recomenda-se registrá-las em um documento de decisões de produto antes de transformá-las em regras definitivas.

# 8. Critérios gerais de conclusão do projeto
O projeto será considerado funcionalmente concluído quando:
- [ ] O usuário conseguir criar uma conta, entrar e sair.
- [ ] O usuário conseguir jogar a palavra diária.
- [ ] O jogo limitar as tentativas a seis.
- [ ] O feedback das letras funcionar corretamente, inclusive com letras repetidas.
- [ ] As partidas forem salvas corretamente.
- [ ] O placar individual apresentar estatísticas consistentes.
- [ ] O histórico apresentar partidas anteriores.
- [ ] O ranking refletir os resultados registrados.
- [ ] Os e-mails diários forem enviados somente aos usuários autorizados.
- [ ] O descadastro interromper os próximos envios.
- [ ] O usuário conseguir consultar e excluir seus dados pessoais.
- [ ] Os requisitos de segurança, desempenho, privacidade e responsividade forem testados.
- [ ] Não existirem carregamentos artificiais ou atrasos sem justificativa funcional.