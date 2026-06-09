# Lección: "10 errores comunes de ideas / tipos de ideas a evitar" — Rob Walling (SaaS Launchpad)

> **Qué es esto.** Transcript (limpiado y organizado por error, sin timestamps) de una lección del
> **curso de Rob Walling** (SaaS Launchpad). El tema: **errores comunes** —sobre todo de fundadores
> nuevos— al elegir ideas o tipos de ideas, **con el "porqué" detrás de cada uno**.
>
> **Relación con los 18 factores.** Es el **complemento negativo** del video "Diseñando el negocio SaaS
> ideal" (los 18 factores positivos, en `rob-walling-18-factores-saas-ideal.md`). Acá Rob enumera **10
> errores**. Dos de ellos ya están cubiertos como factores positivos del otro video —**#1 B2C** (Factor
> 1) y **#5 platform risk** (Factor 14)—, por lo que el comando `/saas_idea_validar_idea` los trata
> dentro de esos factores y convierte los **8 restantes** en sus anti-patrones penalizadores **A–H**.
>
> **Atribución:** material del mismo curso que el resto de los comandos (misma fuente/autoridad que los
> videos de validación de Rob Walling). Lo de acá es **lo que dijo Rob en la lección**; el comando
> `/saas_idea_validar_idea` lo convierte en los anti-patrones A–H (las penalizaciones numéricas −15/−12/…
> son scaffolding del sistema, no están en el video).

---

## Error 1 — B2C (vender a consumidores)

- Ya habló en otras lecciones de por qué **no** deberías arrancar un B2C. "Acá es donde van a morir
  muchas de las ideas que escucho." B2C es malo, no lo hagas.
- Sabe que una porción igual lo va a hacer; después le mandan DMs: "ojalá te hubiera escuchado cuando
  me dijiste que no lo hiciera".

> En el comando, este error está cubierto por el **Factor 1 (B2B)**, no como anti-patrón aparte.

## Error 2 — Marketplaces de dos lados

- En vez de un producto donde los clientes te pagan de forma recurrente, hacés **matchmaking**: lado de
  oferta y lado de demanda. Ej: Uber, DoorDash, Instacart, Angie's List (contratistas de un lado, gente
  que los necesita del otro).
- **Extremadamente difícil de construir.** En vez de un motor de marketing, peleás una **guerra en dos
  frentes**: dos productos, dos clientes, marketing y awareness en ambos lados.
- **Excepción (solo para bootstrapping):** si tenés **acceso a un lado del mercado**. (Con $5M de VC en
  el banco, hacé lo que quieras — "go big or go home" — pero bootstrappeando, la única excepción es ese
  acceso.) Ej: **TinySeed** (accelerator) es un marketplace de dos lados —fundadores de un lado,
  inversores del otro— y Rob tenía acceso a **ambos** lados (aunque levantó plata).
- Conoce "un puñado" (5 o menos) que bootstrappearon marketplaces de dos lados con éxito, y **todos**
  tenían acceso a un lado, o le dijeron que fue "**como comer vidrio**" (nunca lo volverían a hacer).
  Ejemplo concreto: **John Doherty**, que tenía una gran red de dueños de agencias y lanzó/vendió
  **Credo** (getcredo.com), marketplace para contratar agencias pre-vetteadas.

## Error 3 — Negocios venture-scale / redes sociales / network effect

- Intentar lanzar negocios **venture-scale** bootstrappeando. Ejemplo perfecto: "competidor de Facebook"
  o "Facebook para dueños de perros" / "Facebook para lo que sea". Cualquier plataforma de social media
  es un **no-go** para bootstrappers.
- Al lanzar tu SaaS querés **resolver un problema real para clientes reales que te pagan plata real**,
  punto. Una red social es como un marketplace de dos lados pero más bien **network effect**: con 5
  usuarios no sirve; necesitás miles o decenas de miles para que sea viable, y cientos de miles o
  millones para que sea **financieramente** viable porque es **ad-supported**.
- **Excepción:** salvo que cobres una **suscripción mensual desde el arranque** y tengas **audiencia
  suficiente para sembrar** la red hasta una masa con algo de viabilidad.

## Error 4 — Construir algo puramente ad-supported

- **Cobrale una suscripción a quien recibe el valor.** Los negocios ad-supported son un espacio /
  mercado / approach completamente distinto.
- Anécdota: tenía un free plan en un SaaS que estaba **cerrando** (le costaba plata y soporte). Alguien
  le sugirió "no lo cierres, metele ads". Pero con single-digit thousands de pageviews/mes (1.000–2.000)
  habría hecho "**5 dólares**". Los ads no funcionan a la escala a la que trabajamos. Error, no lo hagas.

## Error 5 — Construir sobre una sola plataforma con alto platform risk

- En Step 1 / Step 2 del Stair Step Method **podés** tener platform risk (viene incorporado al modelo).
  Pero en un SaaS standalone hay mucho riesgo. **No es un "nunca"** —hay casos donde tiene sentido—, pero
  ha visto negocios **completamente destrozados** por platform risk.
- Ejemplo: inversión en **CartHook** de Jordan Gal — app de Shopify que hacía millones al año, valía
  decenas de millones, y Shopify "vino a golpear la puerta" y destruyó el negocio. Hay docenas (si no
  cientos) de ejemplos. No es tan tajante como otros errores, pero lo señala.

