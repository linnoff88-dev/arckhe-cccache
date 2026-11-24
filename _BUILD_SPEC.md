# _BUILD_SPEC â€” curso cccache (Prompt Caching no Claude Code)

> Documento de coordenaÃ§Ã£o para os subagentes que constroem o curso no **formato-curso-v2**.
> Cada agente DEVE ler a skill `formato-curso-v2` (MASTER_COMPLETO.md, LEARN-LAYER.md, SVG-FUTURISTA.md, CHECKLIST_REVISAO.md) e obedecer TODOS os erros crÃ­ticos #1â€“#31.
> Este arquivo dÃ¡ o **conteÃºdo** (fatos de caching, jÃ¡ corretos â€” NÃƒO invente nem altere) e o **contrato compartilhado** (courseId, manifesto, nav, assets) para as pÃ¡ginas ficarem consistentes.
> `_BUILD_SPEC.md` Ã© interno â€” NÃƒO vira pÃ¡gina do curso.

## Identidade do curso

- **courseId (meta `ARCKHÉ-course` e namespace `ARCKHÉ.<courseId>`):** `cccache`
- **TÃ­tulo:** `cccache â€” Prompt Caching no Claude Code`
- **SubtÃ­tulo/promessa:** Entenda de verdade o cache que roda por baixo quando vocÃª conversa com o Claude Code â€” o que reaproveita, o que quebra, e como pagar 10% em vez de 100% pelo contexto.
- **PÃºblico:** quem usa o Claude Code no dia a dia e quer economia, velocidade e contexto controlado (nÃ£o precisa ser dev de API).
- **Offline-first:** curso 100% `file://`. SEM dependÃªncia de rede. SVGs inline obrigatÃ³rios (nada de ARCKHÉimg/CDN de imagem). Tailwind via CDN Ã© o Ãºnico externo (padrÃ£o da skill).

## Paleta por trilha

| Trilha | Tema | Cor v2 | Pasta |
|---|---|---|---|
| Trilha 1 â€” Fundamentos e termos | T1 Emerald | `emerald` | `curso/trilha1/` |
| Trilha 2 â€” TÃ©cnico | T2 Blue | `blue` | `curso/trilha2/` |
| Trilha 3 â€” Boas prÃ¡ticas avanÃ§adas | T3 Purple | `purple` | `curso/trilha3/` |

## Contrato de assets (DRY â€” referenciar, nÃ£o colar o par learn.css/learn.js)

- Assets compartilhados: `assets/learn.css` e `assets/learn.js` (construÃ­dos pelo agente FundaÃ§Ã£o).
- **Anti-FOUC** e **`ARCKHÉ.init()`** sÃ£o SEMPRE snippets inline curtos em cada pÃ¡gina (nunca externalizados).
- Caminhos relativos por profundidade:
  - Landing `index.html` (raiz): `assets/learn.css`, `assets/learn.js`
  - Trilha `curso/trilhaN/index.html` e mÃ³dulos `curso/trilhaN/modulo-*.html`: `../../assets/learn.css`, `../../assets/learn.js`

## Nav (idÃªntico em TODAS as pÃ¡ginas â€” erro #13)

Logo ARCKHÉ + `ARCKHÉ AI` (`text-sky-400`, link `https://ARCKHÉ AI`) + 3 botÃµes de trilha + theme toggle. Trilha ativa destacada. Links relativos por profundidade:

- Da **landing** (raiz): `curso/trilha1/index.html`, `curso/trilha2/index.html`, `curso/trilha3/index.html`
- De uma **pÃ¡gina em `curso/trilhaN/`**: `../trilha1/index.html`, `../trilha2/index.html`, `../trilha3/index.html`, e a landing em `../../index.html`

RÃ³tulos dos botÃµes: `Fundamentos` (T1), `TÃ©cnico` (T2), `Boas prÃ¡ticas` (T3).

## Manifesto do curso (erro #28 â€” COLAR IDÃŠNTICO no `<head>` de TODA pÃ¡gina)

