---
layout: post
title: "¿Desarrollo web SPA o MPA?"
date: 2017-11-06 7:16:59
image: 'https://neoteric.eu/wp-content/uploads/2016/12/spa-vs.-mpa.png'
description: ¿Desarrollar aplicaciones webs siguiendo un patrón SPA o MPA?
category: 'Web'
tags: 
- Desarrollo
- Programación
- Web
- SPA
- MPA
introduction: A lo largo de este post se hablará de las ventajas e inconvenientes de utilizar el modelo de desarrollo “Single page application” o “Multi page application” durante el desarrollo web. Se expondrán ejemplos en los que es conveniente la utilización de un modelo u otro y se comparará la seguridad en cada uno de ellos.
---

## INTRODUCIÓN
Hoy día el desarrollo de aplicaciones web está adquiriendo mucha importancia, ya que tiene
muchas ventajas respecto al desarrollo de aplicaciones de escritorios, principalmente gracias
a la “universalidad”, es decir, una aplicación web no sólo se diseña para un sistema operativo
concreto o un dispositivo determinado, sino que a través de un navegador se puede acceder
desde cualquier dispositivo, sistema operativo…

Es por ello que a lo largo de este artículo explicaremos los diferentes modelos de diseño de
aplicaciones web que se pueden elegir a la hora de desarrollar una aplicación.
Estos modelos de desarrollo pueden ser el “Single page application” (SPA), “Multi page application”
(MPA) o un modelo híbrido de los dos.

## PRINCIPAL DIFERENCIA ENTRE SPA Y MPA
La principal diferencia entre una aplicación SPA y MPA radica en que para la aplicación SPA
sólo existe una página web completa y durante el resto de vida de la aplicación se hacen peticiones
“pequeñas” al servidor para ir cargando las diferentes partes de la página que sean
necesarias, mientras que en una aplicación MPA existen “varias páginas completas” que son
enviadas desde el servidor al cliente a medida que el usuario va interactuando con la página
web.

## SINGLE-PAGE APPLICATION
En una aplicación web que utilice el modelo SPA sólo existirá una página web, esto quiere
decir que sólo habrá una página HTML completa la cual se cargará en la primera petición del
cliente al servidor y el resto de las “interacciones” serán peticiones sucesivas para cargar “partes”
de la aplicación.

Debido a que la página web se carga en la primera petición, esta petición será mas lenta que
el resto, pero una vez la página web ya se haya cargado, el cliente interactuará de una forma
más rápida.

Supongamos, por ejemplo, que el cliente realiza una petición a una página web que muestra
una gráfica con estadísticas en tiempo real la cuales se actualizan cada 15 segundos. Pues bien,
al cliente en la primera petición se le devolvería una página web completa mediante HTTP
(con body, head…) por parte del servidor, pero en las siguientes consultas no se le devolvería
más que los datos de la gráfica (un JSON, por ejemplo), siendo el navegador del cliente quien
actualizase la página para mostrar la nueva gráfica, ahorrando así trabajo al servidor, al no
tener que formar la página HTML completa, y tráfico, al ser peticiones mucho menos pesadas.

![SPA Lifcecycle](/assets/img/SPA.png "Medium example image")

# MULTI-PAGE APPLICATION
Por otro lado, en una aplicación web que utilice el modelo MPA, no solo existirá una página
HTML completa que se cargará en la primera petición, sino que el cliente irá solicitando páginas
completas con cada interacción con el servidor.

Supongamos, por ejemplo, que el cliente realiza una petición a una página web de una empresa
en la que se muestre un menú con varias opciones: Introducción, acerca de nosotros y
contactar. En la primera petición el cliente solicitará la página y el servidor mediante HTTP se
la devolverá de forma completa (con el body, head…). Una vez cargada dicha página si el
cliente pulsa sobre alguna opción del menú, por ejemplo, sobre “acerca de nosotros”, se enviará
una petición al servidor y devolverá una página web de forma completa al igual que en
la primera petición, teniendo así que “cargar” partes que son comunes a todas, como es el
caso del menú con las opciones.

