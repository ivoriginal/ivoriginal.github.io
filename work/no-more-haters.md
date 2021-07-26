---
layout: page-back
title:  Fighting hate speech with... games?
description: <strong>No More Haters</strong> is a collection of games to help young people detect and fight hate speech
client: maldita.es
client-logo: https://miro.medium.com/max/844/1*v2mrZKEqqY80h0KpUIr-4Q.jpeg
tags: [UX research, UI design, Development]
image:  '/images/work/no-more-haters.png'
---

We still didn't know <strong>what the hell was</strong> a coronavirus by the time our friend David from N̶e̶w̶t̶r̶a̶l̶ Citymapper intro-ed us to David from maldita.es (to whom, from now on and with narrative ends, we'll call David Part 1 and David Part 2: The Revenge, respectively)

It turned out that maldita.es, the press asociation that fights fake news, needed an extra pair of hands for a pretty cool project that was being cooked with FAD and Google.org
David Part 2: The Revenge told us that he'll soon tell us more about it, but a guy ate a bat and the whole world went to shit. Such is life, I guess.

Months later, when Carlos and I started to adapt to the New Normal™️, we stepped outside our nuclear shelter, dusted off our inbox and hey: there it was, the mail from David Part 2. We 

Meses más tarde, cuando Carlos y yo empezábamos a adaptarnos a la Nueva Normalidad™️, salimos del refugio nuclear, desempolvamos nuestro inbox, y oye: ahí estaba el correo de David Parte 2. Recordamos su magistral cliffhanger y decidimos que "pronto" era ya mismo.
Parece que sí que funcionó.El proyecto –nos contaba David Parte 2, finalmente– se llamaba NO MORE HATERS, y era una app con juegos para enseñar a chavales/as cómo detectar y combatir el hate speech (o como dice mi abuela: las tonterías que dice el tío ese de verde en la tele). Por nuestra parte correría el desarrollo y el diseño del producto y las mecánicas de los juegos, y por parte de ellas el contenido.
Una vez más, encontramos un cliente que nos daba barra libre para trabajar el apartado visual y elegir stack tecnológico. Ya teníamos experiencia haciendo mecánicas de gamificación y desarrollando PWAs, y el equipo de Maldita.es parecía ser un encanto, así que ya sabéis lo que pasó a continuación:

(Lo hicimos)El kickoff
Para encontrar inspiración y construir una suerte de universo visual común, empezamos a repasar las apps de educación (Duolingo, Memrise, Khan Academy…)  y de juegos tipo brain training (Peak, Elevate…)
El producto que inevitablemente nos venía a la cabeza cuando pensábamos en juegos divertidos para gente de un rango de edad relativamente amplio era Duolingo (abajo), que se apoya bastante en su iconografía e ilustración original. 

