# _BUILD_SPEC ê¢â¬â curso cccache (Prompt Caching no Claude Code)

> Documento de coordenaêÂ§êÂ£o para os subagentes que constroem o curso no **formato-curso-v2**.
> Cada agente DEVE ler a skill `formato-curso-v2` (MASTER_COMPLETO.md, LEARN-LAYER.md, SVG-FUTURISTA.md, CHECKLIST_REVISAO.md) e obedecer TODOS os erros crêÂ­ticos #1ê¢â¬â#31.
> Este arquivo dêÂ¡ o **conteêÂºdo** (fatos de caching, jêÂ¡ corretos ê¢â¬â NêÆO invente nem altere) e o **contrato compartilhado** (courseId, manifesto, nav, assets) para as pêÂ¡ginas ficarem consistentes.
> `_BUILD_SPEC.md` êÂ© interno ê¢â¬â NêÆO vira pêÂ¡gina do curso.

## Identidade do curso

- **courseId (meta `ARCKHê-course` e namespace `ARCKHê.<courseId>`):** `cccache`
- **TêÂ­tulo:** `cccache ê¢â¬â Prompt Caching no Claude Code`
- **SubtêÂ­tulo/promessa:** Entenda de verdade o cache que roda por baixo quando vocêÂª conversa com o Claude Code ê¢â¬â o que reaproveita, o que quebra, e como pagar 10% em vez de 100% pelo contexto.
- **PêÂºblico:** quem usa o Claude Code no dia a dia e quer economia, velocidade e contexto controlado (nêÂ£o precisa ser dev de API).
- **Offline-first:** curso 100% `file://`. SEM dependêÂªncia de rede. SVGs inline obrigatêÂ³rios (nada de ARCKHêimg/CDN de imagem). Tailwind via CDN êÂ© o êÂºnico externo (padrêÂ£o da skill).

## Paleta por trilha

| Trilha | Tema | Cor v2 | Pasta |
|---|---|---|---|
| Trilha 1 ê¢â¬â Fundamentos e termos | T1 Emerald | `emerald` | `curso/trilha1/` |
| Trilha 2 ê¢â¬â TêÂ©cnico | T2 Blue | `blue` | `curso/trilha2/` |
| Trilha 3 ê¢â¬â Boas prêÂ¡ticas avanêÂ§adas | T3 Purple | `purple` | `curso/trilha3/` |

## Contrato de assets (DRY ê¢â¬â referenciar, nêÂ£o colar o par learn.css/learn.js)

- Assets compartilhados: `assets/learn.css` e `assets/learn.js` (construêÂ­dos pelo agente FundaêÂ§êÂ£o).
- **Anti-FOUC** e **`ARCKHê.init()`** sêÂ£o SEMPRE snippets inline curtos em cada pêÂ¡gina (nunca externalizados).
- Caminhos relativos por profundidade:
  - Landing `index.html` (raiz): `assets/learn.css`, `assets/learn.js`
  - Trilha `curso/trilhaN/index.html` e mêÂ³dulos `curso/trilhaN/modulo-*.html`: `../../assets/learn.css`, `../../assets/learn.js`

## Nav (idêÂªntico em TODAS as pêÂ¡ginas ê¢â¬â erro #13)

Logo ARCKHê + `ARCKHê AI` (`text-sky-400`, link `https://ARCKHê AI`) + 3 botêÂµes de trilha + theme toggle. Trilha ativa destacada. Links relativos por profundidade:

- Da **landing** (raiz): `curso/trilha1/index.html`, `curso/trilha2/index.html`, `curso/trilha3/index.html`
- De uma **pêÂ¡gina em `curso/trilhaN/`**: `../trilha1/index.html`, `../trilha2/index.html`, `../trilha3/index.html`, e a landing em `../../index.html`

RêÂ³tulos dos botêÂµes: `Fundamentos` (T1), `TêÂ©cnico` (T2), `Boas prêÂ¡ticas` (T3).

## Manifesto do curso (erro #28 ê¢â¬â COLAR IDêÅ NTICO no `<head>` de TODA pêÂ¡gina)

Cada agente ajusta a forma exata ao LEARN-LAYER êÂ§1.7/êÂ§3.9, mas mantêÂ©m estes `id`/`title`/`topics`/`href` SEM alterar. `topics` casa 1:1 com os `data-ARCKHê-topic="<moduloId>#<topicoId>"` reais de cada mêÂ³dulo.

