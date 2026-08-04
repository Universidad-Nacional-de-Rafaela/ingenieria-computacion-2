# Ejercicios — Clase 1: Python y Git

> **Para alumnos.** Practiquen la habilidad, no copien soluciones. Cada ejercicio trae un **"Listo cuando…"** para que ustedes mismos se den cuenta de si está bien.
> Todos los ejercicios usan dominios cualquiera (juegos, música, cine…) **a propósito**: el sistema de sensores de la materia lo van a construir de cero más adelante, no acá.
>
> Niveles: 🟢 calentamiento · 🟡 núcleo · 🔴 desafío (más abierto).
> Regla de oro: si resolvés algo pegando un comando que no entendés, no cuenta. Entendé *por qué* funciona.
>
> **Hay ejercicios de sobra a propósito.** Si tu grupo va rápido, seguí bajando por la lista — no hace falta avisar al profe para que les invente algo más. Lo único obligatorio es el checkpoint de cierre que les marquen los docentes; todo lo demás es para no parar nunca de practicar.
>
> **Cómo se entrega:** estos ejercicios van en tu **repo individual** `IC-IC2-apellido-fecha_de_la_practica` (no en el repo del equipo). **Un Pull Request por cada Parte** (A, B, C…), mergeado a `main` desde GitHub. Un commit directo a `main` sin PR no cuenta como entregado. Ver el detalle en [`../../consignas.md`](../../consignas.md).

---

## Parte A — Python: tipos, variables, operaciones

### 🟢 A1 — Calculadora de promedio
Tenés las notas de un alumno: `7, 4, 9, 10, 6`. Calculá e imprimí el promedio. Después imprimí si **aprobó** (promedio ≥ 6) o no.
**Listo cuando:** imprime el promedio correcto y el cartel de aprobado/desaprobado.

### 🟢 A2 — El tipo importa
Creá una variable `cantidad = "5"` (con comillas) y otra `precio = 100`. Hacé `cantidad * precio` e imprimí el resultado — **no da un error**, pero tampoco da lo que uno esperaría de una multiplicación. Después arreglalo para que dé `500`.
**Listo cuando:** entendés *por qué* `"5" * 100` no explota pero tampoco multiplica, y por qué la versión arreglada sí da `500`. (Pista: `type(cantidad)`.)

### 🟢 A3 — Conversión de temperatura
Pedí (o fijá) una temperatura en Celsius e imprimí su equivalente en Fahrenheit (`F = C * 9/5 + 32`).
**Listo cuando:** 0 °C da 32 °F y 100 °C da 212 °F.

### 🟡 A4 — Redondeo y formato
Mostrá el promedio de A1 con **un solo decimal** (ej. `7.2`, no `7.200000001`).
**Listo cuando:** la salida tiene exactamente un decimal.

### 🟢 A5 — ¿Mayor o menor de edad?
Dada una variable `edad`, imprimí `"mayor de edad"` o `"menor de edad"` según corresponda. Probalo con `17`, `18` y `0`.
**Listo cuando:** el caso límite (`18`) da el resultado correcto sin que lo hayas mirado dos veces.

### 🟡 A6 — Par, impar, y turnos
Tenés 30 alumnos numerados del 1 al 30. Usando el operador `%` (módulo), separalos en dos grupos: los de número par y los de número impar. Imprimí cuántos hay en cada grupo.
**Listo cuando:** los dos grupos suman 30 y entendés qué hace `%` (no es una división normal).

### 🔴 A7 — Cadena de conversiones
Encadená conversiones de unidades: de kilómetros a millas, y de millas a pies (buscá los factores de conversión). Escribí el camino completo `km → millas → pies` para un valor cualquiera, sin escribir tres scripts sueltos.
**Listo cuando:** podés cambiar el valor de entrada una sola vez y las tres conversiones se actualizan solas.

---

## Parte B — Listas

### 🟢 B1 — Playlist
Hacé una lista con 5 canciones. Imprimila entera, después imprimí solo la primera y la última.
**Listo cuando:** podés acceder a cualquier posición sin error.

