# Video: "Planificar y construir tu MVP — los 5 pasos de Rob Walling"

> **Qué es esto.** Transcript (limpiado y organizado por tema) de una lección del curso de
> **Rob Walling** (SaaS Launchpad) sobre **planificar y construir tu Minimum Viable Product (MVP)**.
> Es la misma fuente/autoridad que el resto de los videos de validación de Rob Walling usados por
> los demás comandos. El comando `/saas_build_mvp_5pasos` lo convierte en un proceso guiado paso a paso.
>
> **Atribución:** lo que está acá es **lo que dijo Rob en la lección**. Lo que el comando agregue por
> fuera de la lección se marca inline con *〔no está en la lección〕*.

---

## Qué es un MVP (según Rob)

- El término **MVP** lo acuñó **Frank Robinson (2001)** y lo popularizaron **Steve Blank** y
  **Eric Ries** en *The Lean Startup*. La **M es de minimum**: lo **mínimo** que tenés que construir
  para tener un producto **viable** que mostrarle a clientes.
- En muchos casos **un MVP NO es software**, y **normalmente NO es una versión más simple de tu
  producto final**.
- Definición operativa de Rob: **un MVP es tu próximo paso más chico para validar el supuesto MÁS
  riesgoso** que tenés sobre tu producto. (Sabe que esto no encaja con la definición "oficial", pero
  en las etapas tempranas el MVP **es** tu siguiente paso.)
- Por eso un MVP puede ser:
  - **Conversaciones** con tus prospectos.
  - Una **landing page** (¿puedo traer tráfico? ¿a alguien le interesa? ¿se anotan?).
  - Un **Google Sheet** (solo, o atado a Make/Zapier → solución **no-code**).
  - Un **producto entregado por "human automation"**: un humano (vos, o un asistente virtual)
    haciendo manualmente lo que algún día quizás haga el código.
- El supuesto riesgoso puede ser sobre: **qué problema** resolver, si **a alguien le importa** ese
  problema, si **podés traer clientes**, o si **realmente podés construirlo** (esto último casi nunca
  es lo más riesgoso).

## Por qué un MVP (y no construir el producto completo)

- "Lo que solíamos hacer": Rob pasaba **6 a 12 meses** en el sótano codeando el producto completo,
  lo lanzaba… y **crickets** (silencio). 6–12 meses de costo de oportunidad mientras tenía un
  trabajo de día.
- El MVP **te da permiso** de dar pasos en el camino para **validar que lo que construís hace falta**.
- Cuando construís algo nuevo es **muy probable** que estés **equivocado** en muchos de tus supuestos
  tempranos. El MVP te obliga a ser **deliberado** y a no "tirarte de cabeza a construir".
- La mayoría de la gente del curso **son coders**, y nos sentimos atraídos a construir/escribir código.
  El MVP busca **resistir esa urgencia**, porque si no arriesgamos meses (o años) construyendo en la
  **dirección equivocada**, algo que a nadie le importa.

## Propósito de un MVP

- **Testear hipótesis.** Tenés una corazonada/idea; podrías encerrarte 12 meses a construirla, pero es
  **más probable que desperdicies todo ese tiempo**.
- El MVP te ayuda a pensar **estratégicamente** el próximo paso lógico para **probar o refutar** los
  supuestos más riesgosos.
- Dicho de otro modo: el propósito es **descubrir si el problema vale la pena resolverlo** y si el
  **approach** que estás considerando **va en la dirección correcta**.

## Cuándo construir un MVP

Cuando hay **incertidumbre** en alguno de estos puntos:

1. Creés que el problema **existe** pero no estás seguro de que sea un **dolor desesperante**.
2. Sabés que es un dolor pero **no estás seguro de la forma correcta** de resolverlo.
3. Sabés cómo resolverlo pero **no estás seguro de poder llegar** a prospectos.
4. Podés llegar a prospectos pero **no estás seguro de poder venderles** / de que les importe / de que
   paguen.

