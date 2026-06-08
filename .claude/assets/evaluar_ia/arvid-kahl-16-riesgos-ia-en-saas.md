# Entrevista: "16 riesgos de incorporar IA a tu SaaS" — Arvid Kahl (PodScan.fm)

> **Qué es esto.** Transcript (limpiado y organizado por riesgo) de una sesión del **mismo curso de
> Rob Walling** (SaaS Launchpad). Es una conversación entre el host del curso y **Arvid Kahl**
> (fundador de [PodScan.fm](https://podscan.fm), autor de "The Embedded Entrepreneur" y "Zero to Sold",
> [tbf.fm](https://tbf.fm), @arvidkahl en X). El tema: **antes** de "espolvorear un poco de IA" sobre
> tu SaaS para crecer el MRR, pensá las **consecuencias**. Arvid corre PodScan (transcribe y analiza
> *todos* los podcasts del mundo en tiempo real) sobre APIs de IA a escala 24/7, así que habla desde
> las trincheras.
>
> **Atribución:** es **material del mismo curso** que el resto de los comandos (misma fuente/autoridad
> que los videos de validación de Rob Walling), presentado por Arvid Kahl. Lo que está acá es **lo que
> dijo en la entrevista**; el comando `/saas_idea_evaluar_ia` lo convierte en un sistema de evaluación.

---

## Contexto: dónde cae PodScan en el espectro de IA

Arvid **no** entrena modelos fundacionales (eso cuesta cientos de millones: OpenAI, Anthropic, Google,
Meta). Está cerca del lado **"wrapper"**: usa APIs de foundation models (OpenAI sobre todo) con buenos
prompts, a veces con embeddings/datos extra. Deliberadamente evita poseer hardware ("edificios llenos
de placas de video con alarma de incendio") porque es un negocio bootstrappeado. Su razonamiento: aun
con un nicho híper específico y datos infinitos, lo que construirías vos sería **peor** que el foundation
model — y ellos igual usan tus datos para entrenar. Dos usos en PodScan: **transcripción** (audio→texto,
ya con una capita de IA de texto que corrige en contexto) y **análisis** (resumen, quién habla, temas,
demografía estimada del oyente).

> Punto clave para la evaluación: **el espectro va de "wrapper de ChatGPT" (solo un prompt a una API)
> a "foundation model propio" (millones de dólares).** Casi todo bootstrapper vive cerca del wrapper.
> Ubicá tu solución en ese espectro antes de evaluar riesgos.

---

## Los 16 riesgos / trampas

### Bloque A — Operativos y de costo (1–4)

#### 1. Prevención de abuso (abuse prevention)
Las APIs cobran **por token** (entrada + salida): prompts más grandes y respuestas más grandes = más
plata. El abuso es facilísimo: un cliente, por negligencia o **intencionalmente para hacerte daño
financiero**, puede pegarle a tu feature de IA cientos de veces por minuto. Sin safeguards, esto cuesta
**cientos de dólares por hora** — para un bootstrapper, **fundir el negocio en un día o dos**.
- **Mitigación (en tu app):** rate limiting agresivo en cualquier cosa que toque IA. Ej: un chat que
  genera algo interno → 2–5 usos por minuto máximo. Si alguien lo usa 10–15 min seguidos, no es uso
  normal → notificación.
- **Mitigación (en la plataforma):** seteá un **límite diario de costo** en OpenAI/Anthropic, bajo al
  principio (vas a ajustarlo con los spikes). Si pagás 20x lo de un día normal, algo está mal: o tu
  propio código bugueado, o un usuario abusando.
- "Se siente como plomería, código desperdiciado" — pero sin esto te exponés a la ruina. **Buena
  noticia:** la IA lo escribe bien (hay 20.000 implementaciones de rate limiting en los datos de
  entrenamiento). Mejor que tu "primera vez pensándolo".

#### 2. Perder acceso a tu plataforma de IA (platform risk)
Riesgo de plataforma clásico (como cambiar de proveedor de email), pero acá hay **pocos players** con
API a escala. Si OpenAI **deshabilita tu cuenta**, estás liquidado: semanas peleando para que la
reinstalen, o ban directo. Y puede no ser culpa tuya — puede ser algo que **un cliente tuyo** hizo a
través de tu plataforma (les pasás datos crudos), que les flageó la cuenta para review → baneada 2–3
días. "No tengo buena solución a esto." Si abrís un sistema de IA a tus clientes y pueden meter
cualquier palabra, con suficientes idiotas vas a tener problemas que no podés filtrar antes de que
lleguen a los servidores de la plataforma.
- **Sub-riesgo: cambios de precio arbitrarios.** Nada está escrito en piedra. Anthropic con Claude 3.7
  lo hizo **4x más caro** que 3.5. A veces bajan (a Arvid OpenAI le bajó a 25% → 4x más uso al mismo
  costo), pero **puede subir**. La economía interna de estas empresas no es clara y está muy subsidiada
  por funding, no por plata de clientes. No tenés control.
- **Sub-riesgo: model drift.** Empezás con `o4-mini` versión de febrero; en marzo lo actualizan un
  poquito (training data, ajustes) y los resultados cambian sutilmente. **Tus clientes lo notan** aunque
  vos no cambiaste nada. La única forma de controlarlo es self-hostear el modelo (AWS Bedrock/SageMaker
  — caro y tampoco garantizado, otra capa de abstracción) o LLM local en GPU (no tan performante, no
  entran los modelos grandes; más privacidad pero mucho menos performance). Los LLM locales tampoco son
  solución a escala. **Te vas a sorprender de cuánto afectan tu bottom line cambios diminutos en
  calidad y costo.**

#### 3. Vendor lock-in (no es "solo cambiar de modelo")
"Es solo un prompt de texto, lo cambio al otro" es **ingenuo**. Hay un protocolo común (OpenAI fijó el
estándar de cómo hablar con estos servers: chat completion, imágenes), pero hay **matices en los
prompts**: cada modelo se entrenó con un estilo de prompt. Los modelos de Meta (Llama) usan ciertos
tokens XML para denotar system prompt / usuario / inicio de respuesta; eso difiere mucho de lo que
espera DeepSeek o de lo que espera OpenAI, y hasta Claude responde distinto a ciertos prompts.
- **Fine-tuning empeora el lock-in:** podés tunear un modelo con tus datos (más confiable/efectivo),
  pero eso **siempre pasa en la plataforma de otro** y **no hay estándar para mover un modelo tuneado**
  a otro lado. Si querés moverlo, tenés que re-tunearlo allá, con datos posiblemente distintos porque el
  foundation model es distinto. No hay estándar de compatibilidad para mover modelos.
- **Mitigación:** usá un **AI SDK** (existen para los lenguajes/frameworks populares), NO el SDK de
  OpenAI ni el de Claude directamente. El AI SDK te deja **cambiar el modelo** y hace el reformateo que
  haga falta para resultados equivalentes.
- **Corolario — outages/fallback:** las plataformas de IA **no son tan estables** como AWS EC2. Arvid,
  a escala (24/7, miles de requests para cientos de clientes), recibe **muchísimos 502 / 408 / errores
  raros** porque despliegan todo el tiempo y "explotan". Él tiene un **fallback a LLM local** (Llama 3.2
  en el server con GPU) que hace el trabajo si no puede conectar con OpenAI: no tan bueno, pero no
  explota el flujo. Está trabajando en switchear a **otro proveedor** ante fallas — pero eso implica
  lidiar con la diferencia de modelos: para Llama tuvo que **reescribir el prompt** (dos funciones
  distintas en el código, prompts parecidos pero distintos). "No hay un estándar unificador; lo tenés
  que resolver vos."

#### 4. Complejidad del conteo de tokens (token counting)
Cada modelo **cuenta tokens distinto**: para algunos un token es una palabra, para otros parte de una
palabra, para otros varias letras. Nunca sabés exacto cuántos hay porque lo determinan al ingerir tu
data. Hay **aproximadores** para pre-calcular (Arvid los usa para ver si pega el context limit).
- **Implicancia de costo:** tus 20.000 tokens acá pueden ser 30.000 allá → la diferencia de precio que
  creías genial juega en contra. Y cambian precios todo el tiempo. "Es el lejano oeste."
- **Implicancia de context limit:** todos tienen límite. Un episodio de Joe Rogan puede ser cientos de
  miles de tokens, pero Claude tiene ~200.000. A veces hay que **partir el transcript en dos**, analizar
  dos veces y mergear, solo por el tamaño. Hacé la matemática.

### Bloque B — Observabilidad y control (5–8)

#### 5. Ceguera de monitoreo (monitoring blindness)
No sabés bien qué hacen tus clientes ni si tiene un efecto deletéreo en los resultados. Con SQL
injection te das cuenta rápido (se rompe todo). Con IA hay **prompt injection** que puede disparar un
**tool call** que no pensabas que podían llamar, y ese sistema de IA — al que quizá le diste acceso a tu
DB o (dios no quiera) a datos de pago — responde con info que nunca deberían haber tenido. Y **no lo
ves**, porque pasa en la plataforma de otro. Tu cadena de observabilidad (request→finish) es sólida
mientras todo está en tu server; cuando algo "mágico" pasa en otro server y vuelve (o va directo al
cliente), no llegás a trackearlo. Las plataformas **no dan buen tooling de insight** (no hay un APM con
esta data): ellos infieren rápido, te mandan el resultado y te facturan por token. Ese es su modelo.
- **Sub-problema: no hay version control para prompts.** Querrías versionar prompts y ver qué versión
  dio qué resultado — **no existe** si no lo trackeás vos en tu código (no alcanza con tenerlo en un
  `if` en la DB). "MCP surgió porque la gente lo quería; cuando queramos version control de prompts y
  resultados, también va a aparecer." Tiene que madurar. (Comparación: el web dev del 97/98 — sin
  monitoreo, logs crudos, sin version control, sin unit tests.)

#### 6. Sin control sobre system prompts secretos
No sabés qué prompts les metieron los que entrenan/operan el modelo. Ejemplo público: el lío de Grok /
Sudáfrica — parte del system prompt estaba **políticamente influenciado** para responder ciertos temas
de cierta forma. Ejemplo propio de Arvid: en PHPStorm (su IDE) el autocomplete por IA le genera listas
para `age:` y `purchasing power:`, pero al tipear `gender` → **nada**. Hay un system prompt en la cadena
("cuidado al responder sobre género") que devuelve un 401 silencioso. **No puede autocompletar UNA
palabra** en su propio editor. Para otro habrá una buena razón; para tu uso alternativo te rompe el 5%
de las cosas y **no sabías que ese system prompt estaba ahí**.
- Esto **cambia con el tiempo:** quizá mañana no importa el género pero no podés criticar a cierta
  empresa/su dueño. Casi imposible de monitorear; una vez que sabés qué es, reformulás y de repente
  funciona.

#### 7. Sesgo inherente de los modelos (inherent bias)
Los datos de entrenamiento, los system prompts, el feedback de la gente → crean un modelo que **refleja
los sesgos humanos** del contenido de internet. Hay distorsiones. Para Arvid esto a veces es **útil**:
en PodScan estima demografía (edad, género, poder adquisitivo del oyente) **usando** el sesgo del modelo
— le da un transcript de "Call Her Daddy" y el modelo sabe, por foros/redes, que lo escuchan más
mujeres. Es todo guesstimación, pero sirve.
- **Pero** si trabajás con grupos **subrepresentados** o propensos a ser estereotipados, ese sesgo
  siempre está. Si lo usás para forecasting de mercado, va a "pensar como la mayoría piensa el mercado"
  (lo que ingirió).
- **Mitigación:** o lo usás explícitamente (dejando claro de dónde viene), o **prompteás contra el
  sesgo**: pedile en el prompt tomar una **visión multi-perspectiva**, "des-sesgar" la respuesta. Los
  modelos *thinking* recientes son buenos viendo su propio sesgo; los viejos/baratos no tanto, pero
  instruir "sé menos sesgado" mejora. Si no, estás regurgitando posts de Reddit.

#### 8. Prompt injection vía uploads de usuarios
Riesgo general si pasás los prompts tal cual. La gente puede subir un archivo o pegar texto con un
system prompt adentro. Existen **"god phrases"** (frases que la máquina toma con mucha más fuerza que
todo lo demás), a veces no intencionales — parte del proceso de entrenamiento: decís cosas raras y las
siguientes líneas se toman como un system prompt por encima del system prompt, y nadie sabe por qué. Una
vez que las encuentran existen como la escena "cracker" del prompting. Si las usan, pueden — vía tool
calling o respuestas raras que entran a tu data — **arruinarte la data**.
- **Mitigación:** las instrucciones que seteás **no son necesariamente lo que se ejecuta**. Sé
  extra-cuidadoso con la data que recibís de vuelta y cómo la manejás.

### Bloque C — Calidad del output (9–10)

#### 9. Alucinaciones cuando faltan datos
"Los LLM son máquinas extremadamente buenas para hacernos gaslighting." Su punto es **adivinar el
siguiente token más probable** que aparezca al que pregunta y le haga creer que tiene razón — no piensan,
no son inteligentes. El ~95% del tiempo eso coincide con la verdad. Si **no tienen data real**, toman su
mejor guess. A veces eso es lo que querés (bias para extraer demografía nebulosa); pero si pedís "nombrá
las 4 personas de este episodio" y hay **3**, ve 4 y en la persona 4 dice "y entonces apareció Michael
Jackson" porque a la gente le encantaría.
- **Mitigación 1:** sé explícito — "**si no tenés data, respondé con valor null**". Tiene que ser parte
  del prompt. "Para cualquier cosa de la que no estés seguro, respondé null."
- **Mitigación 2 (truco buenísimo):** pedile **primero** una **probabilidad/likelihood** (0 a 1) de que
  su resultado sea creíble, **antes** de la respuesta. A veces es 0.8, a veces 0.1 — y eso ya influye lo
  que pone (si la likelihood es baja, pone null). **El orden importa:** si pedís la respuesta primero y
  la likelihood después (error que Arvid cometió al principio), te da una respuesta muy creíble y después
  inventa una razón para que sea "aceptable". Likelihood/razón **primero**, respuesta **después**.
- Darle al cliente la indicación de que esto es **generado por IA**: está bien, ellos saben lo difícil
  que es la data real; aceptan un guesstimate 80/20 **mientras no se lo vendas como data real**.

#### 10. Usá structured outputs (JSON) para todo lo no conversacional
Structured output = pedir la respuesta como **JSON/XML** en vez de texto libre. Hasta hace ~1 año no era
opción: tenías que instruir "dame un JSON" y empezaba con "acá está el resultado:" + el JSON, y a veces
se olvidaba de cerrar una llave. Desde que integraron structured output en casi todos los modelos
grandes, **no hay razón para no usarlo**: te **garantiza** JSON válido (puede tener basura adentro, pero
es JSON parseable) → no desperdiciás plata en un JSON roto que no podés usar.
- Arvid lo recomienda **para todo, incluso conversaciones**: en un chatbot, no tomes texto plano — pedí
  structured output con el mensaje + **metadata** (ej: likelihood de necesitar un humano, user ID, info
  extra). Structured outputs además **reducen** el riesgo de pagar de más por divagar: si es JSON, sale
  prístino.

### Bloque D — Relacionales y legales (11–16) — "lightning round"

> Arvid los enmarca como "depende": como decidir cuándo comprar un seguro o formar una LLC. Temprano,
> con solo una idea, no obsesionarse — pero conocerlos.

#### 11. Riesgo relacional (IA entre vos y el cliente)
El menos obvio: poner una IA (ej: chatbot de customer service) entre vos y tus clientes te **roba la
mejor oportunidad** de construir una relación que vaya más allá de lo transaccional. Como founder chico,
ese chat es tu chance de preguntar por qué usan el producto, qué quieren, qué features necesitan;
mostrarte ("soy el founder, estoy acá para vos"), convertirlos en evangelistas. Internamente la IA es
genial; **para la conversación con el cliente, Arvid NO la usa.**

#### 12. Decepción / uncanny valley / mala gestión de expectativas
Una vez que implementás IA, la gente se acostumbra y espera que esté **24/7** y con calidad **humana**.
Cuando aparece lo "casi bien" (uncanny valley — "esta data no debería verse así / esto se ve demasiado
artificial"), lo **odian**. "Si esperan bueno y reciben casi-bueno, lo odian; si esperan malo y reciben
malo, está bien." Es **gestión de expectativas**. No la uses de forma que después tengas que lidiar con
ese fallout.

#### 13. Exposición de privacidad de datos
Si subís algo a OpenAI, prácticamente **cedés** el contenido. Aunque hagas opt-out, ¿quién sabe? Podrían
usarlo para verificación, para entrenar el próximo modelo. Por eso muchas empresas **B2B enterprise** no
tocan IA: no saben dónde aterrizan sus secretos. **No mandes** memos internos ni data de pago de tus
clientes enterprise a OpenAI solo para un resumen lindo — no es smart. Y pueden pedirte
**contractualmente** abstenerte. Para esto, **IA local** (cluster propio / AWS en facility segura) es
buena idea.

#### 14. Gaps de cumplimiento regulatorio (compliance)
Las plataformas **no son standard-compliant**, y los resultados que generan tampoco. No hay check de esto.
HIPAA, SOC, GDPR: lo que se genera **no se mira** para eso (normalmente compliance lo hacés *mientras*
creás la cosa; acá no la creás vos, no llegás a mirarlo). Mientras no haya garantía de compliance, si vos
sos compliant y **vendés** compliance, puede ser un problema grande. "Odio hablar de compliance, me aburre
a las lágrimas, pero es enorme en cuanto usás IA a escala."

#### 15. IA a escala — el prompt NO es un moat
Todos pueden usar estas cosas. Tenés ventaja **hasta que** los demás también la usen. "Los prompts son
como las ideas" (lo de ideas vs ejecución): tener un prompt no significa que tengas algo — otro puede
tener el mismo prompt y ejecutar mejor. Los modelos son cada vez más baratos y disponibles (local,
open source gratis). **Si tu único moat es tu prompt, tenés un problema.** Necesitás construir relaciones
con clientes y algo **encima** del prompt.

#### 16. Atrofia de habilidades (skill atrophy)
Si abusás, tus devs **ya no saben programar** (solo instruyen a la IA), o tus clientes pierden la skill
para hacer su trabajo. El mayor deal para devs: "no es que ame escribir código, amo **entender** qué
hace. Si me olvido cómo escribir código que hace lo que quiero, ¿cómo juzgo el código que escribió la IA
para ver si hace lo que pretendía?" Te volvés **dependiente de la IA** — riesgo en tu negocio, en tus
clientes y en todos ahora mismo. No hay buena solución, pero combinado con la **dependencia de
plataforma** (#2) puede ser desastroso rápido: la apagan → "¿cómo hago mi trabajo? Ya no sé programar."

---

## Cierre

Arvid arma esta lista desde "años con la IA hasta los codos". Su recomendación de prioridad: el **#1
(prevención de abuso)** sí o sí hay que construirlo desde el inicio (y la IA te ayuda a escribirlo). El
resto son cosas para **estar al tanto**: quizá nunca pegues con el del system prompt secreto, pero ahora
lo sabés. No gastes 3 meses resolviendo todo upfront antes de mirar — pero tenelos en el radar a medida
que construís. Y donde tenga más control (su podcast/YouTube en tbf.fm) está el lugar con **menos
problema de dependencia de plataforma**.