```json
{
  "course": { "id": "cccache", "title": "cccache ê¢â¬â Prompt Caching no Claude Code" },
  "tracks": [
    {
      "id": "trilha1", "title": "Fundamentos e termos",
      "modules": [
        { "id": "modulo-1-1", "title": "O que êÂ© prompt caching", "href": "curso/trilha1/modulo-1-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-1-2", "title": "Termos e economia", "href": "curso/trilha1/modulo-1-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    },
    {
      "id": "trilha2", "title": "TêÂ©cnico",
      "modules": [
        { "id": "modulo-2-1", "title": "O cache numa conversa", "href": "curso/trilha2/modulo-2-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-2-2", "title": "Skills e ferramentas: anexar vs quebrar", "href": "curso/trilha2/modulo-2-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-2-3", "title": "InvalidaêÂ§êÂ£o a fundo", "href": "curso/trilha2/modulo-2-3.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    },
    {
      "id": "trilha3", "title": "Boas prêÂ¡ticas avanêÂ§adas",
      "modules": [
        { "id": "modulo-3-1", "title": "Cache vs CompactaêÂ§êÂ£o", "href": "curso/trilha3/modulo-3-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-3-2", "title": "Arquitetura prêÂ³-cache e auditoria", "href": "curso/trilha3/modulo-3-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-3-3", "title": "Prompts prontos (copy-run)", "href": "curso/trilha3/modulo-3-3.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    }
  ]
}
```

---

# CONTEêÅ¡DO ê¢â¬â fatos de caching (base de verdade; NêÆO inventar nem contradizer)

**O invariante que explica tudo:** prompt caching êÂ© um **casamento de prefixo**. A chave do cache sêÂ£o os bytes exatos do prompt atêÂ© um ponto de corte (`cache_control`). Qualquer byte que mude no prefixo invalida tudo dali pra frente. Ordem de montagem: **`tools` ê¢â â `system` ê¢â â `messages`**.

**NêÂºmeros de economia (usar consistente em todo o curso):** leitura do cache (hit) ê¢â°Ë **0,1êâ** do preêÂ§o de input; gravaêÂ§êÂ£o (write) ê¢â°Ë **1,25êâ** com TTL de 5 min e ê¢â°Ë **2êâ** com TTL de 1 h; token nêÂ£o-cacheado = **1êâ** (cheio). Break-even: com TTL 5 min, 2 requisiêÂ§êÂµes jêÂ¡ compensam; com 1 h, ~3.

**Campos de verificaêÂ§êÂ£o:** `cache_read_input_tokens` (lido do cache), `cache_creation_input_tokens` (gravado), `input_tokens` (sêÂ³ o resto nêÂ£o-cacheado). Total do prompt = soma dos trêÂªs. Se `cache_read_input_tokens` fica 0 repetindo o mesmo prefixo ê¢â â tem silent invalidator.

## TRILHA 1 ê¢â¬â Fundamentos e termos (emerald). Todo mêÂ³dulo aqui êÂ© FUNDAMENTO: define cada termo na 1êÂª apariêÂ§êÂ£o (erro #31), estilo "Novo aqui?".

### modulo-1-1.html ê¢â¬â "O que êÂ© prompt caching"
- **topico-1 ê¢â¬â O problema: reprocessar tudo toda vez.** A API êÂ© stateless: a cada mensagem vocêÂª reenvia a conversa inteira (prompt de sistema + ferramentas + histêÂ³rico). Sem cache, o modelo reprocessa tudo do zero todo turno ê¢â¬â caro e lento. ("Prompt de sistema" = o texto de instruêÂ§êÂµes que vem antes da conversa; "stateless" = a API nêÂ£o guarda a conversa, vocêÂª reenvia sempre.)
- **topico-2 ê¢â¬â A ideia: reaproveitar o prefixo.** O comeêÂ§o da conversa êÂ© estêÂ¡vel e se repete a cada turno. O cache guarda esse comeêÂ§o jêÂ¡ processado e reaproveita, em vez de reprocessar.
- **topico-3 ê¢â¬â O invariante: casamento de prefixo.** A chave sêÂ£o os bytes exatos atêÂ© o ponto de corte. UM byte diferente no meio invalida tudo dali pra frente. (Definir "prefixo" = o pedaêÂ§o do comeêÂ§o que se repete igual.)
- **topico-4 ê¢â¬â A ordem: tools ê¢â â system ê¢â â messages.** O prompt êÂ© montado nessa ordem. Um breakpoint no fim do `system` cacheia tools + system juntos. Coisa estêÂ¡vel vai no comeêÂ§o; coisa que muran a cada requisiêÂ§êÂ£o vai no fim.
- **topico-5 ê¢â¬â Hit, miss e write.** Hit = leu do cache (barato). Write = gravou no cache (leve prêÂªmio). Miss = nêÂ£o achou, processou cheio. A 1êÂª mensagem grava; as seguintes leem.
- **topico-6 ê¢â¬â Breakpoint (`cache_control`).** êâ° a marca que diz "cacheie atêÂ© aqui". MêÂ¡x. 4 por requisiêÂ§êÂ£o; prefixo mêÂ­nimo cacheêÂ¡vel ~1024ê¢â¬â4096 tokens (varia por modelo) ê¢â¬â abaixo disso nêÂ£o cacheia e nêÂ£o dêÂ¡ erro. No Claude Code isso êÂ© automêÂ¡tico; o aluno nêÂ£o precisa marcar êÂ  mêÂ£o, mas precisa entender o conceito.

