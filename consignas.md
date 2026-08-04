# Ingeniería en Computación 2 — Bloque de Software

## De qué va esto

Vienen de electrónica y de programar Arduino. Acá damos el salto a **Python sobre Raspberry Pi** y le metemos **comunicaciones**: APIs y MQTT, todo corriendo en **contenedores**.

Esta materia es la **antesala de Computación 3 y 4**. No buscamos que dominen estos temas: buscamos que lleguen a las materias que vienen con el mapa mental armado, el vocabulario puesto y —sobre todo— con la experiencia de haber construido un sistema completo de punta a punta y haberlo hecho funcionar.

## La regla del juego

**Esto se construye de cero.** No hay esqueleto para completar, no hay código pre-armado, no hay trampas plantadas. Arrancan de un repo vacío y de una consigna.

Eso significa que **se va a romper**. Las dependencias no van a estar, el mensaje no va a llegar, el contenedor no va a encontrar la base. Está bien. Eso es ingeniería. Un ingeniero reniega desde la instalación de una librería hasta la lógica de lo que está armando, y aprende en cada tramo.

Lo único que importa: **cuando algo se rompe, hay que entender por qué.** Resolver un error pegando un comando de internet que no entendieron no cuenta. Leer el error, aislar el problema, entender la causa y arreglarlo — eso sí. Los profes están para empujar en esa dirección, no para darles la respuesta.

---

## El objetivo final (el capstone)

Al terminar el bloque, tienen que tener **este sistema andando**:

```
[Dispositivo simulado]                      [Consumidor / Bridge]
  publica lecturas         ─── MQTT ───▶      se suscribe al topic
  cada N segundos                                   │
  (JSON con sensor y valor)                         │  por cada mensaje:
       │                                            ▼  llama a la API
       ▼                                       [API HTTP]
  topic: ej. aura/sensores/temp                     │
                                                    ▼
                                            [Base de datos]
```

En palabras: **un dispositivo publica lecturas por MQTT, un consumidor las levanta y, usando la API, las persiste en una base de datos.** Todo levantado con un solo comando, en contenedores.

Qué tiene que hacer el sistema (el *qué*, no el *cómo* — el cómo lo resuelven ustedes):

- El dispositivo simulado genera lecturas (temperatura, humedad, lo que elijan) y las publica por MQTT a intervalos regulares.
- El consumidor está suscripto al topic y reacciona a cada mensaje que llega.
- El consumidor **no escribe directo en la base**: usa la API. La API es la única que toca los datos.
- La API recibe la lectura, la valida y la guarda en la base de datos.
- Tiene que poder consultarse lo que se guardó (un endpoint que liste las lecturas, una query a la base, lo que sea que demuestre que el dato llegó hasta el final).

Esa separación —el que publica no sabe nada de la base, la API es el único portón a los datos— no es un capricho: es exactamente cómo está pensado un sistema IoT real.

---

## Las 4 clases

Cada clase deja **una pieza andando** que sobrevive hasta el capstone. No son temas sueltos: es el mismo sistema que se va armando.

### Clase 1 — Python y Git

**Objetivo:** empezar a moverse en Python. Tener el repo del equipo creado y funcionando.

Al final de la clase tiene que estar andando:
- Un script de Python que resuelva un problema con datos reales (parsear lecturas, calcular promedios, detectar valores fuera de rango — no un "hola mundo").
- El repo del equipo en GitHub, con todos commiteando. Trabajando sobre el mismo repo de verdad (sí, se van a cruzar; resolver el primer conflicto es parte de la clase).

Punteros:
- Python: documentación oficial, foco en tipos, listas, diccionarios (clave para JSON después).
- `venv` para aislar el entorno.
- Git: `clone`, `add`, `commit`, `push`, `pull`. GitHub para el repo compartido.
- `pytest` para escribir tests automáticos de sus propias funciones (no es obligatorio para el cierre de hoy, pero lo van a necesitar en las clases que vienen).
- **Track de Git por etapas:** [`../../code/ic-git-por-etapas`](../../code/ic-git-por-etapas) — etapas 1 a 5, ejercicios y rúbrica. Es el recorrido de Git de esta clase.
- `gpiozero` si quieren tocar GPIO de la RPi desde Python.

### Clase 2 — APIs (y el concepto de MQTT)

**Objetivo:** tener una API propia que reciba y devuelva datos, y entender *en concepto* la diferencia entre *pedir y que te contesten* (HTTP/API) y *publicar y que el que quiera escuche* (MQTT).