### 🟢 B2 — Sumar a la lista
Agregá dos canciones más a la playlist de B1 **después** de crearla. Imprimí cuántas canciones tiene ahora.
**Listo cuando:** la lista crece y `len()` lo confirma.

### 🟡 B3 — El más alto y el más bajo
Dada la lista de puntajes `[120, 45, 300, 80, 210]`, imprimí el mayor, el menor y el promedio. **No uses** `max()`/`min()` la primera vez: hacelo con un `for`. Después comparalo con `max()`/`min()`.
**Listo cuando:** tu versión con `for` da lo mismo que la de las funciones.

### 🟡 B4 — Filtrar
De la lista `[120, 45, 300, 80, 210]`, armá una **lista nueva** solo con los puntajes mayores a 100.
**Listo cuando:** la lista nueva tiene `[120, 300, 210]` y la original quedó intacta.

### 🔴 B5 — Ranking
Dada una lista de puntajes, imprimila **ordenada de mayor a menor**. Investigá cómo ordenar una lista en Python.
**Listo cuando:** sale ordenada y entendés la diferencia entre ordenar la lista en su lugar y obtener una copia ordenada.

### 🟢 B6 — Al revés
Dada la playlist de B1, imprimila **en orden inverso** sin escribir un `for` que la recorra al revés a mano. Investigá el slicing `[::-1]`.
**Listo cuando:** la lista sale invertida y la original sigue en su orden normal.

### 🟡 B7 — Sin repetidos
Dada la lista `[3, 5, 3, 8, 5, 1, 8, 8]`, obtené una lista de los valores **sin repetir**. Investigá `set()`.
**Listo cuando:** no quedan duplicados. El orden no importa y **no tiene por qué coincidir con el de tu compañero** — `set()` no garantiza ningún orden particular, eso es normal.

### 🔴 B8 — Promedio móvil
Dada una lista de 10 lecturas cualquiera, calculá el **promedio de a 3 elementos consecutivos** (posiciones 0-1-2, después 1-2-3, después 2-3-4…). Esto se llama ventana deslizante.
**Listo cuando:** la lista de promedios tiene 2 elementos menos que la original y podés explicar por qué.

---

## Parte C — Diccionarios (¡la forma del JSON que viene!)

### 🟢 C1 — Una ficha
Creá un diccionario que represente una película: `titulo`, `anio`, `director`. Imprimí solo el título.
**Listo cuando:** accedés a un campo por su clave.

### 🟢 C2 — Agregar y cambiar
A la película de C1, agregale el campo `puntaje` y después cambiale el `anio`. Imprimí el diccionario completo.
**Listo cuando:** el diccionario muestra los cambios.

### 🟡 C3 — Clave que no existe
Intentá acceder a `pelicula["duracion"]` (que no existe) y mirá el error. Después conseguí que, si la clave no está, devuelva `"desconocido"` en vez de romper. Investigá `.get()`.
**Listo cuando:** no se rompe aunque la clave falte.

### 🟡 C4 — Lista de diccionarios
Armá una lista de **3 películas** (cada una un diccionario como C1). Recorrela con un `for` e imprimí solo los títulos.
**Listo cuando:** imprime los 3 títulos. (Esto es *exactamente* la forma en que la API te va a devolver datos en la clase 2.)

### 🔴 C5 — Búsqueda
Sobre la lista de C4, escribí código que imprima las películas de un director dado. Si en C4 guardaste el nombre completo (ej. `"Christopher Nolan"`), buscar por el nombre completo exacto (`==`) no va a encontrar nada si buscás solo `"Nolan"` — son strings distintos. Elegí una de las dos y probá que ande: (a) comparación exacta con el nombre completo, o (b) `"Nolan" in pelicula["director"]` para que matchee por coincidencia parcial. Si no hay ninguna, que avise.
**Listo cuando:** encuentra las que matchean con el criterio que elegiste y maneja el caso "ninguna".

