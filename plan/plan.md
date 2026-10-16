# Análise de Vídeo — Manter como está, corrigir, finalizar e preparar para o site dos atletas

Reconstrução **fiel** do projeto enviado (mesmas funções, mesmo visual, mesmo comportamento), corrigindo erros e completando o que falta.
Além disso, o código será **organizado para o futuro**: ligar cada análise a um atleta e preparar o app para, mais tarde, viver dentro do seu outro site (dos atletas), puxando os atletas de lá e enviando as análises de volta.

## Para quem é
Você (treinador/analista) e, no futuro, seus atletas — que poderão visualizar, dentro do seu site principal, as análises de vídeo feitas para cada um.

## Princípio central (o que será e o que NÃO será feito)
- **NÃO mudar** nenhuma função, visual ou fluxo que já funciona no código enviado.
- **Recriar fielmente** o projeto, do jeito que está.
- **Corrigir** apenas erros reais e **completar** o que estiver incompleto para finalizar.
- **Adicionar** o cadastro de atletas e a preparação para integração como **extras aditivos**, sem alterar o comportamento atual do app.

## Fase 1 — MVP (agora)
### a) Preservar e consertar (prioridade)
1. Extrair e revisar o código enviado, função por função.
2. Mapear o que funciona (mantém intacto), o que está quebrado (corrige) e o que está incompleto (finaliza).
3. Testar de ponta a ponta e entregar um relatório: "isto estava quebrado → corrigido", "isto faltava → concluído".

### b) Cadastro de atletas + vínculo com análises (adição)
- Tela simples para **adicionar/editar atletas** (nome e dados básicos).
- Cada **análise de vídeo pode ser ligada a um atleta**.
- Página por atleta mostrando as análises daquele atleta, com:
  - resumo de cada vídeo analisado,
  - **frequência/assiduidade** (quantas análises, com que regularidade),
  - **evolução ao longo do tempo** (histórico das análises por data).
- O app continua funcionando mesmo para análises **sem atleta** vinculado (nada do fluxo atual quebra).

### c) Preparação para o site dos atletas (estrutural, sem conectar ainda)
- Cada atleta terá um identificador próprio e um campo reservado de **"ID externo"** para, no futuro, casar com o atleta correspondente do seu outro site.
- Uma **camada de integração** separada e isolada, hoje "vazia/local", pronta para depois:
  - **puxar a lista de atletas** do outro site,
  - **enviar as análises** (resumo, transcrição, frequência, evolução) de volta para o outro site.
- O app será montado para poder ser **embutido como uma página dentro do seu outro site** (funciona dentro de um iframe/área do site, sem depender de uma navegação própria pesada).
- Nada disso se conecta a nada externo agora — fica preparado para quando você tiver acesso ao outro projeto.

## Melhorias opcionais (só se você aprovar — não alteram o que existe)
- Busca por título de vídeo e por atleta; filtro por situação (analisado / não analisado).
- Exportar a análise/transcrição (PDF ou TXT) para entregar ao atleta.
- Perguntas e respostas sobre o vídeo (chat).
- Transcrição com marcação de tempo (clicar no texto pula para o momento do vídeo).

## Fase 2 — Conectar ao site dos atletas (quando você tiver acesso)
- Ligar a camada de integração ao seu outro site: importar atletas reais e enviar as análises para que cada atleta visualize as suas.
- Autenticação/permissão conforme as regras do seu site principal.

## Fase 3 — Avançado (futuro)
- Painéis de comparação entre atletas, metas e alertas de frequência.
- Compartilhamento individual por link.

## Suposições
- O comportamento e o visual de referência são **o que estiver no código enviado**; em qualquer dúvida, o original prevalece e é apenas corrigido.
- A IA será mantida como já estiver no código; se faltar chave para uma função existente, será usada a **Universal Key da Emergent** (sem custo de chave para você), com o modelo **Gemini 3.1 Pro** para analisar vídeo (resumo/tópicos) e gerar transcrição.
- Os vídeos serão guardados no **armazenamento de objetos da Emergent** (se o projeto já guardar de outra forma, essa forma é preservada; se estiver incompleta, é finalizada).
- No MVP **não há login**; o controle de acesso real virá na Fase 2, seguindo as regras do seu site principal.
- O cadastro de atletas do MVP é **local** e provisório; ele foi desenhado para depois ser substituído/alimentado pelos atletas do seu outro site, sem perder as análises já feitas (via o campo de "ID externo").
- Dados por atleta considerados importantes (decididos por padrão): resumo das análises, frequência/assiduidade e evolução ao longo do tempo. Dá para ajustar quando conectar ao outro site.
- Idioma da interface: Português (Brasil) / o mesmo do projeto original.
- Observação: o conteúdo exato do .zip não pôde ser aberto no planejamento; a revisão detalhada função por função acontece no início da construção, e o relatório final dirá exatamente o que foi corrigido e completado.