> En el comando, este error está cubierto por el **Factor 14 (platform risk)**, no como anti-patrón
> aparte.

## Error 6 — Cobrar solo un % de fee / GMV / volumen (sin suscripción)

- Vivir de un porcentaje de las transacciones (tipo **Stripe**, 2.9% + fee) funciona a escala masiva,
  no a escala chica.
- **Caveat / no es error:** cobrar **suscripción mensual + un % encima como value metric** es inteligente
  (modelo **Shopify**: más valor para ellos → más valor para vos; refuerza el expansion revenue). Eso
  está bien.
- Pero **solo** el %: cuando Shopify arrancó (hace 15–20 años) solo cobraba eso y rápido se dieron cuenta
  de que no iba a ser gran negocio — hace falta volumen y cantidad de transacciones enormes para juntar
  revenue decente. **Gumroad** también pasó de solo-% a suscripción. Casi todas terminan necesitando
  **ambos**. Construir un negocio basado **solo** en el % es receta de fracaso.

## Error 7 — Lanzar un montón de productos "a ver qué pega"

- En vez de cavar en una **sola idea** y llevarla hasta product-market fit (iterar, escuchar clientes,
  marketing, aguantar la fricción y los headwinds). El "sueño del indie hacker": un producto por mes,
  el que prenda, me pongo detrás.
- **Problema:** no aprendés nada, no mejorás como emprendedor, no sabés qué funciona — es suerte (tirar
  dados a la pared). Y cuando deja de crecer (plateau a $10k), no sabés marketear, pivotear ni superar
  el plateau porque no aprendiste. Los emprendedores exitosos **enfocan** y empujan algo hacia adelante.
  Lanzar cosas sin foco = esperar que algo "mágicamente" despegue. Construir algo grande requiere
  **sacrificio, foco, aprendizaje y hacer cosas difíciles**.

## Error 8 — Intentar definir una nueva categoría de software

- Muy caro, lleva años. **HubSpot** lo hizo con ~$30M en el banco. Rob lo intentó **dos veces y falló**:
  trató de construir **Drip** como categoría nueva, pivoteó hacia categorías existentes (primero ESP,
  después marketing automation) y **ahí** encontró product-market fit y creció rápido.
- Señal del error: en tu **H1 / headline** intentás describir qué hace porque es "algo nuevo" y no querés
  competencia. Mejor: **pegate a una categoría existente** y encontrá tu **rincón** del mercado donde
  podés ser el mejor (más barato, mejor UX, atendés un corner específico).

## Error 9 — Creer que una audiencia en redes sociales = SaaS exitoso

- Pensar que construir audiencia social te da un SaaS exitoso o una ventaja. De forma **muy limitada**
  puede ayudar, pero si no es tu **don natural**, probablemente estás **procrastinando** de lo difícil.
  Si no tenés audiencia ya y vas a construir un SaaS, Rob (que construyó múltiples audiencias, 6 cifras
  de seguidores) **no** construiría audiencia.
- Construir audiencia tiene sentido si vas a **vender información** (cursos, libros, tickets de
  conferencia). Para SaaS, construí tu **RED, no tu audiencia**: la red (influencers, gente de tu
  espacio que te promociona o presenta) te ayuda muchísimo más — JVs y partnerships rápidos.
- Las audiencias **churnean** en SaaS: los info/internet marketers compran un curso o libro
  **aspiracionalmente**, pero si les vendés SaaS, pagan 2-3-4 meses y **cancelan**. Evitá depender de
  esto salvo que sea un don natural o ya tengas la audiencia.

## Error 10 — Lanzar y luego retrasar el revenue

- Bootstrappeando sin funding, cuanto más empujás el ingreso al futuro, más difícil es construir un
  negocio que te permita dejar el day job. Varias formas, todas riesgosas:
  - **Comping for life:** armás una early-access / launch list, entran a usar y dar feedback, y les
    decís "te lo dejo gratis de por vida". Pero esos son los **más interesados y más dispuestos a pagar**
    — son tu revenue inicial (cientos/miles de MRR). No lo hagas. Alternativas mejores: descuento de **1
    año** (los descuentos son un poco "lazy"), o **mejor**: que paguen full price **+ algo extra** (un
    servicio, videos que normalmente cobrás).
  - **Freemium:** "nadie usa mi producto, lo hago gratis". El problema no es que cobrás; es que no
    construiste algo que le importe a alguien, o no lo comunicaste, o no traés tráfico. Hacerlo gratis no
    arregla eso. Parece que debería funcionar (Dropbox, Evernote, Google, Facebook) pero son empresas
    deca/centi-billonarias que levantaron decenas/cientos de millones. **Dropbox convertía ~3% de free a
    pago al año** — pensá cuánto tarda en dar plata. Cita: freemium es como una **katana** — si sabés
    usarla hacés cosas increíbles, si no, te cortás el brazo.
  - **No es error:** **free trial limitado por tiempo o uso** (7/14/21 días, con tarjeta, y después
    pagan) está perfecto. El riesgo es el **freemium permanente / forever-free**, no los free trials.
    No es "nunca", pero si sos inexperto y lo hacés solo porque viste a una empresa grande hacerlo, Rob
    no se metería.