### 🟢 C6 — Combinar fichas
Tenés dos diccionarios de la misma película con datos distintos, ej. `{"titulo": "Dune", "anio": 2021}` y `{"puntaje": 8, "anio": 2024}`. Combinalos en uno solo. ¿Qué pasa con `anio`, que está en los dos? Investigá `.update()` o el operador `|`.
**Listo cuando:** entendés qué valor "gana" cuando una clave se repite — y que depende del **orden** en que combines los diccionarios (`dict1 | dict2` no da lo mismo que `dict2 | dict1`; con `.update()` pasa lo mismo según a cuál le hacés `.update()` de cuál). No hay una única respuesta "correcta" de qué año queda, lo importante es que sepas explicar por qué quedó ese.

### 🟡 C7 — Contador de palabras
Dada una frase cualquiera, armá un diccionario que cuente cuántas veces aparece cada palabra.
**Listo cuando:** el diccionario tiene una clave por palabra distinta y el número correcto de apariciones.

### 🔴 C8 — Diccionario anidado
Armá un "inventario de tienda": un diccionario donde cada clave es un producto y el valor es *otro diccionario* con `precio` y `stock`. Accedé al precio de un producto específico sin recorrer nada, solo encadenando claves.
**Listo cuando:** llegás al dato con `inventario["producto"]["precio"]` y entendés por qué es un dict "de dos pisos".

---

## Parte D — Funciones

### 🟢 D1 — Encapsular
Convertí el cálculo de promedio (A1) en una **función** `promedio(notas)` que reciba una lista y devuelva el número. Probala con dos listas distintas.
**Listo cuando:** la misma función sirve para cualquier lista.

### 🟡 D2 — ¿Aprobó?
Escribí `aprobo(notas)` que use `promedio()` por dentro y devuelva `True`/`False`.
**Listo cuando:** una función usa a la otra (las funciones se combinan).

### 🔴 D3 — Estadísticas
Escribí `estadisticas(notas)` que devuelva un **diccionario** con `promedio`, `maximo` y `minimo`.
**Listo cuando:** una sola llamada te da las tres cosas en un dict.

### 🟢 D4 — Parámetro por default
Escribí `aprobo(notas, minimo=6)` donde el umbral de aprobación tiene un valor por default pero se puede cambiar. Probala sin pasar `minimo` y pasando `minimo=7`.
**Listo cuando:** funciona de las dos formas sin duplicar código.

### 🟡 D5 — Que no explote con la lista vacía
Llamá a `promedio([])`. Va a fallar (`ZeroDivisionError`). Decidí qué debería pasar en ese caso (¿devolver `0`? ¿avisar con un mensaje?) y programalo.
**Listo cuando:** `promedio([])` ya no revienta el programa, y elegiste a propósito qué hace en su lugar.

### 🔴 D6 — Reporte combinado
Escribí `reporte(notas)` que use `estadisticas()` por dentro y devuelva un **texto** ya armado, tipo: `"Promedio: 7.2 | Máximo: 10 | Mínimo: 4"`.
**Listo cuando:** una sola llamada te da el texto final, combinando lo que ya hicieron D1-D3.

---

## Parte E — Leer datos de un archivo (CSV)

> Para estos: creen a mano un archivo `peliculas.csv` con unas líneas tipo `titulo,anio,puntaje` y datos inventados.

### 🟡 E1 — Leer y mostrar
Abrí el CSV y mostrá cada línea por pantalla.
**Listo cuando:** ves el contenido del archivo desde Python.

### 🟡 E2 — Cuidado: todo viene como texto
Sumá la columna `puntaje` de todas las películas. Vas a chocar con que los números vienen como **texto**. Resolvelo.
**Listo cuando:** la suma da un número y entendés por qué había que convertir.

### 🔴 E3 — Reporte
Imprimí: cuántas películas hay, el puntaje promedio, y el título de la mejor puntuada.
**Listo cuando:** los tres datos salen correctos del archivo real.

