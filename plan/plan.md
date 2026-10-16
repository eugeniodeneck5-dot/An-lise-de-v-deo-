# Tela de Análise — editor de trecho, marcações com realce e tempo, e placar corrigido

Melhorias na tela onde o vídeo é analisado: um editor de trecho em destaque que abre junto com o painel de classificação, marcações de desenho com realce translúcido e presas ao momento exato do lance, e um topo com as informações da partida e o placar funcionando certo.
Nada do que já funciona é removido — só é corrigido o que está com problema e acrescentado o que foi pedido.

## Para quem é
Você (treinador/analista), que marca os lances assistindo ao vídeo e precisa editar o trecho, desenhar sobre a jogada e acompanhar o placar sem travar.

## Funcionalidades e experiência

### 1. Corrigir a ferramenta de texto (bug)
- Hoje, com a ferramenta "Texto" ativa, **todo clique na tela abre a caixa de texto de novo** e você não consegue mais mexer em nada.
- Correção: depois de escrever um texto, a ferramenta volta sozinha para o modo "selecionar", então os cliques seguintes voltam a mover/selecionar normalmente. Cancelar a caixa (sem escrever) não cria nada.

### 2. Editor de trecho em destaque, aberto junto com o painel
- Ao clicar num fundamento (ex.: "Saque") na barra ⚡, o vídeo entra em **modo trecho**: foca só nos ~20s do lance (o recorte "antes/depois" de hoje), e o **painel de classificação abre ao lado ao mesmo tempo**, para você classificar enquanto assiste àquele pedaço — tudo numa tela só, para acelerar.
- No editor do trecho dá para:
  - **Reproduzir o recorte** (toca uma vez, com play/pausa manual — sem repetir em loop),
  - **Aumentar ou diminuir o recorte** por alças de arrastar nas pontas e por botões "+/−" (os campos "antes/depois" em segundos continuam existindo),
  - Usar os controles de sempre (voltar/avançar, 0,25x/0,5x/1x, quadro a quadro).
- A classificação ao lado mantém **tudo que já existe**: equipe da ação, fundamento, classificação, atletas, set, formação, fase tática, posição no lance, resultado, **mapa da quadra** (a marcação na linha da quadra, que fica boa, é mantida) e observações.
- Fora do modo trecho, o vídeo volta a ser o vídeo cheio, como hoje.

### 3. Marcações de desenho: realce translúcido + presas ao tempo
- **Realce (marca-texto):** nova ferramenta que pinta uma área com **preenchimento translúcido** (amarelo por padrão, com escolha de cor), para destacar sem ser só o contorno. As formas atuais (seta, linha, retângulo, elipse, trajetória, texto) continuam.
- **Presas ao momento exato:** cada marcação fica ligada ao instante do vídeo em que foi feita. Ao reproduzir o trecho, **o vídeo pausa sozinho naquele instante e mostra o desenho** (ex.: parar no "braço baixo" com a seta em cima); ao dar play de novo, segue.
- **Fixar no trecho inteiro:** cada marcação tem a opção de ficar **visível durante todo o trecho** (não some e não pausa), para quando você quiser deixar algo marcado o tempo todo.
- **Ligar/desligar a pausa automática:** um botão controla se o vídeo pausa nas marcações ou só as mostra sem parar.

### 4. Topo com informações da partida + placar corrigido
- Uma **faixa no topo** mostra as informações do vídeo e contadores da análise: título/categoria/adversário, **placar atual**, nº de **saques** marcados, nº de **side-outs**, nº de rallies e pontos de cada lado — no estilo "Saque 001 · Side-out 001".
- **Corrigir o placar:** revisar o método para os pontos aparecerem e somarem corretamente (quem saca, ponto nosso/adversário, troca de vencedor recalculando), deixando o placar claro e confiável. O placar continua podendo acompanhar o tempo do vídeo.

## Fluxo de uso
1. Abre o vídeo e assiste.
2. No momento do lance, clica no fundamento na barra ⚡ → o vídeo foca no trecho e o painel de classificação abre ao lado.
3. Ajusta o recorte (alças/"+/−"), reproduz o trecho, desenha (realce/seta/etc.) presando ao instante, marca a quadra e preenche a classificação.
4. Salva (ou "salvar e continuar"). Ao reproduzir depois, o trecho pausa nas marcações e mostra os desenhos.
5. Encerra o rally em "ponto de…" e o placar/contadores no topo atualizam.

## Visual e sensação
- Mantém a identidade atual (vermelho/preto AVA, mesmas fontes e componentes). As novidades entram no mesmo estilo, sem redesenhar a tela.
- Editor de trecho com aparência de "recorte" (barra do segmento com alças), painel de classificação ao lado, topo compacto com placar e contadores.

## Fases de implementação

### Fase 1 — MVP (feito agora)
- Correção do bug da ferramenta de texto.
- Editor de trecho em destaque abrindo junto com o painel (reproduzir uma vez, aumentar/diminuir recorte por alças e "+/−").
- Ferramenta de realce translúcido (com cor) + marcações presas ao instante com pausa automática, opção de fixar no trecho todo e botão liga/desliga da pausa.
- Topo com informações da partida e contadores (saques, side-outs, rallies, pontos) + correção do método do placar.

### Fase 2 — Refinos (depois, se quiser)
- Exportar o trecho com as marcações (clipe/imagem) para enviar ao atleta.
- Repetição (loop) opcional do trecho e atalhos de teclado para marcar mais rápido.
- Biblioteca de marcações reutilizáveis (modelos de desenho).

### Fase 3 — Avançado (futuro)
- Linha do tempo visual com todas as marcações sobre a barra do vídeo.
- Comparação lado a lado de dois trechos.

## Suposições
- "Segunda aba" = editor de trecho **dentro do app**, aberto **junto com o painel** de classificação (não uma aba do navegador).
- O recorte reproduz **uma vez** (play/pausa manual), sem loop automático.
- Realce translúcido com **amarelo como padrão** e troca de cor pelas cores já existentes.
- Pausa automática nas marcações **vem ligada por padrão**, com botão para desligar; cada marcação pode ser fixada no trecho inteiro.
- "Side-out" é contado como rally vencido por quem estava recebendo o saque; "Saque" conta os lances de saque marcados. Esses contadores são da análise do vídeo atual.
- O placar continua derivado dos rallies/pontos encerrados; a correção garante soma e exibição corretas, sem mudar a forma de encerrar o ponto.
- Idioma e identidade visual permanecem os atuais (PT-BR, tema AVA). Nenhuma função atual é removida.