![MPA Lifecycle](/assets/img/MPA.png "Medium example image")

# VENTAJAS DEL MODELO SPA
La principal ventaja del enfoque single-page application será por lo tanto la <strong>rapidez</strong> de la interacción
cliente-servidor, ya que al realizarse la comunicación mediante peticiones pequeñas
en cada interacción del cliente, el mensaje de respuesta será menor, procesándose y enviándose
de una forma más rápida. Esto mejorará, consecuentemente, la experiencia del usuario
al ofrecer un servicio que funciona de una forma mas “fluida”.
Por otro lado, al no ser los mensajes de respuestas del servidor mensajes completos HTML,
no solo pueden realizarle peticiones los clientes web al servidor, sino que por ejemplo, una
aplicación móvil podría interactuar con la misma <strong>API</strong>. Es decir, supongamos que tenemos una
web que muestra una lista con los resultados de fútbol y está realizada mediante el método
SPA. En este caso el cliente, una vez cargada la web en la primera petición, realizará solicitudes
para obtener una lista de los partidos del Madrid, del Manchester, de esta semana… por ejemplo.
Esta petición no devolverá una página HTML (con la cabecera, el cuerpo…) ya formada
sino que devolverá, por lo general, una respuesta JSON que el cliente tratará, por lo tanto no
restringe su uso a clientes de páginas web, pudiendo ser utilizada por otras aplicaciones que
realicen peticiones a dicha API, como puede ser el caso de una aplicación móvil.
Además, esto implica que el <strong> servidor y el cliente son totalmente independientes</strong>, pudiéndose
mantener de forma separada más fácilmente.

# INCONVENIENTES DEL MODELO SPA
Uno de los principales inconvenientes de este enfoque es que <strong>el cliente tiene una mayor carga
de trabajo</strong>. Esto es debido a que las respuestas del servidor no serán páginas webs ya formadas
y, por tanto, el cliente tendrá que interpretar dichas respuestas para formas así una página
web.

Otro problema del desarrollo en este modelo se basa en que <strong>el cliente ha de interpretar código
en su máquina</strong> en general (JavaScript), siendo esto un fuerte contra para la seguridad.

Además de todo esto, existe otro inconveniente que afecta principalmente a páginas webs
que quieren darse a conocer al mayor número de personas posibles, ya que al ser páginas
interpretadas en el cliente <strong>perjudica</strong> en gran medida a las técnicas de <strong>posicionamiento SEO</strong>,
es decir, una página web que sigue el enfoque SPA será mas complicada de encontrar mediante
los buscadores habituales (Google, Bing, Yahoo, Ask…) ya que las tecnologías utilizadas
por estos servicios no interpretan una página web completa e interactúan con ella por las
diferentes rutas dentro de ellas.

# VENTAJAS DEL MODELO MPA
La principal ventaja del enfoque MPA es que <strong>el cliente no necesita interpretar código</strong> ya que
las páginas webs son devueltas por el servidor ya formadas, solo teniéndose que mostrar en
el navegador del cliente. Esto hará que toda la carga recaiga en los servidores, liberando de
trabajo a los terminales que actúen como cliente que en general son mucho menos potentes
que los grandes servidores en los que suelen estar desplegadas las aplicaciones webs.
Por otro lado, a gran diferencia del modelo SPA, mediante esta técnica de desarrollo obtendremos
un <strong>posicionamiento web</strong> mucho mejor ya que las técnicas SEO funcionan mejor con
sitios webs que utilizan esta tecnología.

# INCONVENIENTES DEL MODELO MPA
El principal inconveniente de desarrollar páginas webs siguiendo el enfoque MPA se basa en
que el usuario tendrá una <strong>peor experiencia a la hora de navegar</strong> por el sitio web ya que las
interacciones serán mucho mas lentas y pesadas.
Esto se debe a que en cada petición el servidor ha de tratar la acción, generar la nueva web
completa y enviarla de vuelta al cliente, siendo esto mucho mas pesado (Mayor tiempo de
procesamiento en el servidor y de envío al cliente).

