# Entrevista: "Cómo construir un MVP de código (qué incluir y qué dejar afuera)" — Derek Reimer (SavvyCal)

> **Qué es esto.** Transcript (limpiado y organizado por tema) de una sesión del **mismo curso de
> Rob Walling** (SaaS Launchpad). Es una conversación entre el host (Rob) y **Derek Reimer**,
> fundador de [SavvyCal](https://savvycal.com) y ex-CTO de **Drip** (lo construyó con Rob). El tema:
> es la **continuación** de la lección de MVPs de Rob — esa cubre los 3 approaches (human automation
> / no-code / code); esta entrevista **baja al detalle del approach de CÓDIGO**: una vez que decidiste
> (y justificaste) construir software custom, **qué features incluir y cuáles dejar afuera, cuánto
> pulir, qué stack, cómo testear y cómo lanzar**. Derek construyó MVPs muy buenos (Drip) y uno
> sobre-construido (Level), así que habla desde los dos lados.
>
> **Atribución:** es **material del mismo curso** que el resto de los comandos (misma fuente/autoridad
> que los videos de validación de Rob Walling), presentado por Derek Reimer. Lo que está acá es **lo que
> dijeron en la entrevista**; el comando `/saas_build_mvp_tips_dev` lo convierte en un sistema guiado.

---

## Contexto: el sesgo del builder que hay que DESAPRENDER

- El builder que ama hacer **software pixel-perfect** tiene que entrar en un mindset **contraintuitivo**
  para construir un MVP. Hay que entender la diferencia entre "software completo" y "MVP".
- En la industria (Fortune 5000, agencias) **nadie construye MVPs** — se construye **software completo**:
  todos los edge cases, todas las features, todo terminado **antes** de shippear. Si venís entrenado así,
  tenés que ir **en contra de tus instintos / tu entrenamiento**. Hay que **desaprender** mucho.

> Punto clave para la evaluación: **"saber construir software completo" es un pasivo, no un activo,**
> a la hora del MVP. El primer trabajo del fundador-dev es reconocer ese sesgo en sí mismo.

---

## Los temas / decisiones

### Bloque A — Qué construir y qué NO construir (alcance)

#### 1. Drillá el CORE a través del stack — no te vayas a lo secundario
- Mantené el foco en **el objetivo del MVP** (probar una hipótesis). Las conversaciones y wireframes te
  llevan hasta cierto punto; el MVP es el paso siguiente para tener algo **tangible** (no vaporware).
- El foco va en el **"core job to be done"**: la **salsa secreta** que te diferencia, lo que hace que
  resuene en el mercado. Derek lo describe como **"drillar un core a través del stack"** y enfocarte
  **solo en esa pieza**.
- **No** te dejes deambular hacia partes **secundarias o administrativas**. Son **fáciles de construir**,
  y justamente por eso son una **tentación / procrastinación**: te hacen *sentir* productivo sin moverte
  hacia adelante.
- Costo oculto de construir lo secundario: **le agregás legacy** al producto y lo volvés **menos
  maleable**. El objetivo es quedar **lo más ágil posible** para responder al feedback de los primeros
  usuarios.

#### 2. La trampa de la procrastinación productiva (login, forgot-password, settings)
- "Sé construir una página de login, forgot-password y un settings screen → entonces lo construyo." Eso
  es el equivalente a **irte a Twitter/Reddit**: te hace sentir que avanzás, pero **no hace falta** y son
  **horas tiradas**.
- Lo difícil (el modelo de dominio, la pantalla compleja que nadie más tiene, la **salsa secreta**) es
  **mentalmente agotador** — requiere creatividad, iteración, "esto no es del todo, lo tiro y rehago".
  Por eso uno **escapa** a construir lo fácil. Resistí esa escapada.

#### 3. El MVP NO es estático — su tamaño depende de qué tan "amigables" sean tus primeros usuarios
- La **primera versión del MVP** probablemente **hace muy poco** y los primeros usuarios van a decir
  "le falta un montón". **Está bien**, siempre que esos usuarios sean **relativamente amigables**.
- **Cuánto tiene que tener tu MVP depende de qué tan amigables son tus primeros usuarios.** En Drip los
  primeros 5–10 usuarios **conocían a Rob personalmente** (Ruben Gomez, Brennan Dunn): podían mirar algo
  crudo, pensar "esto es un desastre" pero **igual darte feedback constructivo** ("falta esto, pensalo
  así") en vez de huir.

#### 4. Las dos formas de sobre-construir un MVP
1. **Sobre-ingeniería del código** = hacerlo "infinitamente escalable" desde el día 1. **No hace falta.**
   El MVP tiene que **operar y aguantar early customers**, nada más. *Pero* (matiz importante) **no lo
   escribas tan mal** que no se pueda extender después para manejar más carga.
2. **Demasiadas features.** No es solo el settings/billing/forgot-password — es construir un **v1
   completo** disfrazado de MVP. Con **1 usuario** (o 5 amigables) **no necesitás** ni la escalabilidad
   infinita ni features extra. Construir el **core con un twist** (ej: mejor UX), no un producto
   genérico completo.

> Ejemplo de Derek: un CRM. El core core de un CRM = una **vista Kanban**, toma datos de cliente, unos
> campos. No construyas "un CRM más" — construilo **con un twist**. Pero igual, con 5 usuarios amigables
> NO necesitás escalabilidad infinita ni features de más.

---

### Bloque B — Calidad del código, frameworks y tests

#### 5. Frameworks "batteries-included" → enfocás en tu dominio
- Hoy hay frameworks (**Ruby on Rails, Laravel, Django**) que te hacen **muy productivo** con un montón
  de defaults. Si te quedás con los defaults, el **boilerplate** queda resuelto y enfocás en lo que
  importa de **tu aplicación / tu dominio**.
- **No te metas todavía** en escalabilidad prematura ni en infraestructura de deployment. Los devs que
  vienen de empresas grandes preguntan "¿y cómo escala esto? ¿dónde está el logging para almacenamiento
  a largo plazo?" — hay **departamentos enteros** dedicados a esas piezas. **No te preocupes por nada de
  eso en un MVP.**

#### 6. Cortá en CUÁNTO construís, no en la CALIDAD del código
- "Quiero escribir **buen código**, no código de mierda por apuro." El corte va en **cuánto construyo /
  qué features / la escalabilidad**, **no** en la calidad.
- Que sea **escalable después**: dejá las cosas **stubbeadas** (ej: logging para más adelante). **No
  construyas legacy desde el día 1** — no querés un prototipo crappy que después esperás que sea tu v1.

#### 7. ¿MVP descartable o se vuelve tu v1? — escribí tests, pero no 100% coverage
- Dos escuelas: (a) MVP **totalmente descartable** (sandbox para probar ideas, después lo tirás y rehacés
  con tests); (b) lo morphás. **En la práctica casi nunca tirás todo y empezás de cero** — terminás
  morphando el código que ya tenés (¿por qué tirar todo el progreso?).
- Por eso: **escribí tests, pero NO busques 100% de coverage.** Testeá lo **esencial / el core**.
- Derek prioriza **tests de integración / full-stack** (que prueban partes completas del sistema) por
  encima de **unit tests nitty-gritty** de bajo valor. Ese es el balance para **escribir rápido** y poner
  código frente a usuarios rápido — el modo de operación de un startup temprano.
- El objetivo: un **core que puedas expandir**, y cuando lancen y empieces a cobrar, **agregar más tests
  y sentirte bien**, no empezar de cero ni tener miedo de deployar porque "todo se rompe".

> Honestidad de Derek: el "MVP descartable disciplinado" (lanzás, conseguís clientes, tirás todo el
> código y dedicás 3–4 meses a rehacerlo bien poniendo a todos en pausa) **no es para él**. Casi nadie
> lo hace de verdad.

---

### Bloque C — Qué podés lanzar SIN construir (los ejemplos de Drip)

> Regla general detrás de todos estos: estas cosas **pasan POCAS veces** en un MVP y se resuelven en
> **minutos a mano**, mientras que construirlas bien (validaciones, edge cases, UI) son **horas o días**.
> Ese diferencial es la barrera. Y **todas las horas suman**: "el delete tarda solo una hora" → pero
> todas esas horas compuestas a lo largo de los ciclos de feedback te corren el target **de semanas a
> meses**.

#### 8. Botones de delete
- En Drip **no había botón de delete** en la UI por **meses**. Creabas cosas pero no las borrabas desde
  la interfaz. **Sorprendentemente poca gente** lo pidió. Cuando alguien lo pedía por email, lo borraban
  **a mano en la consola/DB** (que para ellos era solo **setear un flag de status**, no borrar la fila).

#### 9. Sorting, búsqueda en grids
- **Sin sorting** en ninguna grilla. **Sin búsqueda.** Gente con 20–40 emails pedía "buscar por subject
  line" → "lo agregamos a la cola". Si **suficientes** lo pedían, lo construían. Esa era la regla.

#### 10. Billing engine
- Por **meses** Rob entraba **manualmente** a la interfaz de Stripe y clickeaba para cobrar a cada cliente.
  Calendar invites / boomerang emails como recordatorio porque eran **10 clientes**. Recién a los **40–50**
  clientes escribieron código (un **cron job**).
- Hoy Stripe tiene **payment links** y **billing portal**: generás un link 1-off, lo mandás, pagan, se
  cumple. Hay **mucho tooling no-code** para llegar lejos **sin escribir código** custom de integración.

#### 11. Password reset
- Si alguien olvida la contraseña, se resuelve **en la consola de dev**. Los frameworks modernos traen
  auth básica, pero **quizás ni vale la pena** gastar el par de horas / el día en cablear todo el flujo en
  el MVP inicial. (Y "es solo una hora" → **todas las horas suman**.)

#### 12. Formulario de self-signup
- Drip **no tenía signup self-service** hasta ~20–40 usuarios / **$3–4k de MRR**. El alta era manual:
  "Derek, andá a la consola, generá la cuenta, mandale el reset-password link". Todo a mano.

#### 13. Código de reembolsos — el ejemplo del "just-in-time"
- En cierto momento hubo que reembolsar a alguien. Como querían que **sincronizara** (webhook), Derek lo
  construyó **just-in-time**: un **botón en un admin console** que pega a la **Stripe API**. **~45 minutos.**
  Se construyó **cuando recién se necesitó**, para mantener todo en sync. **Just-in-time development.**

#### 14. Admin dashboards — Derek hoy es AÚN más agresivo en NO construirlos
- En Drip construyeron pantallas de admin dashboard, pero **post-MVP** (fase ya validada).
- Hoy en **SavvyCal**, todas las operaciones de **refund** siguen pasando por la **UI de Stripe**. Tienen
  un **atajo**: clic en un link dentro de un ticket de Help Scout → matchea por email → te lleva al
  customer record en Stripe → ahí hacés todo.
- Filosofía: **pensá en todas las etapas cómo escribir MENOS código.** Ese tipo de código (un admin UI
  para que soporte haga reembolsos) **lo podés escribir, pero tenés que mantenerlo.** Un **SOP** ("clic
  en el link → ver el record en Stripe → 3 puntitos → refund") evita ese mantenimiento.

#### 15. "Que puedas construirlo no significa que debas" (write less code)
- Cada cosa que construís, **la tenés que mantener**. Si Stripe cambia su API, agrega tax collection, o
  cambia cómo funciona la proration → **dejá que Stripe se preocupe por eso**, no tu código custom.

---

### Bloque D — La ÚNICA feature que Derek SÍ pondría en todo MVP

#### 16. "Ghost / login as user" (impersonation) — must-have desde el día 1
- Apenas tengas **autenticación** (que llega pronto, en cuanto la gente tiene cuenta), construí la
  capacidad de **loguearte como ellos** (ghost / impersonate).
- **Te ahorra tiempo desde el día 1.** Los usuarios reportan "me pasa esta cosa rara en esta página" → la
  capacidad de **ver exactamente lo que ven** es **invaluable** para diagnosticar bugs. Sin eso, ¿cómo ves
  lo que ven? ¿Un screencast? **No es lo mismo.**
- Matiz: si hay **data sensible**, podés meter un poco de lógica if-then para **redactarla** cuando un
  soporte está logueado. Pero la capacidad base de ver-como-ellos es indispensable.
- Es la **única** que Derek incluiría en **cada** MVP. (Aun con 5 usuarios que no te pagan: van a tener
  bugs, y necesitás diagnosticarlos vos.)

---

### Bloque E — Diseño y pulido (¿cuánto?)

#### 17. "Ya no existen los MVPs feos" — depende del cliente
- Frase que escuchó Rob: "la competencia es mucho mejor en diseño/estética; se acabaron los MVPs feos".
  **Es cierto pero depende.**
- Si construís para **realtors, peluquerías, CEOs de construcción** → **no notan la diferencia**. Importa
  la **funcionalidad** (qué hace, qué tan fácil es de usar), no que se vea como Linear.
- Si construís para **techies, fundadores, devs, la "elite de Twitter", gente de UX** → ahí **sí** lo
  notan ("eso es el default de Tailwind", "no puedo creer que uses esto"). Eso **siempre** fue así.
- El software **en general** está mejorando con mejor tooling, así que los MVPs **necesitan ser más
  usables** que hace 10–12 años — pero también hay **más templates y boilerplate** para lograrlo. "Todo
  sube."

#### 18. Estética ≠ usabilidad (separá los dos)
- Distinguí **pulido estético** de **usabilidad / UX**. Aun una industria "offline" (que no prueba
  productos todo el día) **quiere hacer un trabajo** sin perder tiempo peleándose con la UI, y poder
  **entrenar a su equipo**.
- Si no pueden **descubrir cómo usar** el producto, es un **roadblock** — y lo vas a **sentir temprano**
  mirándolos usarlo. **La usabilidad SIEMPRE importa.** El pulido estético, **solo si es tu value prop**.
- ¿Cuándo el pulido **sí** es el value prop? Ej: **Linear** (alternativa a Jira) — parte de su propuesta
  es "somos más lindos de usar" porque Jira tiene fama de clunky, así que invierten una barbaridad en
  diseño. Preguntate honestamente: **¿es eso parte de tu core value prop?** Si no, **arreglátela** con
  templates buenos.

#### 19. Recursos concretos para no-diseñadores
- **Refactoring UI** (del equipo de Tailwind): **práctico** (no teoría de arte), cómo hacer cosas que la
  gente **intuitivamente sepa usar**. Derek lo recomienda seguido.
- **Tailwind** como ecosistema (mucha energía hoy) + **Tailwind UI** / **Catalyst UI** (componentes
  pre-construidos) + themes que dropeás en el proyecto. "Si estás metido en el ecosistema notás que es un
  template de Tailwind, pero **a los clientes no les importa**." Históricamente, **Bootstrap** cumplía ese
  rol de "good enough".
- Si arrancás de cero y no sos diseñador: **empezá con Tailwind** + un template/tema → se ve **decente**
  out-of-the-box. Tailwind es **fácil de customizar** (a diferencia de muchos kits off-the-shelf, donde
  el dolor aparece al customizar).

---

### Bloque F — Elección de tech stack

#### 20. Los "big 3" + honorable mentions (para web apps)
- Recomendación 80/20 (no "la respuesta correcta" — hay guerras religiosas): **Ruby on Rails / Python
  con Django / PHP con Laravel.** Razones: **populares, ecosistemas vivos** (se parchean, se mejoran,
  libs modernas, buena docs, soporte), y **podés contratar devs** sin costos de nosebleed.
- **Honorable mention: Node.js** (popular; Rob menos cómodo, no le gustan los frameworks JS para backend).
- **Honorable mention de Derek: Elixir + Phoenix** (su favorito, similar a Rails) — pero **ecosistema más
  chico**, así que como consejo general gana "**enganchate al ecosistema más grande** que puedas y montá
  esa inercia" (más devs, más fácil contratar).
- **Anti-ejemplos** (no hagas): COBOL, ASP clásico → no encontrás devs.

#### 21. Backend-centric vs front-end-first
- Familia **backend-centric monolítica**: **Rails / Laravel** (y Django). Generan HTML server-side; la
  interactividad del front, históricamente, "escribí tu propio JS". Hoy **suman tooling** para fronts
  interactivos escribiendo las vistas en el lenguaje del backend.
- Familia **front-end-first**: **Next.js** (respaldo VC fuerte de **Vercel**). Popular con devs nuevos que
  arrancan por bootcamps de JS. Se acercan a ser full-backend, pero su lado server es **mucho menos
  maduro** que Rails/Laravel.
- Están **convergiendo** y se vuelve más confuso ("todos se venden como full-stack").
- **Postura de Derek (y Rob): bullish en los backend-centric.** JavaScript tiene **mucho flavor-of-the-week
  / churn**. Rails y Laravel son hoy **aburridos, estándar, rock-solid** — y eso es bueno.

#### 22. La regla que manda: usá el stack que YA conocés
- Si sos dev-founder (o tenés un early teammate construyendo), pedirle **aprender un framework nuevo** para
  el MVP **NO es el momento** para ese aprendizaje. **Priorizá lo que ya conocés.**
- Si venís de **Java / ASP.NET** u otro stack corporativo: en general **construí con lo que sabés** (la
  curva de aprendizaje es alta). **Downside honesto:** contratar devs después va a ser **caro**, y los que
  encontrás vienen de empresas grandes → tienden a **gold-plate / construir de más**. Sabelo de entrada.
  *Igual existen* SaaS bootstrapped multimillonarios en Java/ASP.NET (TinySeed financió varios en stacks
  ni mencionados acá).

> **Advertencia evergreen:** estas recomendaciones de stack **cambian con el tiempo**. Si ves esto 1–3
> años después, habrá shifts. Son recomendaciones **80/20**, no prescriptivas.

#### 23. (Aclaración para no-devs) qué es Tailwind vs el framework de backend
- **Tailwind** = la capa **visual / front-end** (renderiza tu CSS, estilos). Es un estilo de escribir CSS
  con utility-classes; al principio la gente es escéptica y después dice "soy mucho más productivo".
- Se usa **junto** a un framework de **backend / server-side**: Tailwind **+** Rails, Tailwind **+**
  Laravel, etc.

---

### Bloque G — El error de sobre-construir: Drip (bien) vs Level (de más)

#### 24. Drip — un MVP bien hecho (~3–4 meses, lanzamiento por fases)
- Feature count **bajo**, tests (pero no over-engineered ni diseñado para escalar infinitamente), y un
  **lanzamiento por fases**: 1 persona → 2 → 5 → 10, sacando bugs en el camino.
- Tiempo: ~**5 meses calendario pero a medio tiempo** → ≈ **3–4 meses full-time**.
- Rob considera que el MVP de Drip "terminó" cuando empezaron a emailear a 100–300 personas de la lista
  (ahí pasó a ser un **v0.9 / v1**). El v1.0 los llevó a **$8–10k MRR** (gran parte por la audiencia/lista
  de Rob), y después **se estancaron** → 8 meses de customer development + pivot. **Que el MVP funcione
  NO garantiza el éxito.**

#### 25. Level — el MVP sobre-construido (~9 meses)
- App de Derek después de vender Drip: **plataforma de comunicación de equipos** (compitiendo con Slack),
  con twist: **asíncrona**, con **inbox** (entre email y chat).
- **Errores que cometió:**
  - Entró con **muchísimos supuestos fuertes** sobre cómo "debía ser" el producto, asumiendo que todos ven
    el mundo como él. (No está mal tener supuestos — el error es **no tratarlos como hipótesis a testear**.)
  - Tomó el **interés** de la lista de emails como **validación suficiente** y se lanzó a construir "porque
    tengo una idea fantástica".
  - Saliendo de un **codebase legacy** (Drip, años), sintió el subidón **greenfield**: "ahora hago todo
    bien y **juego con tecnología nueva** que quería probar". Eligió un **framework de front-end nuevo**
    cuyo **ecosistema era inmaduro** → terminó **construyendo a mano** cosas que con React (más popular)
    sacaba de un package. Cayó en **sunk-cost fallacy** y siguió.
  - **No mostró nada por 9 meses.** Una plataforma de comunicación es un lift grande, pero igual debería
    haber **previsto** una primera versión que **no fuera** una plataforma completa — solo **previewear las
    opiniones iniciales** (el inbox, las notificaciones async/atenuadas vs push en tiempo real) frente a
    clientes potenciales para ver **si resonaba**.
  - **Riesgo de adopción** no validado: aun si a la gente le gusta el producto, **¿lo adoptan a nivel
    organización?** Ese era el riesgo clave a validar durante el proceso.
- Comparación: Drip ≈ **3–4 meses full-time**; Level ≈ **9 meses** (≈ el doble). No es que "todo buen MVP
  son 4 meses", pero **9 meses sin que nadie lo vea es muchísimo**. Parte del tiempo se fue en **aprender
  un lenguaje/stack nuevo** — exactamente lo que el Bloque F dice **no** hacer.

---

### Bloque H — Cuándo está "listo para lanzar": el lanzamiento por fases

#### 26. No sabés cuándo está listo → lanzá por fases ("phased launch")
- Pregunta "¿cuándo está listo el MVP para lanzar?" → respuesta: **no lo sabés.** **No** emailees de golpe
  a los 1.000 de tu lista (catastrófico).
- Rob lo llamaba "**slow launch**", ahora "**phased launch**" (slow tiene connotación negativa). Lanzás
  **en fases**:
  1. **1 persona amigable** muy metida que te diga la verdad. (Ruben fue el primero en Drip: "esto no hace
     suficiente" → "¿qué le falta?" → lista concreta.)
  2. Construís **exactamente lo que pidió** (2–3 semanas), vuelve a probar. (Ruben no pudo: problemas con
     unsubscribes / conexión de mail → **Drip no encajaba en su use case**.)
  3. **Pasás a la siguiente persona** (Brennan). Iterás un par de meses.
  4. Recién ahí: "creo que estamos listos para emailear a los **primeros 50–100**".
- **Sé muy sensible a quemar tu lista** (5.000 o 1.000 personas) con algo que **no tiene la funcionalidad
  ni el pulido**. ¿Lanzar en semanas/meses? Sí. ¿En 5 años? Obvio que no — sé razonable.

#### 27. Reclutá deliberadamente a tus primeros testers
- Es **difícil** conseguir gente interesada en ayudarte **a escala** (cierto incluso en SavvyCal, producto
  maduro con muchos clientes). Por eso: **reclutá deliberadamente** a quienes les das tanto poder de
  **dirigir el producto**.
- Es todo **hipótesis educadas**: "nuestra apuesta educada era que Ruben sería buen candidato" → le
  dedicaron tiempo **limitado** → al ver que no era óptimo, **pivotaron a la siguiente** persona apostada.
- Si en cambio **blasteás a 100** y solo 3 random prueban y mandan feedback **contradictorio**: ¿qué hacés
  con eso? ¿el "3 de 100" es rechazo o solo gente ocupada? **Ruido inútil.** Por eso la fase 1 es **1
  persona elegida a dedo**, no un blast.

---

## TL;DR — los principios que el comando aplica

1. **Desaprendé el "software completo".** Saber construir todo es un pasivo en el MVP.
2. **Drillá el core** (la salsa secreta) a través del stack; **no construyas lo secundario/administrativo**
   (login, settings, forgot-password) — es procrastinación productiva.
3. **No sobre-ingenierices para escala** ni metas features de más. Pero **no escribas código basura**:
   buen código, **menos** código.
4. **Tests sí, 100% coverage no** — priorizá integración/full-stack sobre unit tests nitty-gritty.
5. **Lo que se hace a mano POCAS veces NO se construye:** delete, sorting, search, billing, password reset,
   self-signup, refunds, admin dashboards. Resolvé en consola / Stripe UI / SOP. **Construí just-in-time.**
6. **La única feature must-have en todo MVP: "login as user" (ghost/impersonate)** para diagnosticar bugs.
7. **Usabilidad SIEMPRE; pulido estético solo si es tu value prop.** Conocé a tu cliente (techie vs offline).
   Tailwind + templates + *Refactoring UI*.
8. **Stack: Rails / Django / Laravel** (Node.js / Elixir-Phoenix honorable mentions). **Backend-centric.**
   **Usá lo que ya sabés** — no aprendas un stack nuevo para el MVP (el error de Level).
9. **No mostrar nada por 9 meses = sobre-construir** (Level). Drip ≈ 3–4 meses full-time = bien.
10. **No sabés cuándo está listo → lanzá por fases:** 1 tester amigable elegido a dedo → construí lo que
    pide → siguiente → recién después 50–100. **No quemes tu lista.**
