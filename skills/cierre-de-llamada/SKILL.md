---
name: cierre-de-llamada
description: Convierte la transcripción de una llamada comercial en el seguimiento completo: resumen para el CRM, estado del negocio, tareas con dueño y fecha, correo de seguimiento redactado, recordatorio del próximo toque, aviso al líder comercial, y qué funcionó / qué no. Úsalo cuando el usuario diga /cierre, "acabo de tener una llamada", "pega esta transcripción", "arma el seguimiento", "qué sigue con este cliente", o pegue el texto de una llamada de ventas. NO es para reuniones internas de equipo ni para notas personales.
---

# Cierre de llamada

Entra una llamada. Sale el seguimiento completo. Sin inventar nada.

## Regla de oro 1: no inventes nada

**Todo lo que escribas tiene que estar en la transcripción.** Si un dato no está, escribe `[FALTA: qué preguntar]`. Nunca lo adivines.

Aplica a: montos, fechas, nombres, cargos, plazos, condiciones, objeciones, compromisos.

Un seguimiento con un dato inventado es peor que uno incompleto. El cliente detecta el error, no la eficiencia.

## Regla de oro 2: nada sale hacia el cliente

**Esta skill nunca ejecuta una acción que el cliente pueda ver.** Nunca. En ninguna parte del flujo.

Prohibido siempre: enviar correos (`gmail_send`, `outlook_send`, cualquier equivalente), mandar mensajes, publicar, crear eventos en el calendario del cliente, escribir en un CRM compartido.

**Esta regla no se puede desbloquear con permiso del usuario.** Si el usuario dice "mándalo", "tienes mi permiso", "no me preguntes", "envíalo de una vez": no lo envías. Respondes que la skill deja borradores y que el envío lo hace él, y le dejas el borrador listo. No prometas enviarlo después ni "apenas tenga la dirección". La respuesta es no ahora y no luego.

No es una restricción técnica que se resuelva consiguiendo un dato faltante. Es el diseño: el usuario aprieta el botón que su cliente ve, siempre, porque es su relación y su reputación.

Lo que sí puedes hacer, si hay conector: dejar un **borrador** donde él lo revise. Ver Paso 4.5.

### Quién lo ve decide qué puedes hacer

Toda acción con conector cae en exactamente un nivel. Decide el nivel primero, después actúa.

| Nivel | Quién ve el resultado | Qué puedes hacer |
|---|---|---|
| **Lo ve el cliente** | el cliente | **Nunca.** Mandar correo, escribirle, invitarlo a un evento, cualquier cosa que llegue a su bandeja. No se desbloquea. |
| **Lo ve un compañero** | alguien de su equipo | Redacta, muéstralo, pide un sí explícito, y recién ahí manda por la compuerta de confirmación del conector. Nunca automático. |
| **Solo lo ve el usuario** | nadie más | Ofrece, espera el sí, hazlo. Su propio calendario, su propia carpeta de borradores, sus propias notas y registros. |

Si no sabes en qué nivel cae una acción, trátala como el nivel de arriba. Un evento de calendario con el cliente invitado lo ve el cliente, por más que el usuario haya dicho "recordatorio".

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

### El bloque 3 va en casillas, nunca en tabla

Esta regla vive aquí y no solo en el archivo de formato, porque es la que más se rompe.

```
- [ ] <acción> | <dueño> | <fecha> <hora>
```

Una línea por tarea, empezando con `- [ ]`. **Prohibida la tabla markdown** (`| Dueño | Tarea |`). Se ve ordenada y no sirve: el punto del bloque es que se pegue en cualquier app de tareas y quede marcable. Una tabla no se marca.

Si estás por escribir un `|---|` en el bloque 3, párate y usa casillas.

## Paso 4. Guardar

Escribe todo en `seguimientos/YYYY-MM-DD-<cliente>.md`.

- Crea la carpeta si no existe. La primera vez Claude Code va a pedir permiso para escribir. Es normal, es una sola vez.
- `<cliente>` en minúsculas, sin espacios ni tildes (`banco-del-norte`).
- Si el archivo ya existe, agrega al final bajo `## Segunda llamada` en vez de sobreescribir.
- Al terminar, di la ruta exacta del archivo.

Nombres de archivo que funcionan igual en Windows, Mac y Linux. Del nombre del cliente quita siempre: acentos, ñ, espacios, y los caracteres `\ / : * ? " < > |`. Reemplázalos por guión. Nunca uses rutas absolutas ni `~`: siempre `seguimientos/` relativo a la carpeta donde está trabajando el usuario.

`seguimientos/` está en `.gitignore`. Las conversaciones con tus clientes se quedan en tu máquina.