Sin embargo, este inconveniente mejoró con la aparición de las peticiones asíncronas realizadas
con AJAX, pudiéndose hacer así peticiones a una parte de la web mientras el cliente puede
seguir navegando por el resto de la página. Pero el inconveniente de esto es que el código
gana mucha complejidad llevando ello a un <strong>mayor tiempo de desarrollo</strong> de una aplicación
web con el enfoque MPA.

Además de todo esto, al devolver el servidor directamente respuestas HTML se produce una
<strong>fuerte relación cliente-servidor</strong> impidiendo así su desarrollo por separado de una forma sencilla.

# ¿QUÉ ENFOQUE ES MÁS SEGURO?
Es cierto que a la vista de lo anterior, el modelo SPA apunta a ser generalmente el mejor de
ellos, pero ¿Es también mas seguro?
Como se dijo anteriormente <strong>en el enfoque SPA se interpretará código JavaScript en el
cliente</strong>, siendo éste el encargado de generar las diferentes vistas de la web tras realizar peticiones
al servidor solicitando <strong>datos</strong>.

Esto puede ser un problema ya que si un cliente malicioso intenta acceder a las diferentes
vistas de un modelo SPA (manipulando el código del lado del cliente), aunque estas vistas le
aparezcan “vacías” (ya que al realizar las distintas peticiones solicitando datos el servidor se
lo denegaría porque no tendremos permisos), podría conocer las distintas acciones o vistas a
las que tendría acceso un usuario autorizado.

Este problema no existirá en páginas webs realizadas mediante el enfoque clásico MPA, ya
que en este caso es el servidor el que devuelve una vista u otra y por tanto si un cliente sin
permisos intenta realizar alguna petición no permitida para él, el servidor podría devolver
una página diferente (un 401 o 404, por ejemplo).

# UN ENFOQUE HÍBRIDO
Entonces, si tanto una técnica como la otra se complementan, ¿por qué no optar por una
opción híbrida?

Pues en <strong>la mayoría de los casos una forma híbrida sería una buena opción</strong>, por ejemplo, en
el caso de la seguridad mencionado anteriormente, si hacemos una tecnología híbrida podríamos
crear dos “vistas” diferentes mediante el enfoque MPA una para cada rol y dentro
de cada una, una vez autenticado, utilizar el modelo SPA.
Sin embargo esto produciría una mayor complicación a la hora de desarrollar la aplicación.

# CONCLUSIÓN: ¿QUÉ ENFOQUE UTILIZAR?
No existe una respuesta unívoca a la pregunta anterior sin embargo si podemos hacernos
una serie de preguntar sobre qué necesitamos y qué iría mejor:

* Mi página web será primordial para mi negocio y por tanto necesito que la conozcan el
mayor número de clientes (Mi negocio está en la web):
En este caso irá mejor el enfoque MPA ya que obtendrás mejor posicionamiento en los buscadores
webs (Google, Yahoo, Bing…).
* Mi página web necesita grandes medidas de seguridad:
Entonces, o bien utilizas MPA o un sistema híbrido para no permitir que los usuarios maliciosos
modifiquen el código JavaScript del cliente.
* Mi página web necesita ir muy fluida ya que muestra estadísticas en tiempo real o similar:
Entonces se recomienda usar SPA ya que las recargas de los datos son más rápidas.
* Dispongo o quiero disponer de una aplicación móvil que realice algo similar a la web:
En este caso si realizamos la web con el enfoque SPA podremos reutilizar la API del servidor
para desarrollar las peticiones de la aplicación móvil al mismo servidor.
* Quiero realizar mi propia página web, no conozco ninguna tecnología, ¿Cuál utilizo?
Si es tu primera página web el enfoque SPA es un enfoque más fácil y con un tiempo de
desarrollo menor.


