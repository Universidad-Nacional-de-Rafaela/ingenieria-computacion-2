# Clase 1 — Python y Git

> **Material para alumnos**: conceptos, lectura abierta, sin código-solución.
> Acompaña a [`../consignas.md`](../consignas.md) (el qué).
> **Ejercicios de esta clase:** [`ejercicios/ejercicios-1.md`](ejercicios/ejercicios-1.md).

---

## Para alumnos — los conceptos

### De dónde venimos y qué construimos hoy

Hoy arrancamos con **Python sobre la computadora** (y después sobre la Raspberry Pi). Y arrancamos el **repositorio del equipo**, que es donde va a vivir *todo* el sistema que armen en las 4 clases.

La pieza que dejan andando hoy:
- Un **script de Python** que resuelve un problema con datos reales.
- El **repo del equipo en GitHub**, con commits de todos.

No es un día de "hola mundo": es el día en que empiezan a pensar en un sistema que crece y que comparten entre varios.

### Concepto 1 — Las tres cosas que más los van a marear al principio

- **Tipado dinámico.** Escriben `x = 5` y listo: la variable no tiene un tipo fijo declarado, lo toma del valor. Eso es cómodo… hasta que `x` termina siendo un texto cuando ustedes creían que era un número. El tipo existe (Python es fuertemente tipado *en tiempo de ejecución*), pero no lo declaran: lo descubren cuando algo explota.
- **La indentación ES la sintaxis.** Python **no tiene llaves**: lo que está adentro de un `if`, un `for` o una función se define *por cuánto está sangrado*. Mezclar espacios y tabs, o sangrar de más, es un error de verdad (`IndentationError`), no un detalle estético.
- **Listas y diccionarios.** Python tiene **listas** (`[ ]`, crecen solas) y **diccionarios** (`{ }`, pares clave-valor). Presten atención al diccionario: es exactamente la forma de un **JSON**, que es como van a viajar los datos en las clases que vienen. El que entiende dicts hoy, entiende JSON en la clase 2 sin esfuerzo.

### Concepto 2 — El entorno virtual (`venv`): por qué aislar

Cuando instalan una librería con `pip`, ¿dónde queda? Si la instalan "para toda la máquina", el proyecto de hoy y el de la materia que viene se pisan las versiones. Un **entorno virtual** es una cajita por proyecto: las librerías que instalen ahí adentro no molestan a nada de afuera, y se pueden listar para que otra persona reproduzca exactamente lo mismo.

> **Semilla para más adelante (eventos):** en Python van a ver código que **reacciona a un evento** en vez de ejecutarse en orden de arriba a abajo. Hoy no lo tocan; queda anotado. En la clase 4 lo van a ver concreto, cuando un programa reaccione solo a cada mensaje que llega.

### Concepto 3 — Git: por qué existe el control de versiones

Hasta ahora un proyecto era una carpeta con archivos. Si lo rompían, perdían lo de antes. Si trabajaban de a varios, se mandaban el código por mail y era un caos.

**Git** resuelve eso: guarda una *foto* (un `commit`) cada vez que ustedes deciden, con un mensaje que dice qué cambiaron. Pueden volver atrás, ver quién tocó qué, y —lo importante para un equipo— **trabajar todos sobre el mismo proyecto** sin pisarse. **GitHub** es el lugar en la nube donde vive esa historia compartida.

El ciclo básico que van a repetir mil veces:
1. `clone` — traen el repo a su máquina (una sola vez).
2. trabajan, editan archivos.
3. `add` — eligen qué cambios entran en la próxima foto.
4. `commit` — sacan la foto, con un mensaje.
5. `push` — suben sus fotos a GitHub.
6. `pull` — bajan las fotos que subieron los compañeros.

### Concepto 4 — El primer merge conflict (no es un error, es un rito)

Cuando dos personas editan **la misma línea** del mismo archivo, Git no sabe cuál versión gana, así que **les pregunta a ustedes**. Eso es un *merge conflict*. Da miedo la primera vez porque aparece un texto raro con `<<<<<<<`, `=======` y `>>>>>>>` en el archivo. No está roto: Git les está mostrando las dos versiones para que elijan. Resolverlo es: borrar las marcas, dejar la versión correcta, y commitear. **Que les pase hoy con algo trivial es lo mejor que les puede pasar** — mucho mejor que en la clase 4 con el sistema entero.

### Concepto 5 — Probar que anda: `pytest`

Hasta ahora, para saber si una función estaba bien, la llamaban y miraban el `print` a ojo. Eso no escala: cuando el script crezca (y va a crecer, clase tras clase), revisar todo a mano cada vez que tocan algo es lento y se les va a escapar un error.

Un **test automático** es código que verifica código: llama a la función con un caso conocido y afirma (`assert`) que el resultado es el esperado. `pytest` es la herramienta estándar de Python para esto. La mecánica mínima:

1. `pip install pytest` (adentro del `venv`, como cualquier librería).
2. Un archivo `test_algo.py` con funciones que empiecen con `test_`.
3. Adentro, un `assert` que compara lo que la función devuelve contra lo que ustedes esperan.
4. Correr `pytest` en la terminal: verde si todo pasa, rojo con detalle si algo falla.

No es una clase de testing a fondo — es la semilla. Lo que importa hoy es la idea: **en vez de mirar la salida una vez, dejan escrita la verificación para que se repita sola**, cada vez que cambian el código. Van a volver a usar esto en las clases que vienen, cuando el sistema tenga más piezas y "mirarlo a ojo" ya no alcance.

### Vocabulario nuevo

| Término | Qué es |
|---|---|
| **REPL / intérprete** | Python ejecuta línea por línea, sin un paso de compilación previo. |
| **`venv`** | Entorno virtual: la cajita de librerías aislada por proyecto. |
| **`pip`** | El instalador de librerías de Python. |
| **`requirements.txt`** | La lista de librerías (con versión) que necesita el proyecto. |
| **commit** | Una foto del proyecto en un momento, con mensaje. |
| **push / pull** | Subir / bajar commits a GitHub. |
| **merge conflict** | Git no puede decidir entre dos cambios sobre la misma línea y les pide que elijan. |
| **`.gitignore`** | Lista de cosas que Git NO debe guardar (el `venv`, archivos basura). |
| **`pytest`** | Herramienta que corre tests automáticos: funciones `test_*` con `assert` adentro. |
| **`assert`** | Afirma que algo tiene que ser verdad; si no lo es, el test falla ahí mismo. |

### Para investigar (punteros, no soluciones)

- Documentación oficial de Python: tipos, listas, diccionarios.
- Cómo crear y activar un `venv`, y cómo congelar dependencias en `requirements.txt`.
- El flujo `clone → add → commit → push → pull` y cómo se ve un merge conflict.
- `pytest`: cómo se instala, cómo se nombra un archivo de test, qué hace `assert`.
- Si quieren tocar la GPIO de la RPi desde Python: la librería `gpiozero`. Track de Git por etapas del equipo: [`ic-git-por-etapas`](https://github.com/Universidad-Nacional-de-Rafaela/ic-git-por-etapas).