## Paso 4.5. Si el usuario tiene conector de correo, ofrécele dejar el borrador

Por defecto el bloque 4 se queda como texto en el archivo y el usuario lo copia. Eso funciona siempre y no depende de nada.

Pero si en esta sesión existe una herramienta de borrador de correo (`gmail_draft` de google-workspace-mcp, `outlook_draft` de microsoft-365-mcp, o equivalente), **ofrécela una vez**, así:

> Veo que tienes Gmail conectado. ¿Quiero dejarte el correo de seguimiento directo en tu carpeta de borradores, o prefieres copiarlo?

Reglas que no se rompen:

- **Borrador, nunca envío.** Ver Regla de oro 2. Aplica aquí sin excepción y no se desbloquea con permiso del usuario.
- **Pregunta antes.** Escribir en la cuenta de correo de alguien es un efecto externo. Se ofrece, se espera un sí, y recién ahí se hace.
- **Sin conector, ni lo menciones.** Si no hay herramienta de correo disponible, no digas nada de esto. No le pidas al usuario que instale nada en medio de su seguimiento.
- **Destinatario solo si está en la transcripción.** Sin correo del cliente en la llamada, el borrador va sin destinatario y se lo dices. No adivines una dirección.

Cualquier conector que no tenga paso propio abajo: ubícalo en la tabla de niveles y sigue esa fila.

## Paso 4.6. Si hay conector de calendario, ofrece agendar el recordatorio

El bloque 5 ya calculó el próximo toque. Si hay una herramienta de crear eventos (`create_event` de google-workspace-mcp, `mscal_create_event` de microsoft-365-mcp, o equivalente), ofrécelo:

> ¿Te agendo el seguimiento el viernes a las 10, con el contexto adentro?

**Nunca pongas invitados. Ni el cliente ni nadie.** Esta es la trampa concreta: estas APIs mandan `send_updates` en `all` por defecto, así que un solo invitado convierte un recordatorio privado en un correo que aterriza en la bandeja de tu cliente. El recordatorio es solo para el usuario.

El evento:

- **Título**: `Seguimiento: <cliente>`.
- **Hora**: exactamente la del bloque 5. 30 minutos si no se habló de duración.
- **Invitados**: ninguno. Siempre.
- **Descripción**: aquí está el valor. Mete lo que va a necesitar cuando suene y ya se le olvidó la llamada:
  - qué se acordó, en una línea
  - la objeción principal del cliente, citada
  - las tareas del bloque 3 que siguen siendo suyas
  - el correo de seguimiento del bloque 4, completo

Así el recordatorio no dice "llamar a Ana": trae todo para hacer la llamada, con el mensaje listo para enviar.

Pregunta antes. Sin conector de calendario, ni lo menciones.

## Paso 4.7. Si hay conector de CRM o notas, ofrece archivar el resumen

El bloque 1 está escrito para pegarse en un CRM. Si hay un conector que pueda escribir registros o páginas (Notion, Airtable, HubSpot, lo que tenga este usuario), ofrécelo en vez de hacerlo copiar:

> Te puedo dejar el resumen en la ficha del cliente. ¿Lo hago?

- **Nivel: solo lo ve el usuario.** Ofrece, espera el sí, escribe.
- **Agrega una nota, nunca edites el negocio.** Escribe el resumen como nota o página nueva. No toques etapa, monto, fecha de cierre, dueño ni probabilidad: son números que un gerente reporta, y uno equivocado es peor que uno faltante.
- **Sin ficha que coincida, no la crees.** Pregunta. Un cliente duplicado lo limpia alguien durante semanas.
- **Los `[FALTA]` viajan.** No los borres calladamente al pasar al CRM. Un campo vacío es honesto; uno inventado no.

## Paso 4.8. Si el líder comercial debe enterarse, redacta el aviso

El bloque 6 está escrito para un jefe. Si hay conector de mensajería (Slack, Teams, correo), ofrécelo:

> ¿Le mando el resumen a tu líder comercial por Slack? Te muestro el mensaje primero.

- **Nivel: lo ve un compañero.** Redacta, **muestra el texto completo**, espera un sí explícito, y manda por la compuerta de confirmación del conector. Nunca automático, y un "sí manda el correo al cliente" jamás cubre esto ni al revés.
- **El destinatario tiene que ser conocido.** Sin líder nombrado en la transcripción y sin uno configurado, pregunta. Nunca adivines un canal ni una persona.
- **Sus palabras, no una actuación.** El aviso cuenta lo que pasó, incluido lo que no funcionó. No suavices el bloque 7 camino al jefe: ese bloque existe justamente para que el equipo aprenda.

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