Cada agente ajusta a forma exata ao LEARN-LAYER Â§1.7/Â§3.9, mas mantÃ©m estes `id`/`title`/`topics`/`href` SEM alterar. `topics` casa 1:1 com os `data-ARCKHÉ-topic="<moduloId>#<topicoId>"` reais de cada mÃ³dulo.

```json
{
  "course": { "id": "cccache", "title": "cccache â€” Prompt Caching no Claude Code" },
  "tracks": [
    {
      "id": "trilha1", "title": "Fundamentos e termos",
      "modules": [
        { "id": "modulo-1-1", "title": "O que Ã© prompt caching", "href": "curso/trilha1/modulo-1-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-1-2", "title": "Termos e economia", "href": "curso/trilha1/modulo-1-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    },
    {
      "id": "trilha2", "title": "TÃ©cnico",
      "modules": [
        { "id": "modulo-2-1", "title": "O cache numa conversa", "href": "curso/trilha2/modulo-2-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-2-2", "title": "Skills e ferramentas: anexar vs quebrar", "href": "curso/trilha2/modulo-2-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-2-3", "title": "InvalidaÃ§Ã£o a fundo", "href": "curso/trilha2/modulo-2-3.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    },
    {
      "id": "trilha3", "title": "Boas prÃ¡ticas avanÃ§adas",
      "modules": [
        { "id": "modulo-3-1", "title": "Cache vs CompactaÃ§Ã£o", "href": "curso/trilha3/modulo-3-1.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-3-2", "title": "Arquitetura prÃ³-cache e auditoria", "href": "curso/trilha3/modulo-3-2.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] },
        { "id": "modulo-3-3", "title": "Prompts prontos (copy-run)", "href": "curso/trilha3/modulo-3-3.html",
          "topics": ["topico-1","topico-2","topico-3","topico-4","topico-5","topico-6"] }
      ]
    }
  ]
}
```

---

# CONTEÃšDO â€” fatos de caching (base de verdade; NÃƒO inventar nem contradizer)

**O invariante que explica tudo:** prompt caching Ã© um **casamento de prefixo**. A chave do cache sÃ£o os bytes exatos do prompt atÃ© um ponto de corte (`cache_control`). Qualquer byte que mude no prefixo invalida tudo dali pra frente. Ordem de montagem: **`tools` â†’ `system` â†’ `messages`**.

**NÃºmeros de economia (usar consistente em todo o curso):** leitura do cache (hit) â‰ˆ **0,1Ã—** do preÃ§o de input; gravaÃ§Ã£o (write) â‰ˆ **1,25Ã—** com TTL de 5 min e â‰ˆ **2Ã—** com TTL de 1 h; token nÃ£o-cacheado = **1Ã—** (cheio). Break-even: com TTL 5 min, 2 requisiÃ§Ãµes jÃ¡ compensam; com 1 h, ~3.

**Campos de verificaÃ§Ã£o:** `cache_read_input_tokens` (lido do cache), `cache_creation_input_tokens` (gravado), `input_tokens` (sÃ³ o resto nÃ£o-cacheado). Total do prompt = soma dos trÃªs. Se `cache_read_input_tokens` fica 0 repetindo o mesmo prefixo â†’ tem silent invalidator.

## TRILHA 1 â€” Fundamentos e termos (emerald). Todo mÃ³dulo aqui Ã© FUNDAMENTO: define cada termo na 1Âª apariÃ§Ã£o (erro #31), estilo "Novo aqui?".

