# Entrevista: "Medir demanda con SEO / búsqueda orgánica" — Ruben Gomez (Bidsketch, SignWell) con Rob Walling (SaaS Launchpad)

> **Qué es esto.** Transcript (limpiado y organizado por tema, sin timestamps) de una **entrevista del
> curso de Rob Walling** (SaaS Launchpad) a **Ruben Gomez** —fundador de **Bidsketch** y **SignWell**,
> bootstrapper de larga data y uno de los expertos en SEO / Google organic que Rob respeta—. El tema:
> cómo usar la **demanda de búsqueda** (quién ya busca el producto / la categoría / la solución a un
> problema) como señal en la pre-validación.
>
> **Dónde encaja.** Es el **Playbook de demanda de búsqueda (SEO)** que el comando
> `/saas_idea_prevalidar_2h` trae como **▶ ANEXO**. Alimenta dos dimensiones del 5 PM: **Problem**
> ("¿buscan una solución?") y **Market** (sizing + competencia). El cuerpo del 5 PM sale de otro video
> (`rob-walling-5pm-framework.md`); esto es el anexo SEO.
>
> **⚠️ Atribución — IMPORTANTE.** Esta entrevista es de **Ruben Gomez**. El anexo SEO del comando, además
> de Ruben, contiene material atribuido a un tal **"Ross"** (ejemplos de *window cleaning* / Jobber /
> home-services, los términos *traffic value* y *referring domains*, la técnica *audience research*, la
> regla de ~$30–40k de traffic value, "dejá el ego en la puerta"). **Ese material NO está en esta
> entrevista** → proviene de **otra fuente todavía no incorporada** (probablemente otro experto SEO del
> curso). Lo de **este** archivo es exclusivamente **lo que dijo Ruben** (con acotaciones de Rob marcadas).
>
> **Atribución general:** material del mismo curso que el resto de los comandos (misma fuente/autoridad).

---

## Por qué SEO para un bootstrapper

- **Si ya sos bueno en otro canal** (cold email, etc.), empezá por ahí. Si está todo parejo, **SEO suele
  ser de los mejores** y está **subestimado**.
- **Ventajas:** eficiente en costo, **no requiere spend constante** (como ads) ni un **proceso ongoing**
  (como outbound). Una vez que tu contenido/tools rankean, el tráfico llega solo.
- **Trade-offs:** toma **mucho esfuerzo upfront** y el **feedback cycle es largo** (puede disuadir).
- **Doble valor (acota Rob):** no es solo un flywheel de marketing una vez que tenés producto; te da una
  idea de **cuánta gente busca esta categoría / problema** en todo internet.

## Google es un PROXY, no la demanda total

- Solo estamos mirando Google, pero la misma gente busca/conversa en **YouTube, Amazon, Reddit, Quora,
  Twitter, Facebook groups, Stack Overflow, Slacks privados**. Si hay "email marketing software" como
  categoría, hay libros de email marketing (Kindle), etc.
- Google es **un sliver** del total. Un término con **20.000** búsquedas/mes en Google probablemente
  tiene otras decenas de miles afuera; uno con **1.000** tiene muchas menos. Sirve para **dimensionar el
  interés relativo**, no como verdad absoluta. Es un **proxy** de la demanda en otras áreas (la categoría
  de producto y también los problemas relacionados).

## No hay reglas (encuadre de Rob + Ruben)

- Esto es **entrepreneurship**, no un PhD peer-reviewed. Lo que sigue son **rules of thumb** de la
  experiencia de Ruben y Rob; algunas son reglas más duras, otras cambian con el tiempo. Vas a escuchar
  consejos que contradicen esto de otra gente — suele ser por **contexto distinto** (otro tamaño de
  empresa, otra época). En SEO hay **muchísimas opiniones** (old school, new school, white/black/gray hat).
  Tomalo con criterio.

## Términos que hay que distinguir

- **Domain Authority (Moz) / Domain Rating (Ahrefs):** número **1–100** que estima qué tan "importante"
  es un sitio a ojos de Google y qué tan probable es que rankee bien. **Se basa esencialmente en la
  cantidad de links.** Si mirás el top 10 de una keyword y hay muchos DA/DR altos, va a ser difícil
  meterse. Ej: si los primeros resultados de un término son **irs.gov** (DA ~90), es batalla cuesta
  arriba — salvo que el resultado **no matchee la intención** (ahí Google "puso lo menos malo" y hay
  oportunidad).