### 🟡 E4 — Filtrar y guardar
Agregale una columna `genero` **al mismo** `peliculas.csv` que ya venís usando desde E1 (no crees un archivo nuevo con otro nombre — si lo hacés, terminás con dos versiones del dataset y los resultados de E1-E3 y E4-E5 dejan de coincidir). Editalo a mano. Leé el archivo, quedate solo con las películas de un género elegido, y escribí un **nuevo CSV** (`filtradas.csv`) solo con esas.
**Listo cuando:** el nuevo CSV existe, tiene menos filas que el original (que ahora incluye la columna `genero`), y lo pueden abrir y verificar a ojo.

### 🔴 E5 — Agrupar por categoría
Usando el CSV con `genero` de E4, calculá el **puntaje promedio por género** (un diccionario `{genero: promedio}`).
**Listo cuando:** cada género del archivo aparece una vez en el resultado, con su promedio correcto.

---

## Parte F — Git y GitHub (en equipo)

> Estos se hacen **con el repo del equipo**, no solos. La meta es que el flujo se vuelva natural.

### 🟢 F1 — El ciclo completo
Cloná el repo, creá un archivo `notas-equipo.md` con sus nombres, y hacé `add` → `commit` → `push`. Que el de al lado haga `pull` y vea tu archivo.
**Listo cuando:** tu cambio aparece en la máquina del compañero.

### 🟢 F2 — Mensajes que sirven
Hacé 3 commits con mensajes que un desconocido entendería (no "cambios", no "asd"). Mirá el historial con `git log`.
**Listo cuando:** el log se lee como una historia de qué pasó.

### 🟡 F3 — `.gitignore`
Activá un `venv` en el repo. Fijate que Git lo quiere subir. Hacé que Git lo **ignore** con un `.gitignore`.
**Listo cuando:** `git status` ya no muestra el `venv`.

### 🔴 F4 — Provocá un merge conflict (a propósito)
Dos integrantes editan **la misma línea** del mismo archivo, ambos commitean, ambos intentan pushear. El segundo va a tener que hacer `pull` y resolver el conflicto a mano.
**Listo cuando:** resolvieron el conflicto entendiendo qué versión quedó (o cómo combinar ambas), y el repo quedó limpio. *Esto es un rito de pasaje: que pase ahora con algo trivial.*

### 🔴 F5 — Volver atrás
Hacé un cambio que rompa algo, commiteá, y después usá Git para ver el historial y entender cómo volverías a la versión anterior.
**Listo cuando:** sabés mirar versiones pasadas y entendés qué commit es cuál.

### 🟢 F6 — Una rama propia
Creá una rama nueva (`git branch` + `git checkout`, o `git checkout -b`), hacé un commit ahí adentro (ej. agregar tu nombre a un archivo), y después volvé a `main`. Fijate que ese cambio **no está** en `main`.
**Listo cuando:** entendés que una rama es una línea de trabajo separada hasta que decidís unirla.

### 🟡 F7 — Traer la rama de vuelta
Sobre la rama de F6, hacé el merge a `main` (`git merge`). Si no hay conflicto, tiene que ser directo.
**Listo cuando:** el cambio que hiciste en la rama ahora aparece en `main`.

### 🔴 F8 — Guardar sin commitear (`stash`)
Empezá un cambio a medio hacer (sin commitear), y necesitás cambiar de rama urgente sin perderlo ni commitearlo a medias. Investigá `git stash` y `git stash pop`.
**Listo cuando:** cambiaste de rama y volviste, y tu cambio a medio hacer seguía ahí, intacto.

---

## Parte G — Testear con pytest (que el código se pruebe solo)

> Hasta acá, para saber si una función andaba bien, la llamaban y miraban el `print` a ojo. Un **test automático** hace esa verificación por ustedes, cada vez, sin que la miren a mano. `pytest` es la herramienta más usada en Python para esto.
>
> Mecánica mínima: instalar con `pip install pytest` (adentro del `venv`), crear un archivo `test_algo.py`, adentro escribir funciones que empiecen con `test_` y usen `assert` para afirmar algo que tiene que ser verdad. Correr `pytest` en la terminal y leer el resultado.