### modulo-1-1.html â€” "O que Ã© prompt caching"
- **topico-1 â€” O problema: reprocessar tudo toda vez.** A API Ã© stateless: a cada mensagem vocÃª reenvia a conversa inteira (prompt de sistema + ferramentas + histÃ³rico). Sem cache, o modelo reprocessa tudo do zero todo turno â€” caro e lento. ("Prompt de sistema" = o texto de instruÃ§Ãµes que vem antes da conversa; "stateless" = a API nÃ£o guarda a conversa, vocÃª reenvia sempre.)
- **topico-2 â€” A ideia: reaproveitar o prefixo.** O comeÃ§o da conversa Ã© estÃ¡vel e se repete a cada turno. O cache guarda esse comeÃ§o jÃ¡ processado e reaproveita, em vez de reprocessar.
- **topico-3 â€” O invariante: casamento de prefixo.** A chave sÃ£o os bytes exatos atÃ© o ponto de corte. UM byte diferente no meio invalida tudo dali pra frente. (Definir "prefixo" = o pedaÃ§o do comeÃ§o que se repete igual.)
- **topico-4 â€” A ordem: tools â†’ system â†’ messages.** O prompt Ã© montado nessa ordem. Um breakpoint no fim do `system` cacheia tools + system juntos. Coisa estÃ¡vel vai no comeÃ§o; coisa que muran a cada requisiÃ§Ã£o vai no fim.
- **topico-5 â€” Hit, miss e write.** Hit = leu do cache (barato). Write = gravou no cache (leve prÃªmio). Miss = nÃ£o achou, processou cheio. A 1Âª mensagem grava; as seguintes leem.
- **topico-6 â€” Breakpoint (`cache_control`).** Ã‰ a marca que diz "cacheie atÃ© aqui". MÃ¡x. 4 por requisiÃ§Ã£o; prefixo mÃ­nimo cacheÃ¡vel ~1024â€“4096 tokens (varia por modelo) â€” abaixo disso nÃ£o cacheia e nÃ£o dÃ¡ erro. No Claude Code isso Ã© automÃ¡tico; o aluno nÃ£o precisa marcar Ã  mÃ£o, mas precisa entender o conceito.

### modulo-1-2.html â€” "Termos e economia"
- **topico-1 â€” `cache_read_input_tokens`.** Tokens servidos do cache neste turno; custam ~0,1Ã—.
- **topico-2 â€” `cache_creation_input_tokens`.** Tokens gravados no cache neste turno; custam ~1,25Ã— (5 min) ou ~2Ã— (1 h).
- **topico-3 â€” `input_tokens` (o resto).** SÃ³ a parte NÃƒO cacheada, preÃ§o cheio. Pegadinha: se seu agente rodou horas e `input_tokens` mostra pouco, o resto veio do cache â€” olhe a SOMA dos trÃªs, nÃ£o um campo sÃ³.
- **topico-4 â€” TTL: 5 min e 1 h.** TTL = tempo de vida da entrada. PadrÃ£o 5 min, renovado a cada uso (conversa ativa mantÃ©m quente). Existe opÃ§Ã£o de 1 h (write mais caro, ~2Ã—) pra trÃ¡fego com pausas longas.
- **topico-5 â€” Custos relativos.** read ~0,1Ã— Â· write 5min ~1,25Ã— Â· write 1h ~2Ã— Â· nÃ£o-cacheado 1Ã—. Numa conversa longa, o grosso do input (system + histÃ³rico) sai a ~10% do preÃ§o.
- **topico-6 â€” Break-even.** 5 min: 2 requisiÃ§Ãµes jÃ¡ pagam o write (1,25Ã— + 0,1Ã— = 1,35Ã— vs 2Ã— sem cache). 1 h: precisa ~3. NÃ£o cacheie prefixo que muda todo request (sÃ³ paga write, nunca lÃª).

## TRILHA 2 â€” TÃ©cnico (blue). MÃ³dulos tÃ©cnicos: cada um traz â‰¥1 exemplo copy-run (erro #30) â€” prompt/comando pronto com objetivo + bloco + como verificar.

### modulo-2-1.html â€” "O cache numa conversa"
- **topico-1 â€” O prefixo estÃ¡vel cresce.** system + tools + todo o histÃ³rico (inclusive a Ãºltima resposta) viram o prefixo estÃ¡vel, que cresce a cada turno.
- **topico-2 â€” Hit por turno.** A cada mensagem nova, sÃ³ o final muda; a API relÃª todo o prefixo do cache (~0,1Ã—) e grava sÃ³ o novo.
- **topico-3 â€” TTL de 5 min renovado por uso.** Enquanto vocÃª responde dentro de ~5 min, a janela renova e o cache fica quente.
- **topico-4 â€” A % de cache SOBE a cada turno.** NÃ£o Ã© uma bateria que descarrega. Um turno pode marcar 40% (porque teve coisa nova, ex.: uma skill grande carregada). Esse bloco novo vira read barato no prÃ³ximo turno. Tabela: turno agora 40k lido / 60k novo = 40%; prÃ³ximo turno (+ msg curta) ~100k lido / ~1k novo = ~99%.
- **topico-5 â€” Primeira mensagem = write.** NÃ£o tem o que ler ainda; ela grava o cache (paga um pouco mais).
- **topico-6 â€” Pausa longa = write frio.** Passou dos ~5 min parado, o TTL expira e a prÃ³xima mensagem paga a gravaÃ§Ã£o de novo.
- **Exemplo copy-run:** prompt pro Claude Code â€” "Verifique numa resposta da API os campos `cache_read_input_tokens`, `cache_creation_input_tokens` e `input_tokens` e me explique quanto veio do cache." + como verificar (a soma dos 3 = tamanho do prompt).