> El problema: como fundadores **solemos estar sobre-confiados** en TODOS estos puntos ("sé que es un
> problema porque me lo dijo fulano", "sé cómo resolverlo porque soy product/dev", "sé que llego con
> Product Hunt y Hacker News", "se va a vender solo"). **Todo debería ser una hipótesis hasta probarse
> lo contrario.**

## ¿Siempre hay que construir un MVP?

- **No siempre.** Si podés sacar una **versión completa** de tu producto en **menos de 2 meses**
  —sobre todo si es un negocio **step 1**— considerá **no** hacer MVP y lanzar la v1 (que normalmente
  termina siendo un MVP igual).
- **El catch:** la mayoría de los devs que dicen "son 2 meses" en realidad **tardan 5**. Y si vas a
  hacer eso, estás desperdiciando enormes cantidades de tiempo **sin chequear tus supuestos más
  riesgosos**.

---

# Los 5 pasos de Rob para construir un MVP

## Paso 1 — Definir el objetivo de tu MVP

- Definí **qué querés que logre** el MVP preguntándote: **¿qué estoy tratando de aprender al construir
  esto?**
- Ejemplos de hipótesis (se usan en todo el video):
  - **Bump CRM:** ¿la gente que hoy usa un CRM **se cambiaría al mío** si es más barato, más fácil de
    usar, pero tiene **solo 1/3 de la funcionalidad**?
  - **Postcard:** ¿a los **realtors** (agentes inmobiliarios) les importa tanto el email marketing como
    para anotarse en un **ESP** (email service provider) hecho específicamente para ellos?
- **Métricas de éxito de ejemplo** (para saber si seguís construyendo):
  - **Bump CRM:** el verdadero MVP en este punto es **tener conversaciones y conseguir buy-in de entre
    10 y 40 personas** (números de un video previo, no inventados). Digamos que tenés **10 personas**
    desesperadas porque construyas un CRM liviano. Luego: ¿cuántos de esos 10 que se comprometieron
    **realmente lo probaron** y **se quedaron**? Incluso un **50% de retención** (prueban y no
    churnean) es **muy bueno** en esta etapa temprana.
  - **Postcard:** hablar con ~**100 realtors** (email/teléfono/Zoom) y conseguir que al menos **10
    acepten probar** el producto.

## Paso 2 — Delinear las features core (esenciales)

- Mirá **solo las features esenciales**: las que **no podés shippear sin ellas**, las que son
  **deal-breakers** para que la gente empiece a usar el producto.
- **Features que probablemente NO necesitás construir** en un MVP (sí o sí en una v1):
  - **Billing por suscripción** — quizás ni cuenta de **Stripe** (nadie te paga todavía).
  - **Reembolsos.**
  - **Reset de contraseña** ni siquiera **signup manual** (podés usar un **login** simple o un
    **magic link**).
  - **Botones de delete** — en su última SaaS pasaron meses sin forma de borrar un objeto en la UI; si
    alguien creaba algo por error: "reusalo / retitulalo, o lo marcamos como borrado a mano en la DB".
  - Podés **provisionar cuentas manualmente** en la base de datos y mandarles un reset de contraseña.
- **¿Cuánto debería tardar un MVP?** Idealmente **2 a 4 meses**. Pasados los **4 meses** empezás a
  **perder motivación** (no tenés buen feedback loop con la incertidumbre de "¿lo usará alguien?").
  Podés ir más allá de 4 meses **si** tus 10–20 interesados están muy involucrados y te dan feedback
  positivo.
- **Priorizá** las features críticas por **importancia + input de usuarios** (basado en tu corazonada
  + conversaciones con los interesados).
- **Niche down ayuda:** si hablás con gente de **10 industrias o 10 roles distintos**, pueden pedirte
  **10 CRMs completamente distintos**. Agrupá tu **ICP** temprano (ej: solo fotógrafos freelance, o
  web devs freelance, o realtors) porque tienen **requisitos similares**. No es obligatorio ir
  vertical (podés hacer un CRM horizontal), pero en los días tempranos los pedidos dispares lo hacen
  muy difícil. **Si no encontrás un subconjunto de funcionalidad que la mayoría necesite → bailá de la
  idea o conseguí más early-access customers que tengan algo en común.**
- **Postcard (clave):** para el ESP de realtors **NO construiría un ESP custom ni escribiría una línea
  de código.** Definiría qué ofrecer (secuencias de email pre-armadas, un widget preconfigurado para
  su sitio, un done-for-you service…) y lo armaría **sobre una plataforma existente** (Mailchimp,
  ActiveCampaign, AWeber). **0 código** para sacar el MVP.

## Paso 3 — Elegir el approach correcto para construir el MVP

Un MVP puede ser una landing que junta emails (esto se llamaba **smoke test**), un Google Sheet que
llenás a mano, una **no-code app**, o **software custom**. Los **3 approaches** más comunes:

1. **Human automation (Wizard of Oz).** El hombre/mujer detrás de la cortina hace algo y parece magia
   (parece que corre software), pero es **un humano**. Ej: si el producto va a darle a vendedores
   **100 leads/semana**, lo hacés vos o un asistente virtual y **scrapeás los leads a mano**. ¿Podés
   hacerlo manual **antes** de construir infraestructura? Prueba/refuta la hipótesis (¿le importa a
   alguien? ¿qué pagarían recurrente?). **No quieren software, quieren el resultado** (los leads).
   Pregunta clave: **¿cómo resuelvo esto sin software?**
2. **No-code.** Se volvió popular. Ej: una herramienta de project management para producir podcasts /
   YouTube / TikToks. Hace 10 años necesitabas un dev; hoy lo armás con **Bubble + Airtable +
   Zapier/Make**. (El productor de Rob, que **no es dev**, construyó las herramientas internas de
   podcast/YouTube con eso: app completa con notificaciones y estados, con la que shippean ~104
   episodios/año y hasta 52 videos/año.) Quizás **no escala** a 100–500 usuarios, **pero no es lo que
   estás tratando de hacer ahora** — estás testeando la hipótesis. **El riesgo de "¿puedo
   construirlo?" es bajo;** lo riesgoso es todo lo demás.
3. **Full code (software custom).** Lo que la mayoría imagina. Si **sos dev**, podés llegar acá
   **antes** que otros — aunque Rob igual probaría no-code / human automation / landing primero. Una
   vez derisqueado, no hay validación como clientes **usando y pagando**.
   - **Si NO sos dev:** dos alternativas:
     - **Cofounder developer.** Difícil (es como buscar pareja: matrimonio financiero + relación
       cercana). Se encuentran **uniéndose a comunidades** (MicroConf Connect, eCommerceFuel, Dynamite
       Circle) y eventos en persona / meetups locales. **Si solo aportás una idea, vale poco:** deberías
       saber **marketing/ventas** o ser **subject matter expert** para que alguien ponga sus horas
       (un dev cobra $50–$150/h).
     - **Contratar dev/agencia.** Camino **duro**. Los founders no-técnicos suelen terminar con **código
       malo** porque no saben evaluar al dev/agencia: anda unos meses, a los 6 aparecen bugs, a los 12
       el dev se va y el nuevo dice "hay que reescribir todo, 6 meses". Recomendación: **pagale a un dev
       caro y de confianza** (amigo, Upwork, comunidad) para que te **ayude a vetear** la agencia/dev.
       No garantiza nada pero evita un gran error inicial — **el código es como un edificio: una vez que
       pusiste los cimientos, es durísimo deshacerlo.**
   - **Tech stacks recomendados** (para web apps / SaaS): los **big 3** son **Ruby on Rails**, **Python
     con Django**, **PHP con Laravel** — muy populares, fácil encontrar devs, ecosistemas vivos con
     parches de seguridad, y **no perjudican tu capacidad de vender la app después**. Un **4º** stack
     muy popular y viable (aunque no su favorito): **Node.js**.
- **¿Cuál de los 3 approaches?** Orden de Rob: **si human automation funciona, hacelo primero y
  probalo.** Si necesitás código, investigá si **no-code** lo resuelve (te ahorra muchísimo tiempo).
  Si no, y tenés que ir **full code**, preguntate si tenés **los recursos / skills técnicos / la
  capacidad de financiar** un MVP full code.
- > Por eso cuando un founder no-dev dice "quiero hacer una SaaS", Rob pregunta "¿estás seguro?":
  > es complejo, caro de construir y de mantener. Entrar a algo donde el core es software/desarrollo
  > sin saber de eso es **empujar una roca cuesta arriba (hard mode)** — no es "no lo hagas", es saber
  > en qué te metés y la ventaja que tiene el founder-dev.

## Paso 4 — Crear un timeline de desarrollo (mucha gente lo saltea)

- Establecé un **timeline realista**. **No** se hace diciendo "serán 2 meses": abrí un **spreadsheet** y
  escribí **cada bit y pieza** que necesitás construir, asignándole **horas**.
- (Rob lo hacía como consultor porque tenía que cotizar horas/costo.) **Hacete bueno estimando y
  trackeando tu tiempo.** Armá un **burn-down chart** con **milestones y fases** para saber cuándo se
  te está estirando el build. Acá es donde el dev que dijo "2 meses" se equivoca: **no se sentó a
  pensar qué necesita construir.**
- Cómo desglosar: para una web app, **página por página**, pensando funcionalidad + diseño de base de
  datos + validación. **No tires estimaciones de 40h**: partilas en piezas chicas de **8h o 16h** para
  tener idea real, y **trackeá a medida que avanzás** (tachás y ves cuántos días/horas te quedan).
- **Separá el planning del building.** Si empezás a construir y cada día te preguntás "¿qué construyo
  hoy?", te frena (context switching). Planificá lo más posible al inicio; **no es waterfall** —
  ajustás el curso sobre la marcha. Con un plan sólido, "tengo 2 horas después de que los chicos se
  duerman, sé exactamente qué construir: es la próxima fila del spreadsheet".

## Paso 5 — Manos a la obra (ejecutar)

- Es hora de ejecutar. **No** te encierres 2 meses en el sótano: trabajá **unas pocas semanas** y
  **volvé a esos 10 clientes** / tu lista de early-access: "esto es lo que tengo hasta ahora".
- **Balance:** si no son gente de software, mostrar mockups o cosas a medio terminar puede ser
  complicado — tomalo con pinzas. Pero mantené a la gente **al tanto**: "voy en camino, voy a estar 2
  semanas más tarde de lo que te dije, me encantaría ponértelo en las manos cerca de tal fecha".
  Mantenerlos **enganchados** es súper sano.
- **El ghosting es normal:** los que estaban entusiasmados al principio pueden **desaparecer**, y está
  bien (su situación cambia, se entusiasman menos). Lo que querés hacer es **reemplazarlos**: si
  arrancaste con 10–15 "sí" y te ghostean, salí a conseguir más.
- Para eso: tené una **landing page** y **traé tráfico** (hablando del tema online, ads, SEO, cualquiera
  de los ~20 approaches de marketing B2B SaaS). Tu **lista de emails** debería crecer aunque sea lento,
  y podés **hacer backfill** de tu lista de early-access para mantener el **ciclo de feedback positivo**
  (para ellos y para vos).
