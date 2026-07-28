# Cierre de llamada

Pegas la transcripción de una llamada comercial. Sale el seguimiento completo.

- Resumen listo para pegar en el CRM
- Estado del negocio: cerró, no cerró, monto, quién decide, la objeción real
- Tareas con dueño, fecha y hora
- El correo de seguimiento ya redactado
- El recordatorio del próximo toque
- El aviso al líder comercial
- Qué funcionó y qué no en esa llamada

Lo que un buen vendedor hace en 30 minutos después de colgar. En segundos, igual, todas las veces.

**No se inventa nada.** Si un dato no está en la llamada, lo marca como `[FALTA]` en vez de rellenarlo. Un seguimiento con un monto inventado te cuesta el cliente.

---

## Empezar sin instalar nada

Si nunca has usado GitHub ni la terminal, esta es tu ruta. Toma un minuto.

Abre [EMPIEZA-AQUI.md](EMPIEZA-AQUI.md), copia el texto que está ahí, pégalo en Claude o en ChatGPT junto con la transcripción de tu última llamada.

Ya está. Ese es el resultado.

---

## Instalarlo de verdad (Claude Code)

La versión instalada guarda cada llamada en tu máquina, así que después puedes preguntar cosas entre llamadas: qué objeción se repite, qué dijiste en las que sí cerraron, cuántos seguimientos tienes vencidos.

Dentro de Claude Code, escribe estos dos comandos:

```
/plugin marketplace add mycelium-hq/cierre-de-llamada
```

```
/plugin install cierre-de-llamada@cierre-de-llamada
```

Listo. Ahora, después de cualquier llamada:

```
/cierre
```

Y pega la transcripción cuando te la pida.

**La primera vez te va a pedir permiso** para crear la carpeta donde guarda los seguimientos. Dale que sí. Es una sola vez, y es la señal de que está guardando en tu máquina y no en otro lado.

¿No tienes Claude Code? Se instala en [claude.com/code](https://claude.com/code). Si hoy no te alcanza, usa la ruta de arriba y vuelve a esta cuando quieras.

---

## Dónde queda tu información

Cada llamada procesada se guarda en `seguimientos/` dentro de tu carpeta, en tu computador.

Esa carpeta está en `.gitignore`. No se sube a git, nosotros no la vemos, y este repo no tiene telemetría de ningún tipo: no hay código que pueda reportar nada a Mycelium.

Con una precisión que importa: **Claude Code sí manda tu transcripción a los modelos de Anthropic para procesarla.** Así funciona cualquier herramienta con Claude, con este repo o sin él. Lo que no pasa es que tus llamadas lleguen a nosotros.

El detalle completo está en [SECURITY.md](SECURITY.md). Vale la pena leerlo antes de meter llamadas de clientes.

---

## Si ya tienes el correo conectado

Por defecto el correo de seguimiento sale como texto y tú lo copias. Funciona siempre y no depende de nada.

Si además tienes un conector de correo en Claude Code, la skill lo detecta y te ofrece **dejar el borrador directo en tu carpeta de borradores**. Dos que puedes instalar, gratis y abiertos:

- Gmail: [google-workspace-mcp](https://github.com/adelaidasofia/google-workspace-mcp)
- Outlook: [microsoft-365-mcp](https://github.com/adelaidasofia/microsoft-365-mcp)

**Borrador, nunca envío.** La skill no manda correos aunque se lo pidas. Abrir y enviar es tuyo, siempre.

## Qué NO hace esto

Vale la pena decirlo claro, porque es la mitad del valor.

Esto lee **una llamada a la vez**, y después solo recuerda las llamadas que tú mismo procesaste en esta carpeta.

No sabe qué le prometiste a ese cliente por correo hace tres meses. No ve tu CRM. No ve las propuestas que mandaste. No ve las llamadas de los otros vendedores de tu equipo. No conecta un cliente de hoy con la conversación que tuvieron en marzo.

Cuando lo uses varias veces vas a sentir exactamente dónde está ese techo. Ahí empieza otra conversación, que es la del segundo cerebro: el mismo principio, pero sobre todo lo que tu empresa ya sabe, y compartido por todo el equipo.

Esto es la puerta. Úsala primero.

---

## Requisitos

**Windows, Mac y Linux.** Funciona igual en los tres.

Aquí no hay scripts que instalar ni terminal que abrir. Los dos comandos de arriba se escriben dentro de Claude Code, que es la misma ventana en cualquier sistema. En Windows no necesitas WSL, ni Git Bash, ni PowerShell como administrador.

Para la ruta sin instalar (la de [EMPIEZA-AQUI.md](EMPIEZA-AQUI.md)) solo necesitas un navegador, así que también sirve desde el celular.

No necesitas saber programar. No necesitas saber qué es un repositorio. No hay que configurar nada.

---

## Licencia

MIT. Úsalo, cámbialo, compártelo con tu equipo.

Hecho por [Mycelium AI](https://github.com/mycelium-hq).