### 🟢 G1 — Tu primer test
Escribí un archivo `test_promedio.py` que importe tu función `promedio()` (de D1) y tenga un test que verifique que `promedio([7, 4, 9, 10, 6])` da el valor esperado. Corré `pytest` y mirá la salida.
**Listo cuando:** `pytest` corre y muestra `1 passed`.

### 🟢 G2 — Un test que falla a propósito
Escribí un test con un `assert` que sepas de antemano que va a fallar (comparalo contra un valor incorrecto). Corré `pytest` y leé el output en rojo. **Una vez que lo entendiste, comentá o borrá ese test** — no tiene que quedar fallando en la versión final que subís, o cada corrida de `pytest` de ahí en adelante (incluso en G3-G8) va a mostrar un fallo que no es un bug real.
**Listo cuando:** entendés qué información te da pytest cuando un test falla — no solo "falló", sino con qué valor esperaba y cuál obtuvo — y tu repo final queda con todos los tests en verde.

### 🟡 G3 — Varios casos, varios tests
Escribí al menos 3 tests para `aprobo()` (D2): un caso que aprueba, uno que no aprueba, y uno "al límite" (promedio exactamente 6).
**Listo cuando:** los 3 tests pasan y cada uno prueba una situación distinta, caso límite incluido.

### 🟡 G4 — Testear un diccionario
Escribí un test para `estadisticas()` (D3) que verifique que el diccionario devuelto tiene las claves `promedio`, `maximo` y `minimo`, con los valores correctos.
**Listo cuando:** el test chequea las tres claves, no solo una.

### 🟡 G5 — Testear el caso raro
Para tu función de C3 (la que usa `.get()` con un valor por default), escribí un test que pruebe justo el caso de la clave que no existe.
**Listo cuando:** el test prueba el caso "falta el dato", no solo el caso feliz donde todo está.

### 🔴 G6 — El caso límite que decidiste en D5
Escribí un test para la decisión que tomaste en D5 sobre `promedio([])` (lista vacía). El test tiene que confirmar exactamente el comportamiento que elegiste.
**Listo cuando:** el test documenta, con código, qué decidiste que pasa en ese caso raro.

### 🔴 G7 — Un solo test, varios casos (`parametrize`)
Investigá `@pytest.mark.parametrize` y reescribí los 3 tests de G3 como **un solo test** parametrizado con varios casos de entrada/salida.
**Listo cuando:** un solo test corre varios casos y pytest te muestra cuántos pasaron (más de 1, de un solo bloque de código).

### 🔴 G8 — Los tests viajan con el repo
Sumá tus archivos `test_*.py` al repo del equipo, con un commit que diga qué testean. Que un compañero clone el repo (o haga `pull`) y corra `pytest` sin que vos le expliques nada.
**Listo cuando:** el compañero corre `pytest` desde su clon y ve los mismos tests pasar, sin que vos intervengas.

---

## Cierre del día (juntando todo)

### 🔴 H1 — Mini-proyecto en el repo
En equipo, dejen en el repo un script de Python que: lea el `peliculas.csv`, calcule estadísticas (Parte E + D), y lo imprima ordenado (Parte B). Sumen **al menos 2 tests con pytest** que prueben las funciones de estadísticas. Que **todos** hayan commiteado algo. El README del repo tiene que explicar cómo correr el script y cómo correr los tests.
**Listo cuando:** otra persona clona el repo, sigue el README, el script corre y `pytest` pasa, sin que ustedes le expliquen nada.

### 🔴 H2 — ¿Cuánto confiás en tu propio código?
Sin usar todavía herramientas de cobertura: mirá tu script del H1 función por función y preguntate "si alguien la rompe sin querer, ¿algún test se daría cuenta?". Donde la respuesta sea no, agregá el test que falte.
**Listo cuando:** para cada función del script, hay al menos un test que la cubre — y pueden justificar por qué ese test alcanza.