### modulo-2-2.html â€” "Skills e ferramentas: anexar vs quebrar"
- **topico-1 â€” Dois sentidos de "skill".** (a) A DESCRIÃ‡ÃƒO da skill (linha curta na lista de skills) fica sempre no prefixo estÃ¡vel. (b) O CONTEÃšDO completo (o documentÃ£o) sÃ³ entra quando a skill Ã© invocada.
- **topico-2 â€” Skill no meio da conversa NÃƒO zera o cache.** O conteÃºdo entra ANEXADO no FIM do histÃ³rico (nÃ£o na posiÃ§Ã£o 0). Tudo antes continua vÃ¡lido e Ã© lido barato; sÃ³ o bloco novo da skill Ã© gravado (um write). Nos turnos seguintes ela jÃ¡ Ã© read barato.
- **topico-3 â€” Quebrar a lista de `tools` = posiÃ§Ã£o 0.** As ferramentas sÃ£o renderizadas na posiÃ§Ã£o 0 (antes de system e histÃ³rico). Mudar a lista `tools` invalida TUDO.
- **topico-4 â€” Exemplos de quebra.** (1) Conectar/desconectar um servidor MCP no meio (registra tools novas). (2) Mudar `description` ou `input_schema` de uma tool (basta uma palavra). (3) Ordem nÃ£o-determinÃ­stica: montar `tools` de um `set`/`dict` sem ordenar â†’ ordem varia entre requests. (4) Ligar/desligar tools por modo/permissÃ£o.
- **topico-5 â€” Tool Search anexa de propÃ³sito.** O Tool Search carrega o schema de uma ferramenta ANEXANDO (nÃ£o trocando a lista) â€” feito justamente pra NÃƒO quebrar o cache. Descobrir tool via Tool Search Ã© seguro; conectar MCP que reescreve a lista, nÃ£o.
- **topico-6 â€” Regra de bolso.** ConteÃºdo novo no FIM = seguro. Mexer na lista de `tools` ou no system prompt = reset da posiÃ§Ã£o 0.
- **Exemplo copy-run:** trecho de cÃ³digo montando `tools` â€” versÃ£o âŒ (de `set`/`dict` sem sort â†’ cache nunca bate) vs âœ… (`sorted(...)` â†’ prefixo idÃªntico). Como verificar: `cache_read_input_tokens` deixa de ser 0 entre requests iguais.