### modulo-1-2.html ê¢â¬â "Termos e economia"
- **topico-1 ê¢â¬â `cache_read_input_tokens`.** Tokens servidos do cache neste turno; custam ~0,1êâ.
- **topico-2 ê¢â¬â `cache_creation_input_tokens`.** Tokens gravados no cache neste turno; custam ~1,25êâ (5 min) ou ~2êâ (1 h).
- **topico-3 ê¢â¬â `input_tokens` (o resto).** SêÂ³ a parte NêÆO cacheada, preêÂ§o cheio. Pegadinha: se seu agente rodou horas e `input_tokens` mostra pouco, o resto veio do cache ê¢â¬â olhe a SOMA dos trêÂªs, nêÂ£o um campo sêÂ³.
- **topico-4 ê¢â¬â TTL: 5 min e 1 h.** TTL = tempo de vida da entrada. PadrêÂ£o 5 min, renovado a cada uso (conversa ativa mantêÂ©m quente). Existe opêÂ§êÂ£o de 1 h (write mais caro, ~2êâ) pra trêÂ¡fego com pausas longas.
- **topico-5 ê¢â¬â Custos relativos.** read ~0,1êâ êÂ· write 5min ~1,25êâ êÂ· write 1h ~2êâ êÂ· nêÂ£o-cacheado 1êâ. Numa conversa longa, o grosso do input (system + histêÂ³rico) sai a ~10% do preêÂ§o.
- **topico-6 ê¢â¬â Break-even.** 5 min: 2 requisiêÂ§êÂµes jêÂ¡ pagam o write (1,25êâ + 0,1êâ = 1,35êâ vs 2êâ sem cache). 1 h: precisa ~3. NêÂ£o cacheie prefixo que muda todo request (sêÂ³ paga write, nunca lêÂª).

## TRILHA 2 ê¢â¬â TêÂ©cnico (blue). MêÂ³dulos têÂ©cnicos: cada um traz ê¢â°Â¥1 exemplo copy-run (erro #30) ê¢â¬â prompt/comando pronto com objetivo + bloco + como verificar.

### modulo-2-1.html ê¢â¬â "O cache numa conversa"
- **topico-1 ê¢â¬â O prefixo estêÂ¡vel cresce.** system + tools + todo o histêÂ³rico (inclusive a êÂºltima resposta) viram o prefixo estêÂ¡vel, que cresce a cada turno.
- **topico-2 ê¢â¬â Hit por turno.** A cada mensagem nova, sêÂ³ o final muda; a API relêÂª todo o prefixo do cache (~0,1êâ) e grava sêÂ³ o novo.
- **topico-3 ê¢â¬â TTL de 5 min renovado por uso.** Enquanto vocêÂª responde dentro de ~5 min, a janela renova e o cache fica quente.
- **topico-4 ê¢â¬â A % de cache SOBE a cada turno.** NêÂ£o êÂ© uma bateria que descarrega. Um turno pode marcar 40% (porque teve coisa nova, ex.: uma skill grande carregada). Esse bloco novo vira read barato no prêÂ³ximo turno. Tabela: turno agora 40k lido / 60k novo = 40%; prêÂ³ximo turno (+ msg curta) ~100k lido / ~1k novo = ~99%.
- **topico-5 ê¢â¬â Primeira mensagem = write.** NêÂ£o tem o que ler ainda; ela grava o cache (paga um pouco mais).
- **topico-6 ê¢â¬â Pausa longa = write frio.** Passou dos ~5 min parado, o TTL expira e a prêÂ³xima mensagem paga a gravaêÂ§êÂ£o de novo.
- **Exemplo copy-run:** prompt pro Claude Code ê¢â¬â "Verifique numa resposta da API os campos `cache_read_input_tokens`, `cache_creation_input_tokens` e `input_tokens` e me explique quanto veio do cache." + como verificar (a soma dos 3 = tamanho do prompt).

