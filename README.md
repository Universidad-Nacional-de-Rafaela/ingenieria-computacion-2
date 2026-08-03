# Ingeniería en Computación 2 — Bloque de Software

Material para alumnos del bloque de software de la materia: Python sobre Raspberry Pi, comunicaciones (APIs y MQTT) y todo corriendo en contenedores.

## Cómo se trabaja

1. **Clonen este repo** para tener las consignas y los ejercicios de la clase.
2. **Cada equipo crea su propio repositorio** en GitHub (privado o público, como prefieran) para el trabajo del bloque: ahí van a vivir sus scripts, su API, su `docker-compose`, y el historial de commits de todos los integrantes.
3. Al cierre de cada clase, avisen a los docentes el link a su repo — es lo que se corrige.

**Esto se construye de cero.** No hay esqueleto para completar, no hay código pre-armado. Arrancan de un repo vacío y de una consigna. Ver el detalle de la filosofía en [`consignas.md`](consignas.md).

## Estructura

| Carpeta / archivo | Contenido |
|---|---|
| [`consignas.md`](consignas.md) | El problema bien definido: el objetivo del capstone completo (las 4 clases) y qué tiene que estar andando al final de cada una. |
| [`contenido-por-clase/clase-1.md`](contenido-por-clase/clase-1.md) | El material conceptual de la Clase 1 (lectura abierta, sin código-solución). |
| [`contenido-por-clase/ejercicios/ejercicios-1.md`](contenido-por-clase/ejercicios/ejercicios-1.md) | Ejercicios de la Clase 1, en tres niveles (🟢 calentamiento · 🟡 núcleo · 🔴 desafío), en dominios paralelos para practicar sin construirles el capstone. |

> **Solo Clase 1 publicada por ahora.** El material de las clases 2 a 4 se va a sumar a este repo antes de cada clase.

## El objetivo final (el capstone)

Un dispositivo publica lecturas por MQTT, un consumidor las levanta usando una API propia, y la API las persiste en una base de datos. Todo levantado con un solo comando, en contenedores. El detalle completo está en [`consignas.md`](consignas.md).

## Stack del bloque

- **Lenguaje:** Python (sobre Raspberry Pi).
- **API:** FastAPI.
- **Mensajería:** MQTT con broker Mosquitto, cliente `paho-mqtt`.
- **Contenedores:** Docker y `docker-compose`.
- **Base de datos:** PostgreSQL.
- **Testing:** `pytest`.
- **Control de versiones:** Git + GitHub (repo por equipo).

## Material relacionado

- **[ic-git-por-etapas](https://github.com/Universidad-Nacional-de-Rafaela/ic-git-por-etapas)** — el track de Git por etapas (etapas 1 a 5, ejercicios, rúbrica) para la parte de Git de la clase 1.