### modulo-2-3.html â€” "InvalidaÃ§Ã£o a fundo"
- **topico-1 â€” Hierarquia de 3 tiers.** MudanÃ§a sÃ³ invalida o tier dela e os de baixo. Tabela: mudar tools OU trocar modelo = reset total (tools+system+messages); mudar system = invalida system+messages; mudar mensagem = sÃ³ messages.
- **topico-2 â€” `tool_choice`/`thinking` on-off NÃƒO derrubam tudo.** Trocar `tool_choice` por request ou ligar/desligar `thinking` mantÃ©m o cache de tools+system. NÃ£o precisa se preocupar com esses.
- **topico-3 â€” 20-block lookback.** Cada breakpoint procura entrada anterior olhando no mÃ¡x. 20 blocos pra trÃ¡s. Turno que adiciona >20 blocos (loops com muitos tool_use/tool_result) pode fazer o prÃ³ximo turno errar o cache silenciosamente. Fix: breakpoint intermediÃ¡rio a cada ~15 blocos.
- **topico-4 â€” Silent invalidators.** `datetime.now()`/`Date.now()`/uuid no system; `json.dumps` sem `sort_keys=True`; iterar `set`; tools montadas por usuÃ¡rio; seÃ§Ã£o condicional no system (`if flag: system += ...`). Sintoma: `cache_read_input_tokens` sempre 0.
- **topico-5 â€” Timing concorrente (fan-out).** A entrada sÃ³ fica legÃ­vel DEPOIS que a 1Âª resposta comeÃ§a a streamar. N requests paralelos com o mesmo prefixo pagam todos preÃ§o cheio. Fix: mandar 1, esperar o 1Âº token, disparar os N-1.
- **topico-6 â€” Verificar com `usage`.** `cache_read_input_tokens` / `cache_creation_input_tokens` na resposta. Zero em requests repetidos = tem invalidator; faÃ§a diff dos bytes do prompt entre dois requests.
- **Exemplo copy-run:** prompt pro Claude Code â€” "Audite este pipeline: procure `datetime.now()`, `uuid`, `json.dumps` sem `sort_keys` e montagem de `tools` por `set` no que alimenta o prefixo; aponte cada silent invalidator e como corrigir." + como verificar.

## TRILHA 3 â€” Boas prÃ¡ticas avanÃ§adas (purple). Fecha com mÃ³dulo de PROMPTS PRONTOS copy-run.

### modulo-3-1.html â€” "Cache vs CompactaÃ§Ã£o"
- **topico-1 â€” Dois eixos diferentes.** Cache = otimiza o PREÃ‡O POR TOKEN do contexto. Compactar = otimiza QUANTOS tokens vocÃª carrega. NÃ£o competem no mesmo eixo. (Definir "compactar" = resumir o histÃ³rico numa versÃ£o menor; no Claude Code, `/compact`.)
- **topico-2 â€” Contexto grande cacheado ainda Ã© caro.** Cache barateia por token, mas 400k tokens lidos a 0,1Ã— ainda equivalem a ~40k de input CHEIO por turno, todo turno.
- **topico-3 â€” O teto do contexto (1M) â€” cache nÃ£o resolve.** O cache deixa 900k tokens baratos, mas eles ainda ocupam 900k de 1M. Uma hora vocÃª nÃ£o continua sem compactar/`/clear`. SÃ³ compactar/limpar resolve o teto.
- **topico-4 â€” Compactar: 1 write frio â†’ turnos leves (nÃºmeros).** Tabela: sem compactar, 400k @0,1Ã— â‰ˆ 40k-equiv por turno, pra sempre. Compactando pra 20k: 1 write frio 20k @1,25Ã— â‰ˆ 25k (uma vez), depois 20k @0,1Ã— â‰ˆ 2k-equiv por turno. Payback em ~1 turno; cada turno seguinte ~20Ã— mais leve.
- **topico-5 â€” Qualidade e latÃªncia.** Contexto inchado espalha a atenÃ§Ã£o do modelo ("context rot") â†’ erra e enrola mais. E mesmo lido do cache, 400k levam mais tempo que 20k (TTFT maior). Compactar melhora os dois.
- **topico-6 â€” Quando compactar / quando NÃƒO.** Conversa pequena â†’ NÃƒO compacte (sÃ³ perde o cache quente sem ganho â€” essa Ã© a intuiÃ§Ã£o certa). Contexto grande, perto do teto, ou qualidade caindo â†’ compacte (troca 1 write frio Ãºnico por turnos muito mais leves).