### modulo-2-2.html ê¢â¬â "Skills e ferramentas: anexar vs quebrar"
- **topico-1 ê¢â¬â Dois sentidos de "skill".** (a) A DESCRIêâ¡êÆO da skill (linha curta na lista de skills) fica sempre no prefixo estêÂ¡vel. (b) O CONTEêÅ¡DO completo (o documentêÂ£o) sêÂ³ entra quando a skill êÂ© invocada.
- **topico-2 ê¢â¬â Skill no meio da conversa NêÆO zera o cache.** O conteêÂºdo entra ANEXADO no FIM do histêÂ³rico (nêÂ£o na posiêÂ§êÂ£o 0). Tudo antes continua vêÂ¡lido e êÂ© lido barato; sêÂ³ o bloco novo da skill êÂ© gravado (um write). Nos turnos seguintes ela jêÂ¡ êÂ© read barato.
- **topico-3 ê¢â¬â Quebrar a lista de `tools` = posiêÂ§êÂ£o 0.** As ferramentas sêÂ£o renderizadas na posiêÂ§êÂ£o 0 (antes de system e histêÂ³rico). Mudar a lista `tools` invalida TUDO.
- **topico-4 ê¢â¬â Exemplos de quebra.** (1) Conectar/desconectar um servidor MCP no meio (registra tools novas). (2) Mudar `description` ou `input_schema` de uma tool (basta uma palavra). (3) Ordem nêÂ£o-determinêÂ­stica: montar `tools` de um `set`/`dict` sem ordenar ê¢â â ordem varia entre requests. (4) Ligar/desligar tools por modo/permissêÂ£o.
- **topico-5 ê¢â¬â Tool Search anexa de propêÂ³sito.** O Tool Search carrega o schema de uma ferramenta ANEXANDO (nêÂ£o trocando a lista) ê¢â¬â feito justamente pra NêÆO quebrar o cache. Descobrir tool via Tool Search êÂ© seguro; conectar MCP que reescreve a lista, nêÂ£o.
- **topico-6 ê¢â¬â Regra de bolso.** ConteêÂºdo novo no FIM = seguro. Mexer na lista de `tools` ou no system prompt = reset da posiêÂ§êÂ£o 0.
- **Exemplo copy-run:** trecho de cêÂ³digo montando `tools` ê¢â¬â versêÂ£o ê¢ÂÅ (de `set`/`dict` sem sort ê¢â â cache nunca bate) vs ê¢Åâ¦ (`sorted(...)` ê¢â â prefixo idêÂªntico). Como verificar: `cache_read_input_tokens` deixa de ser 0 entre requests iguais.