Cuando se dio el pistoletazo de salida, el equipo de Maldita.es todavía estaba trabajando en el contenido –que además iba a ser multi-idioma– así que tuvimos que empezar a diseñar sin saber muy bien cómo de largos eran los textos, qué tipo de escenarios íbamos a tener, etc.
El contenido es, en gran parte, lo que define el layout. Si tienes imágenes grandes y chulas puedes hacer ésto, y si tienes titulares llamativos e historias interesantes puedes hacer ésto otro. Nosotros teníamos: buenas intenciones. 
Nos arremangamos y empezamos a diseñar una interfaz llena de placeholders que pronto empezaría a tomar forma.
Haciendo la diseñación
Marca ➡️ interfaz
Laura de Maldita nos mandó el manual de la marca diseñada por NSUE y abrimos un nuevo proyecto en Figma para empezar a generar el sistema tipográfico y el sistema de color. Para la tipo, Montserrat; para el color, en el manual sólo venía un rojo (#e1052d) y negro puro, así que empezamos generando variaciones del rojo y dejamos los secundarios, acentos, etc. para un poco más adelante. 
Coolors es una herramienta increíble para comparar armonías y para simular protanopia y otras condiciones.
#E1052D Color info - Coolors
Get useful #E1052D color information like combinations, blindness simulation, libraries matching and converson in RGB…coolors.co
Le subimos un poco la luminosidad al negro para evitar un contraste demasiado alto con el fondo blanco, pero no se lo digáis a los de NSUE. 
Front-end ↔️ Figma
Nos importamos al Figma los componentes de Material para hacer un primer prototipo. Ya sabíamos que íbamos a desarrollar en vue.js + Vuetify, así que si el diseñador no se pasaba de listo personalizando los componentes de Material, podríamos pasar de prototipo a cosa que funciona de verdad relativamente rápido.

Los requerimientos eran:
Crear una cuenta (requerimiento del cliente), y por lo tanto:
Editar o borrar tu perfil. 
Una forma de acceder a los tres juegos.
Una forma de ver tu puntuación en relación a otras jugadoras.
Una forma de buscar bulos usando el motor de maldita.es

Uno de los casos de uso era que una profe lo abriese en los ordenadores de clase para jugar con el alumnado, así que la web app también tendría que poder jugarse cómodamente desde un viewport grandecito. Por eso decidimos crear un container con ancho máximo que pudiese mostrar todos los menús en cualquier pantalla de ordenador, grande o pequeña. 
Si los ordenadores tenían resoluciones o ratios de aspecto antiguas, el contenedor se ajustaría al ancho de la pantalla sin problema. 
Si por otra parte abrían la web en una pantalla gigante (o ultrapanorámica, que nunca se sabe…) el contenedor no escalaría horizontalmente: mantendría su tamaño máximo.
Este fue el primer "borrador":

Un layout para dominarlos a todos
En viewports más pequeños (tablet, móvil…) el buscador y el ranking se convertirían en menús independientes accesibles desde un bottom navigation (o como dicen en la RAE: navegación p'abajo), manteniendo "juegos" como el menú principal.

Sí, soy un maestro del Auto Layout
Íbamos a tener que compilar la web* para subirla como app a los stores de Apple y Google, así que diseñar dos modelos de interacción (uno para la web y otro para la app) habría sido un infierno de media queries y user agents**; a pesar de los problemas que da Safari con este tipo de navegación, decidimos seguir adelante con la navegación p'abajo. Mucha gente se he pegado con ésto antes que nosotros, así que no fue (muy) difícil encontrar truquis para que no diese muchos problemas***
* Si te interesa el apartado técnico, Carlos te cuenta dentro de un ratito cómo fue el desarrollo
** Ésto a lo mejor no lo explicamos
*** Ésto sí que lo explicamos

✨ La magia del responsive ✨
Diseñando personajes sin raza, género o edad
Como te contaba arriba, una de nuestras mayores inspiraciones para este proyecto era Duolingo. Hace un tiempo actualizaron su marca para incluir personajes diversos que les ayudasen a hacer los juegos y algunas interacciones más amigables, y representar los distintos tipos de usuarios que un producto global pueda llegar a tener.
Duolingo para todes ❤No hay nadie en Commit Sans que tenga mucha mano para la ilustración, así que abrimos la agenda y empezamos a llamar a nuestros coleguis. Deivid Sáenz nos recomendó hablar con Silvia Fernández Palomar, la diseñadora de Ferpal Sans: la tipografía de los carteles de San Isidro 2018, que más tarde fue adaptada por el ayuntamiento de Madrid para los letreros de sus calles.
Nos pusimos en contacto con ella, y después de hablar un ratito de sus proyectos y de nuestros planes para NO MORE HATERS, vimos que trabajar juntos podría ser la bomba.
Empezamos con el briefing (palabra inglesa que en español significa "ésto es lo que no sabemos hacer, por favor ayúdanos"): necesitábamos unos personajes sin género ni marcadores étnicos con cierta expresividad para un producto digital enfocado a gente de entre 14 y 25 años; ni demasiado infantiles, ni demasiado adultos.
¿Por qué digo "con cierta expresividad"? Porque los usaríamos para reforzar positivamente a los/as usuarios/as cuando respondiesen bien a una pregunta, o para no desanimarlos cuando se equivocasen. ¡Tenían que tener cara, por lo menos!
Y como Silvia es como el T-800 en Terminator 2 (una máquina), como Will Smith en Soy Leyenda (una leyenda), como los bichos esos grandes de Ataque a los Titanes (una titana), en muy poco tiempo tenía listo un moodboard (o como dice la gente normal: una colección de referencias visuales) para ayudarnos a encontrar una identidad que se ajustase al briefing.
El moodboardNos gustó mucho a todas el póster de las bolitas neon con el fondo amarillo (arriba a la derecha, marcado con un corazón). Algo así parecía fácil de diseñar y jaquear. A Silvia también le gustaron mucho las formas geométricas del póster con fondo negro de abajo a la derecha, y la idea de hacer personajes modulares del panel central.
Silvia nos hizo dos propuestas para compartir con el cliente y así poder ver cómo se sentían en relación a cada una de ellas: qué les cuadraba más de la primera, qué les gustaría conservar de la segunda, etc.
La primera nos gustó mucho más por su potencial para construir un sistema de ilustración y adaptar cada personaje o cada cabecita para cada interacción con el producto:
La "propuesta A"De la segunda –que no te voy a enseñar a no ser que me lo pidas amenazadoramente– nos gustó más a todas la idea de que los muñequitos tuviesen también boca para poder expresar mejor emociones. Silvia iteró los personajes en tiempo récord y nos envió algunas posibles aplicaciones que nos encantaron:

Los personajes de la  "propuesta A" aplicados a la UI
Enseñamos distintas variaciones a familiares y amigos de conocidos en los rangos de edad que maldita.es había definido, y enseguida confirmamos que NO MORE HATERS empezaba a molar 😎
El sistema de ilustración
Al haber construido los personajes de forma modular, pudimos crear una especie de generador de personajes en Figma donde cambiábamos las cabezas, los cuerpos, las caras o los colores usando instancias y estilos compartidos.
Aquí las piezas sueltas:
Y aquí, el joven Ivo, ilusionado, enseñándole el sistema de ilustración a Silvia:

De ese frame sacamos todos los personajes y creamos componentes que reutilizaríamos como instancias en todos los apartados del producto. Teniendo una página con todos los assets, Carlos podía exportarse los personajes en SVG, PNG o lo que hiciese falta sin que ningún estúpido y atractivo diseñador hiciese de cuello de botella.
También nos sirvió para compartir los avances con el equipo de Maldita.es, y en especial, para coordinar el lanzamiento de la landing promocional de NO MORE HATERS con Pablo, su diseñador in-house.
Diseñando los juegos
El Rondo: haciendo malabares con las columnas
El mayor reto fue el layout de los juegos. Uno de ellos recuerda a un conocido formato televisivo que en pantallas grandes funciona fantástico, pero para sorpresa de nadie, en viewports pequeñitos no cabían todas las cosas. 
Primer prototipo del Rondo"¿¡Dónde metemos ese rosco gigante!?", gritaba el Ivo de entonces entre lágrimas a la pantalla del ordenador. "No lo sé, bro. Ese es tu trabajo", respondía un un joven desarrollador tan sensato como barbudo.
Para viewports de tamaño medio fue relativamente fácil de adaptar, pero para móviles tuvimos que encontrar una solución "creativa": en el rosco sólo se mostraría visualmente en qué zona estás actualmente, pero la letra de dentro de la selección se vería en un nuevo bloque con scroll horizontal, añadiendo un tooltip que lo remarcase:
Puedes echar una partidilla aquí, si te aburres de tanto leer: https://play.nomorehaters.es/rondo
Verdadero o falso: no es una app para ligar
El modelo de interacción quizá te suene. Mucha gente me lo dice, pero no sé de qué les va a sonar, si lo inventé yo. Es 100% original y no puedes probar lo contrario.
Un modelo de interacción 110% originalEn viewports más grandes funcionaba exactamente igual, siendo las tarjetas algo más anchas. Cuando te equivocas, te explicamos por qué, y mostramos uno de los muñequito que te mira fijamente con cara de desaprobación para que t̶e̶ ̶s̶i̶e̶n̶t̶a̶s̶ ̶c̶u̶l̶p̶a̶b̶l̶e̶ ̶p̶o̶r̶ ̶t̶r̶a̶g̶a̶r̶t̶e̶ ̶u̶n̶ ̶b̶u̶l̶o̶ ̶d̶e̶ ̶l̶a̶ ̶u̶l̶t̶r̶a̶d̶e̶r̶e̶c̶h̶a̶ aprendas a detectar mejor la desinformación.
¡Es que os lo creéis todo, macho!Si no te has echado una partida al Rondo cuando te he dejado el enlace ahí arriba, es el momento perfecto para probar Verdadero o falso: https://play.nomorehaters.es/cards
Si sí que te has echado una partida al Rondo cuando te he dejado el enlace ahí arriba, es el momento perfecto para probar Verdadero o falso: https://play.nomorehaters.es/cards
Elige tu propia aventura.
El Quiz: miniaventuras gráficas para todas
Ésta fue, sin ninguna duda, la parte más complicada del proyecto desde un punto de vista de interacción, planificación y diseño de contenidos. Acordamos con el cliente dejar este juego, inicialmente conocido como "proyecto x de la muerte mortal" para el final, ya que sabíamos que iba a ser algún tipo de aventura gráfica animada, pero no sabíamos exactamente qué personajes habría, ni teníamos guión, ni sabíamos cómo íbamos a animarla.
Cero dramas, siempre smile.
Desde antes del kickoff ya sabíamos que se nos iban a complicar las cosas, pero no sabíamos hasta qué punto.
Intentando que el layout del Quiz no se nos fuese de madreEn las primeras conversaciones con Nuestra Ilustradora de Confianza™️ ya le hablamos sobre éste juego, y le dijimos que en algún momento le pediríamos diseñar escenarios que pegasen con los muñequitos en los que pronto empezaríamos a trabajar.
Cuando Laura nos mandó el contenido, ya en la recta final del proyecto, estábamos inmersos en el desarrollo, y después de echar números vimos que no íbamos a tener tiempo material de encargar a Silvia ese segundo proyecto de ilustración, revisarlo con el cliente, discutirlo ni iterarlo, ni muchísimo menos de animarlo. 
Menudos project managers estamos hechos. En fin.
Según el guión de Laura había, al menos, cuatro escenarios distintos, así que me até la manta a la cabeza y los diseñé y animé en un fin de semana de crunch. "Sé tu propio jefe", decían. "Controlarás tus horarios, tendrás más libertad", dijeron. Ajá.

Mano para ilustrar no tendré, pero apañao soy un rato
La primera fila en la captura de arriba es "clase", la segunda "con amigos", y la tercera "en casa". El cuarto escenario es "en Twitter", para el cual decidimos simular la UI de una red social en lugar de dibujar un espacio físico:
Para animarlo, a Carlos se le ocurrió diseñar todos los escenarios con cuatro niveles de profunidad como máximo en mente. Así, podríamos copiar y pegar las propiedades de animación de cada nivel de profunidad de un archivo al siguiente. Más o menos.
Me explico: esta es la animación de entrada que se repite en casi todas las viñetas de "en clase". He reducido la velocidad al 50% para que se aprecie mejor:
Si te fijas, hay tres niveles, y cada uno entra a una velocidad y en una dirección:
1. Personaje en primer plano | 2. Personaje en segundo plano | 3. Fondo (pizarra)La cabeza de 2. Personaje en segundo plano se mueve en el eje Y para reforzar la risita malvada. Estos valores los podríamos copiar a otros elementos con estructura similar para ahorrar tiempo y esfuerzo. 
Para hacer la animación, el bueno de Miguel nos recomendó usar Keyshape, que es algo así como After Effects para tontos*: tiene las funcionalidades básicas para animar y exportar sin toda la complejidad que tiene un software profesional que se usa para hacer cosas complicadísimas.
* Espero que no me lo recomendase con eso en mente
Espacio de trabajo en KeyshapeDesde Keyshape se puede exportar a Lottie, a SVG, a formatos de video y básicamente a lo que te dé la gana. 
Al ver que SVG no guardaba correctamente algunas de las propiedades que habíamos aplicado a las capas, decidimos probar a exportar en WebP vídeo (sí, WebP también tiene codec de vídeo), y una cosa te digo: la compresión es expectacular. Al menos para éste tipo de imágenes de colores planos y animaciones sencillas.
El stack tecnológico (por Carlos Hernández)
Vale, muy chulo el producto, y muy divertidos los juegos, pero… ¿Y ésto como lo habéis construido? ¿Que hay por detrás? Ya que te hemos abierto las bambalinas de este proyecto, te lo cuento también. Es más sencillo de lo que te esperas, pero hay dos detalles que, seguro, te van a sorprender.
El front
Empecemos por el front-end. Lo que se ve. Lo bonito. Está hecho con Vue (v2, cuando empezamos con esto la v3 todavía estaba en pañales) y apoyado en Vuetify. ¿Por qué? Porque Vue nos ofrece reactividad y data binding bidireccional, que para un juego interactivo es un must. Podríamos haber usado React, sin duda, pero estamos más cómodos trabajando con Vue, honestamente.
Vuetify nos ha dado una base maravillosa sobre la que construir: botones, iconos, dropdowns, barras… todo siguiendo las directrices de Material, y bien testeado por una comunidad inmensa. Y, sobre esta librería, hemos creado nuestros componentes. Así podemos dedicar el tiempo a que los juegos molen y no tenemos que comernos la cabeza reinventando la rueda.
La parte de autenticación era lo más delicado. Es un juego al que pueden jugar menores. Esto quiere decir que tenemos que tener especial cuidado en qué datos usamos, y cómo los procesamos. Decidimos no usar datos personales identificables. Nada de emails. Para no desarrollar un sistema complejo de autenticación, y asegurar que no hay problemas de seguridad, hemos usado el servicio de Firebase. Ya está Google trabajando para que eso no pase.
El back
En cuanto al back-end, lo que no se ve, hemos usado una de mis combinaciones favoritas: NodeJS y MySQL. 
Pero, ¿MySQL no era para PHP? Una base de datos del pasado, vaya…
Ahora mismo, todos los hipsters del código están llamándome viejoven. Bien por ellos. 
Una de las cosas que teníamos claras es que se iba a usar en coles. Esto quiere decir que, quizá, en un mismo momento del tiempo nos podía venir mucha carga a la vez. Esto es una de las ventajas de Node. Al mismo tiempo podíamos usar caché en memoria para evitar consumir más recursos de 
los necesarios en la base de datos. Sonaba bien.
Por otra parte, los juegos son sistemas relativamente sencillos de normalizar: usuario, juego, partida. Todo puede funcionar de forma sencilla y eficiente en una base de datos relacional. Además, en la arquitectura que tenía montada David Parte 2: La Venganza ya había MySql instalado. 
No añadir una pieza nueva a su arquitectura me pareció un motivo más que suficiente para enfocar el tiro.
Básicamente, NodeJS expone una API, que se conecta a MySQL para traer y llevar los datos. Por delante, tenemos un proxy inverso con Nginx. Todo muy estándar, la verdad.
¿Y la autenticación en el back, como la habéis conectado con Firebase?
Muy sencillo: JWT
Verás. En el front, se hace el login. Sólo tu dispositivo sabe tu usuario y contraseña. Cuando Firebase lo aprueba, nos da un token JWT. Ese token es la llave para validar el login. Es el token el que se manda a la petición de login de la API.Desde Node, validamos con Firebase el token, obtenemos el ID y nombre de usuario, y construimos un token de autenticación con la API, ajeno a tu login de Firebase.
Así el juego funciona con tu usuario, pero sin utilizar nada de información personal, ni enviar contraseñas.
Lo del modelo de interacción dando problemas en iOS
Los problemas con el status bar de iOS a la hora de compilar la web los solucionamos poniendo esto en el head:
<meta name="viewport" content="width=device-width, height=device-height, initial-scale=1.0, user-scalable=0, minimum-scale=1.0, maximum-scale=1.0">
Lo de la navegación del sistema superponiéndose al bottom navigation lo arreglamos poniendo un safe padding:
env() - CSS: Cascading Style Sheets | MDN
The env() CSS function can be used to insert the value of a user agent-defined environment variable into your CSS, in a…developer.mozilla.org
Designing Websites for iPhone X
The section below about safe area insets was updated on Oct 31, 2017 to reflect changes in the iOS 11.2 beta. Out of…webkit.org
Fácil, ¿no?
Lanzamiento y recepción

Tras tres meses de duro trabajo y algún tiempo más de bugfixes y pequeños updates, al fin dimos por terminado nuestro papel en NO MORE HATERS y volvimos a la cueva de la que salimos una o dos veces al año para hacer cosas chulas y tomar el solecito. 
Las apps y la web suman casi 14.000 usuarios desde su lanzamiento, pero como puedes ver en la sección de comentarios del spot de la campaña (arriba), todavía queda mucho trabajo por hacer. Y si quieres poner tu granito de arena frenando el discurso del odio y no sabes por dónde empezar, échale un ojo a esto.

---

Recursos
Maldita.es y Fad lanzan 'No more haters' para luchar contra el discurso de odio en redes en…
Maldita.es y Fad, con el apoyo de Google.org, lanzan "No more haters. ¡Rompe la cadena del odio!", un proyecto para…maldita.es
'No More Haters': la app que nos ayuda a combatir los discursos de odio en redes
La app que permite identificar y dar herramientas a los más jóvenes para hacer frente a los discursos de odio. Un 38,1%…www.rtve.es
Odiómetro | El espejo de nuestro odio
¿Somos conscientes del poder de la persuasión, de la inteligencia, de la empatía, de la educación, del humor para…odiometro.es
No les des casito
@nolesdescasito es una cuenta de Twitter que tiene el objetivo de promover estrategias para frenar a la ultraderecha en…nolesdescasito.carrd.co
Romper cadenas de odio, tejer redes de apoyo: Los y las jóvenes ante los discursos de odio en la…
La investigación 'Romper cadenas de odio, tejer redes de apoyo: Los y las jóvenes ante los discursos de odio en la red'…www.adolescenciayjuventud.org

---

Pero… ¿Commit Sans no es una tipografía?
No sé de qué me hablas. 
Commit Sans somos Carlos Hernández y yo, Ivo Vilches, y hacemos desarrollo integral de productos digitales. Sí, como el pan: integral, desde la fase más temprana hasta la release, pasando por el branding y el desarrollo del front, del back y de todo lo que haya entre medias (¿el mid? 🤔)
Commit por el código y Sans por el diseño. Tremendo juego de palabras, sí.
También mandamos un newsletter en formato físico, hemos hecho una colección de herramientas para gestionar comunidades que se llama (sorpresa): Community Tools, y pronto sacaremos un videojuego y un disco de metal. No es broma. 
Cuando no sabemos hacer algo súper bien, llamamos a nuestros amigos. Si quieres ser nuestro/a amigo/a, escríbenos unas líneas. Si quieres pagarnos por hacer cosas chulas, también escríbenos unas líneas. Y si tienes un proyecto bueno para la Pachamama y sus gentes, también escríbenos esas líneas, que a lo mejor hasta lo hacemos gratis.
Cuídate mucho y hasta la próxima ❤