### modulo-3-2.html â€” "Arquitetura prÃ³-cache e auditoria"
- **topico-1 â€” System prompt congelado.** NÃ£o interpolar data/hora, modo, nome do usuÃ¡rio no system (fica na frente do prefixo e invalida tudo). Injete contexto dinÃ¢mico depois, nas `messages`.
- **topico-2 â€” Tools determinÃ­sticas.** Serialize a lista sempre na mesma ordem (ordene por nome). Set/dict sem sort = ordem variÃ¡vel = miss.
- **topico-3 â€” NÃ£o trocar modelo no meio.** Cache Ã© por modelo. Trocar de modelo invalida tudo. Precisa de um modelo mais barato pra subtarefa? Use subagente, mantendo o loop principal num modelo sÃ³.
- **topico-4 â€” Fork reusa o prefixo do pai.** OperaÃ§Ã£o lateral (resumo, subagente) que remonta system/tools/model diferente perde o cache do pai. Copie system/tools/model verbatim e anexe o especÃ­fico no fim.
- **topico-5 â€” Checklist de silent invalidators.** Varra o que alimenta o prefixo: `datetime.now()`, uuid, `json.dumps` sem `sort_keys`, set, tools por usuÃ¡rio, seÃ§Ãµes condicionais no system.
- **topico-6 â€” PrÃ©-aquecimento e TTL 1h.** RequisiÃ§Ã£o `max_tokens: 0` ao subir o app grava o cache do prefixo e retorna na hora â€” tira a latÃªncia do 1Âº request real. SÃ³ vale se: 1Âª latÃªncia Ã© visÃ­vel, prefixo Ã© grande, e hÃ¡ um momento antes do trÃ¡fego. TTL 1h (write ~2Ã—) pra trÃ¡fego com gaps > 5 min.
- **Exemplo copy-run:** prompt pro Claude Code â€” "Revise meu system prompt e a montagem de `tools`: aponte o que estÃ¡ impedindo cache (interpolaÃ§Ã£o dinÃ¢mica no system, ordem de tools nÃ£o-determinÃ­stica) e reescreva pra maximizar hit." + como verificar.

### modulo-3-3.html â€” "Prompts prontos (copy-run)" â€” mÃ³dulo PRÃTICO, cada tÃ³pico Ã© um prompt colÃ¡vel real (erro #30), com objetivo + bloco copiÃ¡vel (`<isto voce troca>`) + como verificar.
- **topico-1 â€” Auditar cache de um pipeline.** Prompt que manda o Claude Code varrer o cÃ³digo que monta o prompt e listar cada silent invalidator + fix.
- **topico-2 â€” Tornar a lista de tools determinÃ­stica.** Prompt que pede ordenar a serializaÃ§Ã£o de `tools` por nome e confirmar ordem estÃ¡vel entre requests.
- **topico-3 â€” Decidir compactar vs continuar.** Prompt que estima o custo por turno de carregar o contexto atual vs o custo Ãºnico de compactar, e recomenda.
- **topico-4 â€” Diagnosticar `cache_read_input_tokens = 0`.** Prompt que faz diff dos bytes do prefixo entre dois requests iguais e aponta o byte que muda.
- **topico-5 â€” Revisar system prompt prÃ³-cache.** Prompt que tira interpolaÃ§Ã£o dinÃ¢mica do system e move pro fim das messages.
- **topico-6 â€” EstratÃ©gia de breakpoints.** Prompt que sugere onde colocar `cache_control` (fim do system estÃ¡vel; fim do trecho compartilhado num prefixo+sufixo variÃ¡vel) e alerta sobre o 20-block lookback.

---

## Checklist de consistÃªncia entre agentes (conferir antes de entregar cada pÃ¡gina)
1. `courseId = cccache` no `<meta name="ARCKHÉ-course">` e no namespace.
2. Manifesto IDÃŠNTICO (o JSON acima) no `<head>` de toda pÃ¡gina.
3. Nav idÃªntico (3 trilhas + ARCKHÉ AI sky + theme toggle), links relativos certos pela profundidade.
4. `../../assets/learn.css` e `../../assets/learn.js` nas pÃ¡ginas de `curso/trilhaN/`; `assets/...` na landing.
5. Cores: T1 emerald, T2 blue, T3 purple.
6. Cada mÃ³dulo: â‰¥6 tÃ³picos, 500â€“800 linhas, â‰¥1 SVG futurista inline, variedade de componentes; mÃ³dulos tÃ©cnicos/prÃ¡ticos com â‰¥1 exemplo copy-run; mÃ³dulos de fundamento definem termos inline.
7. Anti-FOUC inline primeiro no `<head>`; `ARCKHÉ.init()` por Ãºltimo.