### modulo-2-3.html ê¢â¬â "InvalidaêÂ§êÂ£o a fundo"
- **topico-1 ê¢â¬â Hierarquia de 3 tiers.** MudanêÂ§a sêÂ³ invalida o tier dela e os de baixo. Tabela: mudar tools OU trocar modelo = reset total (tools+system+messages); mudar system = invalida system+messages; mudar mensagem = sêÂ³ messages.
- **topico-2 ê¢â¬â `tool_choice`/`thinking` on-off NêÆO derrubam tudo.** Trocar `tool_choice` por request ou ligar/desligar `thinking` mantêÂ©m o cache de tools+system. NêÂ£o precisa se preocupar com esses.
- **topico-3 ê¢â¬â 20-block lookback.** Cada breakpoint procura entrada anterior olhando no mêÂ¡x. 20 blocos pra trêÂ¡s. Turno que adiciona >20 blocos (loops com muitos tool_use/tool_result) pode fazer o prêÂ³ximo turno errar o cache silenciosamente. Fix: breakpoint intermediêÂ¡rio a cada ~15 blocos.
- **topico-4 ê¢â¬â Silent invalidators.** `datetime.now()`/`Date.now()`/uuid no system; `json.dumps` sem `sort_keys=True`; iterar `set`; tools montadas por usuêÂ¡rio; seêÂ§êÂ£o condicional no system (`if flag: system += ...`). Sintoma: `cache_read_input_tokens` sempre 0.
- **topico-5 ê¢â¬â Timing concorrente (fan-out).** A entrada sêÂ³ fica legêÂ­vel DEPOIS que a 1êÂª resposta comeêÂ§a a streamar. N requests paralelos com o mesmo prefixo pagam todos preêÂ§o cheio. Fix: mandar 1, esperar o 1êÂº token, disparar os N-1.
- **topico-6 ê¢â¬â Verificar com `usage`.** `cache_read_input_tokens` / `cache_creation_input_tokens` na resposta. Zero em requests repetidos = tem invalidator; faêÂ§a diff dos bytes do prompt entre dois requests.
- **Exemplo copy-run:** prompt pro Claude Code ê¢â¬â "Audite este pipeline: procure `datetime.now()`, `uuid`, `json.dumps` sem `sort_keys` e montagem de `tools` por `set` no que alimenta o prefixo; aponte cada silent invalidator e como corrigir." + como verificar.

## TRILHA 3 ê¢â¬â Boas prêÂ¡ticas avanêÂ§adas (purple). Fecha com mêÂ³dulo de PROMPTS PRONTOS copy-run.

### modulo-3-1.html ê¢â¬â "Cache vs CompactaêÂ§êÂ£o"
- **topico-1 ê¢â¬â Dois eixos diferentes.** Cache = otimiza o PREêâ¡O POR TOKEN do contexto. Compactar = otimiza QUANTOS tokens vocêÂª carrega. NêÂ£o competem no mesmo eixo. (Definir "compactar" = resumir o histêÂ³rico numa versêÂ£o menor; no Claude Code, `/compact`.)
- **topico-2 ê¢â¬â Contexto grande cacheado ainda êÂ© caro.** Cache barateia por token, mas 400k tokens lidos a 0,1êâ ainda equivalem a ~40k de input CHEIO por turno, todo turno.
- **topico-3 ê¢â¬â O teto do contexto (1M) ê¢â¬â cache nêÂ£o resolve.** O cache deixa 900k tokens baratos, mas eles ainda ocupam 900k de 1M. Uma hora vocêÂª nêÂ£o continua sem compactar/`/clear`. SêÂ³ compactar/limpar resolve o teto.
- **topico-4 ê¢â¬â Compactar: 1 write frio ê¢â â turnos leves (nêÂºmeros).** Tabela: sem compactar, 400k @0,1êâ ê¢â°Ë 40k-equiv por turno, pra sempre. Compactando pra 20k: 1 write frio 20k @1,25êâ ê¢â°Ë 25k (uma vez), depois 20k @0,1êâ ê¢â°Ë 2k-equiv por turno. Payback em ~1 turno; cada turno seguinte ~20êâ mais leve.
- **topico-5 ê¢â¬â Qualidade e latêÂªncia.** Contexto inchado espalha a atenêÂ§êÂ£o do modelo ("context rot") ê¢â â erra e enrola mais. E mesmo lido do cache, 400k levam mais tempo que 20k (TTFT maior). Compactar melhora os dois.
- **topico-6 ê¢â¬â Quando compactar / quando NêÆO.** Conversa pequena ê¢â â NêÆO compacte (sêÂ³ perde o cache quente sem ganho ê¢â¬â essa êÂ© a intuiêÂ§êÂ£o certa). Contexto grande, perto do teto, ou qualidade caindo ê¢â â compacte (troca 1 write frio êÂºnico por turnos muito mais leves).