Al final de la clase tiene que estar andando:
- Una API que reciba lecturas (POST) y las devuelva (GET). Probada desde su documentación interactiva y desde un script cliente.
- Haber visto un mensaje MQTT viajar **contra un broker público de prueba** (sin instalar nada) y entender el modelo pub/sub. El broker propio llega en la clase 3.

Punteros:
- FastAPI (regala documentación interactiva en `/docs` — úsenla para probar sin escribir cliente).
- `requests` para consumir la API desde Python.
- Conceptos a tener claros: verbos HTTP, JSON, códigos de estado (200, 404, 422).
- Para el anticipo de MQTT: un broker público (`mosquitto_pub`/`sub` o un cliente web contra un servidor de prueba). Cero infraestructura: el broker propio se baja como imagen en la clase 3.

### Clase 3 — Docker (y el broker MQTT, ahora de verdad)

**Objetivo:** entender qué problema resuelve un contenedor (ese "en mi máquina anda y en la tuya no" que para entonces ya sufrieron), dejar el stack corriendo orquestado, y de paso conseguir el **broker MQTT propio** bajándolo como imagen.

Al final de la clase tiene que estar andando:
- La API de la clase 2 dentro de un contenedor, con su Dockerfile escrito por ustedes.
- Un `docker-compose` que levante de un solo comando: la API, el broker MQTT y la base de datos.
- Pub/sub funcionando contra **su propio broker** (ya no el público): publicar y recibir contra el Mosquitto del compose.

Punteros:
- Conceptos: imagen vs contenedor, `Dockerfile`, `docker-compose`.
- Imágenes oficiales: `python`, `eclipse-mosquitto`, `postgres`. El broker no se instala: se baja como imagen. Docker es *cómo conseguís* el broker.
- `mosquitto_pub` / `mosquitto_sub` contra el broker del compose; topics y wildcards.
- Ojo con la red entre contenedores: dentro del compose, los servicios se llaman por su **nombre de servicio**, no por `localhost`.

### Clase 4 — El capstone: cerrar el circuito

**Objetivo:** conectar todo. El dispositivo simulado, el broker, el consumidor, la API y la base, funcionando juntos.

Al final de la clase tiene que estar andando: **el sistema completo descrito arriba.** Un dato nace en el dispositivo simulado y termina guardado en la base, pasando por MQTT y por la API.

Punteros:
- `paho-mqtt` para el dispositivo simulado (publisher) y para el consumidor (subscriber).
- El consumidor llama a la API con `requests` por cada mensaje.
- Todo dentro del `docker-compose` de la clase 3, sumando los dos servicios nuevos.

Va a fallar en varios lugares antes de andar. Eso es esperable y es la parte que más enseña. Cuando finalmente vean el dato del dispositivo aparecer en la base después de pelearla, ese es el objetivo de la materia cumplido.

---

## Entrega de los ejercicios (repo individual)

Los ejercicios de cada clase (`ejercicios/ejercicios-N.md`) **no** se entregan en el repo del equipo: van en un repo de GitHub **propio de cada alumno**, separado del repo del capstone.

- **Nombre del repo:** `IC-IC2-apellido-fecha_de_la_practica`, con la fecha en formato `AAAA-MM-DD` (la fecha de la clase en la que se hace la práctica). Ejemplo: `IC-IC2-perez-2026-08-03`.
- **Un Pull Request por cada Parte** de `ejercicios-N.md` (un PR para la Parte A, otro para la Parte B, y así). Nada de un PR gigante con todo junto, ni uno por cada ejercicio suelto.
- Cada PR se **mergea a `main` desde GitHub** (botón *Merge*), no por consola.
- **Un commit directo a `main`, sin pasar por un PR, no se considera entregado.** Si el docente corrige y ve que algo llegó a `main` sin su PR correspondiente, es como si no existiera.

Esto es intencional: es la primera práctica real del flujo rama → Pull Request → merge, que es como se trabaja en cualquier equipo de verdad (y es distinto del flujo de push directo que usan en el repo del equipo para el capstone).

## Entregas y trabajo en equipo (el capstone)

- **Material para clonar:** [`Universidad-Nacional-de-Rafaela/IC-ingenieria-computacion-2`](https://github.com/Universidad-Nacional-de-Rafaela/IC-ingenieria-computacion-2) — consignas y ejercicios (se va sumando clase a clase).
- Todo vive en el **repo del equipo** en GitHub (uno propio, creado por ustedes — no es el repo de material de arriba, ni el repo individual de ejercicios). Lo que no está commiteado, no existe.
- Commits seguido y con mensajes que digan qué hicieron.
- Cada clase tiene que cerrar con su pieza andando y subida.
- El README del repo tiene que explicar cómo levantar el sistema. Si otro no puede levantarlo siguiendo el README, no está terminado.
