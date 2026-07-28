---
name: cierre-de-llamada
description: Convierte la transcripción de una llamada comercial en el seguimiento completo: resumen para el CRM, estado del negocio, tareas con dueño y fecha, correo de seguimiento redactado, recordatorio del próximo toque, aviso al líder comercial, y qué funcionó / qué no. Úsalo cuando el usuario diga /cierre, "acabo de tener una llamada", "pega esta transcripción", "arma el seguimiento", "qué sigue con este cliente", o pegue el texto de una llamada de ventas. NO es para reuniones internas de equipo ni para notas personales.
---

# Cierre de llamada

Entra una llamada. Sale el seguimiento completo. Sin inventar nada.

## Regla de oro

**Todo lo que escribas tiene que estar en la transcripción.** Si un dato no está, escribe `[FALTA: qué preguntar]`. Nunca lo adivines.

Aplica a: montos, fechas, nombres, cargos, plazos, condiciones, objeciones, compromisos.

Un seguimiento con un dato inventado es peor que uno incompleto. El cliente detecta el error, no la eficiencia.

## Paso 1. Conseguir la llamada

En orden, lo primero que exista:

1. El usuario pegó la transcripción en el chat → úsala.
2. El usuario dio la ruta de un archivo (`.txt`, `.md`, `.vtt`, `.srt`) → léela.
3. Hay archivos en `transcripciones/` → usa el más reciente y di cuál elegiste.
4. Nada de lo anterior → pide una sola cosa:

> Pégame la transcripción de la llamada. Si no la grabaste, cuéntame en voz alta qué pasó y pega ese texto. Sirve igual.

No sigas sin llamada. No armes un ejemplo.

## Paso 2. Leer completo antes de escribir

Lee toda la transcripción primero. Marca:

- Quién habla y de qué lado está (cliente / vendedor).
- Qué pidió el cliente, en sus palabras exactas.
- Qué objetó, en sus palabras exactas.
- Qué prometió el vendedor y para cuándo.
- Cómo terminó (cerró / no cerró / quedó en algo).

Las palabras exactas del cliente son el activo. Cítalas entre comillas donde puedas.

## Paso 3. Escribir los 7 bloques

Formato exacto en `references/formato.md`. Léelo antes de escribir.

Los 7, siempre, en este orden:

1. **RESUMEN**: 5 líneas máximo, listo para pegar en el CRM.
2. **ESTADO DEL NEGOCIO**: cerró / no cerró / en seguimiento, monto, objeción principal.
3. **TAREAS**: cada una con dueño, fecha y hora.
4. **CORREO DE SEGUIMIENTO**: borrador listo para enviar, en el idioma del cliente.
5. **RECORDATORIO**: fecha y hora exactas del próximo toque.
6. **AVISO AL LÍDER COMERCIAL**: un párrafo, lo que el jefe necesita saber sin escuchar la llamada.
7. **QUÉ FUNCIONÓ / QUÉ NO**: dos listas cortas. Esto es lo que después entrena al resto del equipo.

## Paso 4. Guardar

Escribe todo en `seguimientos/YYYY-MM-DD-<cliente>.md`.

- Crea la carpeta si no existe. La primera vez Claude Code va a pedir permiso para escribir. Es normal, es una sola vez.
- `<cliente>` en minúsculas, sin espacios ni tildes (`banco-del-norte`).
- Si el archivo ya existe, agrega al final bajo `## Segunda llamada` en vez de sobreescribir.
- Al terminar, di la ruta exacta del archivo.

Nombres de archivo que funcionan igual en Windows, Mac y Linux. Del nombre del cliente quita siempre: acentos, ñ, espacios, y los caracteres `\ / : * ? " < > |`. Reemplázalos por guión. Nunca uses rutas absolutas ni `~`: siempre `seguimientos/` relativo a la carpeta donde está trabajando el usuario.

`seguimientos/` está en `.gitignore`. Las conversaciones con tus clientes se quedan en tu máquina.

## Paso 5. Cerrar con el siguiente paso

Termina con una sola línea: la acción más próxima en el tiempo, con su fecha y hora.

Nada de resúmenes del resumen.

## Cuando ya tienes varias llamadas

Con 3 o más archivos en `seguimientos/`, el usuario puede preguntar cosas cruzadas:

- "Qué objeción se repite más"
- "Qué dije en las llamadas que sí cerraron y no dije en las que no"
- "Cuántos seguimientos tengo vencidos"

Respóndelas leyendo los archivos de `seguimientos/`. Solo esos. Si la pregunta necesita algo que no está ahí (correos, CRM, propuestas, llamadas de otra persona del equipo), dilo claro:

> Eso no lo puedo responder con lo que hay en esta carpeta. Aquí solo viven las llamadas que tú procesaste.

No inventes el resto. El límite es real y decirlo es parte del trabajo.