### modulo-3-2.html ê¢â¬â "Arquitetura prêÂ³-cache e auditoria"
- **topico-1 ê¢â¬â System prompt congelado.** NêÂ£o interpolar data/hora, modo, nome do usuêÂ¡rio no system (fica na frente do prefixo e invalida tudo). Injete contexto dinêÂ¢mico depois, nas `messages`.
- **topico-2 ê¢â¬â Tools determinêÂ­sticas.** Serialize a lista sempre na mesma ordem (ordene por nome). Set/dict sem sort = ordem variêÂ¡vel = miss.
- **topico-3 ê¢â¬â NêÂ£o trocar modelo no meio.** Cache êÂ© por modelo. Trocar de modelo invalida tudo. Precisa de um modelo mais barato pra subtarefa? Use subagente, mantendo o loop principal num modelo sêÂ³.
- **topico-4 ê¢â¬â Fork reusa o prefixo do pai.** OperaêÂ§êÂ£o lateral (resumo, subagente) que remonta system/tools/model diferente perde o cache do pai. Copie system/tools/model verbatim e anexe o especêÂ­fico no fim.
- **topico-5 ê¢â¬â Checklist de silent invalidators.** Varra o que alimenta o prefixo: `datetime.now()`, uuid, `json.dumps` sem `sort_keys`, set, tools por usuêÂ¡rio, seêÂ§êÂµes condicionais no system.
- **topico-6 ê¢â¬â PrêÂ©-aquecimento e TTL 1h.** RequisiêÂ§êÂ£o `max_tokens: 0` ao subir o app grava o cache do prefixo e retorna na hora ê¢â¬â tira a latêÂªncia do 1êÂº request real. SêÂ³ vale se: 1êÂª latêÂªncia êÂ© visêÂ­vel, prefixo êÂ© grande, e hêÂ¡ um momento antes do trêÂ¡fego. TTL 1h (write ~2êâ) pra trêÂ¡fego com gaps > 5 min.
- **Exemplo copy-run:** prompt pro Claude Code ê¢â¬â "Revise meu system prompt e a montagem de `tools`: aponte o que estêÂ¡ impedindo cache (interpolaêÂ§êÂ£o dinêÂ¢mica no system, ordem de tools nêÂ£o-determinêÂ­stica) e reescreva pra maximizar hit." + como verificar.

### modulo-3-3.html ê¢â¬â "Prompts prontos (copy-run)" ê¢â¬â mêÂ³dulo PRêÂTICO, cada têÂ³pico êÂ© um prompt colêÂ¡vel real (erro #30), com objetivo + bloco copiêÂ¡vel (`<isto voce troca>`) + como verificar.
- **topico-1 ê¢â¬â Auditar cache de um pipeline.** Prompt que manda o Claude Code varrer o cêÂ³digo que monta o prompt e listar cada silent invalidator + fix.
- **topico-2 ê¢â¬â Tornar a lista de tools determinêÂ­stica.** Prompt que pede ordenar a serializaêÂ§êÂ£o de `tools` por nome e confirmar ordem estêÂ¡vel entre requests.
- **topico-3 ê¢â¬â Decidir compactar vs continuar.** Prompt que estima o custo por turno de carregar o contexto atual vs o custo êÂºnico de compactar, e recomenda.
- **topico-4 ê¢â¬â Diagnosticar `cache_read_input_tokens = 0`.** Prompt que faz diff dos bytes do prefixo entre dois requests iguais e aponta o byte que muda.
- **topico-5 ê¢â¬â Revisar system prompt prêÂ³-cache.** Prompt que tira interpolaêÂ§êÂ£o dinêÂ¢mica do system e move pro fim das messages.
- **topico-6 ê¢â¬â EstratêÂ©gia de breakpoints.** Prompt que sugere onde colocar `cache_control` (fim do system estêÂ¡vel; fim do trecho compartilhado num prefixo+sufixo variêÂ¡vel) e alerta sobre o 20-block lookback.

---

## Checklist de consistêÂªncia entre agentes (conferir antes de entregar cada pêÂ¡gina)
1. `courseId = cccache` no `<meta name="ARCKHê-course">` e no namespace.
2. Manifesto IDêÅ NTICO (o JSON acima) no `<head>` de toda pêÂ¡gina.
3. Nav idêÂªntico (3 trilhas + ARCKHê AI sky + theme toggle), links relativos certos pela profundidade.
4. `../../assets/learn.css` e `../../assets/learn.js` nas pêÂ¡ginas de `curso/trilhaN/`; `assets/...` na landing.
5. Cores: T1 emerald, T2 blue, T3 purple.
6. Cada mêÂ³dulo: ê¢â°Â¥6 têÂ³picos, 500ê¢â¬â800 linhas, ê¢â°Â¥1 SVG futurista inline, variedade de componentes; mêÂ³dulos têÂ©cnicos/prêÂ¡ticos com ê¢â°Â¥1 exemplo copy-run; mêÂ³dulos de fundamento definem termos inline.
7. Anti-FOUC inline primeiro no `<head>`; `ARCKHê.init()` por êÂºltimo.