- **Keyword volume:** nº de búsquedas (típicamente/mes) de un término. **No son precisos** y no van a
  matchear lo que verás al rankear, pero **relativos entre sí** son buena señal para decidir.
- **Commercial / purchase intent:** términos que tipea alguien que está por comprar. Más cerca de la
  compra: **nombre de producto** o **nombre de categoría**. Más lejos (top of funnel): **reviews**,
  **how-to**.
- **Difficulty score (Ahrefs, por keyword):** estima qué tan difícil es rankear. **Pero un score alto NO
  siempre es difícil de verdad** — uno de los errores más comunes.

## Cómo verificar el difficulty score (no creerle ciegamente)

- Priorizá primero las de **difficulty bajo con tráfico decente**. Pero para las **keywords importantes**
  (no se puede con todas), **verificá** el score.
- **Cómo:** mirá el **top 10 en Ahrefs** (no en Google — **Ahrefs scrapea genérico, sin personalizar**).
  El algoritmo **promedia los links del top 10** y no es muy inteligente: **1–2 sitios grandes/importantes
  con muchos links inflan el promedio**. Si entre los 10 ves sitios con **DR bajo y 0–2 links** rankeando,
  **hay oportunidad** ("si ellos entraron, yo también") — el score está distorsionado por esas 1–2 marcas.
  Si todos son DR alto con muchos links, la dificultad es real.

## Armar la lista de keywords (de dónde salen)

1. **Competidores directos** → Ahrefs → sección **"Top pages"** (prioriza por tráfico): qué páginas son y
   por qué keywords rankean; mirá también sus keywords. Hacelo con los **grandes conocidos** y con
   **chicos que tengan tráfico significativo** (si un chico no tiene tráfico, **no está haciendo SEO** →
   ignoralo). Ojo: las marcas grandes a veces tienen mucho tráfico pero es **branded**, no SEO de
   categoría.
2. **Alternativas (no competidores directos):** ¿qué **sitios** captan ese tipo de tráfico? Comunidades,
   blogs, sitios **que ni siquiera son software**. En **nicho** es fácil pensarlos (ej. una app para
   salespeople → sitios que atraen salespeople). En **horizontal** es más difícil: para **SignWell**
   Ruben pensó en **use cases relacionados** — el espacio legal, documentos legales, **qué pasa antes y
   qué pasa después** de firmar — y qué tools/webs/comunidades sirven a eso. (Para el ejemplo **Bump CRM**
   horizontal: salespeople, sales managers, news/community sites con tráfico SEO.)
3. **Términos propios:** los que se te ocurren tipeando.
4. **Review sites (subestimado):** G2 y Capterra rankean muy bien por categoría. Buscá "<producto> G2" o
   "<producto> Capterra", entrá a la review y **subí un nivel de directorio** → ahí está el **nombre de la
   categoría** (ej. "email marketing software", "CRM software"). Meté esa categoría en Ahrefs y mirá qué
   pasa.

## Analizar (export a spreadsheet)

- Exportá de Ahrefs a una planilla: **keyword · difficulty · CPC · volume** (se puede a mano, pero es un
  dolor). Mirá con **varias vistas**:
  - **Por CPC desc** → **proxy de buyer intent**: dónde hay intención de compra con tráfico ok y
    difficulty no demencial. Empezá a cavar ahí.
  - **Por volume desc** → dónde están los grandes y si hay oportunidad (según difficulty).
  - Las keywords que **te gustan mucho aunque tengan difficulty alto** → **verificá el top 10** (paso de
    arriba) por si el score está inflado.

## Correr la matemática (la lente de validación)

- La pregunta es: **¿cuánto necesito vs cuánto hay disponible?** Depende de **tu sitio** (dominio nuevo =
  más difícil y lento; dominio con algo de antigüedad/links = head start) y de **tu precio y goals**.
- Buscás **pockets / un punto de entrada**: un par de términos de **volumen decente y baja competencia**
  para arrancar, y un **camino hacia más tráfico**.
- **Ejemplo de embudo (Ruben):** llegar (en ~6–12 meses, no de un saque) a ~**10.000–20.000–30.000
  visitas/mes**; **1% a trial** → 200 trials/mes; **15–20% de trials a pago** → ~30 clientes nuevos/mes.
  A **$20/mes** = ~$600 MRR/mes nuevo. ¿Alcanza? **Depende de los goals.**
- **Ponderá la probabilidad** de lograr ese tráfico (si nunca hiciste SEO, bajá el optimismo).
- **Precio alto → necesitás menos tráfico** (y suele venir con **menos buyer-intent** y **ciclos de venta
  largos**: de 1 día a 6–12 meses en gov/educación/construcción, con demos). **Precio bajo / B2C →
  necesitás muchísimo volumen.** Por eso **no hay fórmula** "si el volumen está por encima de X, hacelo":
  el mismo embudo es un negocio distinto a $20/mes que a $300/mes.
- **Lo que buscás NO es un "quizás funciona" al límite.** Con datos tan tempranos buscás el **"no"
  obvio** ("no hay forma de que esto alcance lo que necesitaríamos"). Si es marginal, no lo fuerces.
- **No lo veas como todo-o-nada (Ruben):** SEO puede ser **suplementario** — uno de tus canales más
  grandes, pero no el único. (Rob: si llega a la mitad del crecimiento, el resto va por cold outreach,
  integraciones/partnerships, y los **otros ~18 enfoques** de marketing.)

## Banderas rojas (alejate)

- **Nadie busca** la categoría **ni** los problemas asociados → en SEO no hay de dónde agarrarse.
- **Demasiados competidores cubriendo todo**, incluso las **rutas indirectas** — porque la gente piensa
  SEO = contenido/content marketing y deja afuera **free tools, templates y otros recursos** (que dan más
  trabajo que pedirle un blog post a ChatGPT). Si los competidores cubren hasta eso, el **ratio no cierra**.
- **SaaS-para-SaaS** (tu cliente son otras SaaS): malo para SEO — **súper competitivo**, **poco volumen
  real**, y todos van por los mismos términos (los devs/indie hackers construyen para otras SaaS porque
  rascan su propia picazón y conocen el espacio). **Más oportunidad** en nichos "aburridos" poco atendidos
  (**senior living facilities, CEOs de construcción**).

## Ángulos cuando la categoría es competitiva (no todo es el "money term")

- Vas a querer rankear #1 por los términos de categoría (email marketing software, e-signature) pero son
  **súper competitivos**. Otros ángulos:
  - **Long tail (acota Rob, ej. Drip):** "email marketing software **GDPR compliant**", "**for Canadian
    companies**". Bajo volumen (a veces ni aparece en las tools, ~100/mes), pero **baja competencia +
    buena intención**.
  - **Free tools:** ⚠️ **un free tool es un SEGUNDO producto que también hay que marketear** — no "lo
    construís y vienen"; igual hay que conseguirle **links**. Ej. SignWell: **signature generator** (con
    dos entry points, typed signature y drawn signature) y uno en desarrollo para **firmar PDFs** (super
    competitivo, costó encontrar un camino para rankear).
  - **Templates:** ej. **contract/sales templates** → **segundo orden** (quien busca un sales contract
    después necesita **firmarlo**). **Volumen alto, conversión baja**, pero **menos competencia** que el
    money term. La **intención es difícil de cambiar**: podés encauzarlos al producto como next step si
    toda la experiencia lleva a eso, pero **no es fácil**.
- **Separá top-of-funnel de bottom al estimar:** templates/tools convierten **bajo** (~1%); términos
  pegados a buyer intent convierten **alto** (10–15% a trial, y mejor a pago). No los promedies.
- En todos los casos: **seguís necesitando links y promoción.** Nada es automático.

## Acortar el feedback cycle (puente a ejecución)

- **Empezar SEO con anticipación:** Ruben hizo SEO de **contracts/templates 12–18 meses antes** de tener
  el producto SignWell, para llegar al lanzamiento con tráfico ya construido. (Lo hace **poca gente**,
  pero se puede.)
- **Google Ads de prueba:** para **keywords importantes pero competitivas** (donde el esfuerzo SEO sería
  grande y querés saber si vale la pena), **bidealas** y llevá a una landing. **~70% de las veces** el
  comportamiento se parece al del orgánico (difiere porque otra gente clickea ads). Sumá **encuestas tipo
  Hotjar** para entender **quién** llega y su comportamiento **sin** necesidad de que conviertan. Buscá
  siempre **una señal temprana** que te ahorre esperar 12 meses.

## Caveat de honestidad

- No hay fórmula "si está por encima de X, hacelo". La validación es **difusa**: parte experiencia, parte
  **gut feel**. **Conocé tu sesgo:** si tendés a **hablarte para NO avanzar** ("todo está tomado, no hay
  buenas ideas"), inclinate un poco hacia lo **incómodo** y mirá esa oportunidad igual; si tendés al
  optimismo, **descontá**. Sabé qué riesgos estás tomando cuando vas por algo más difícil por gut feel. Y
  **nunca decidas solo por los números** de una tool.
