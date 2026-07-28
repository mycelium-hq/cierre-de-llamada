# Seguridad y datos

Este repositorio maneja conversaciones con tus clientes. Aquí está exactamente qué pasa con ellas, sin letra chica.

## Qué es este repo

Markdown y dos archivos JSON. **No hay código ejecutable**: ni scripts, ni dependencias, ni llamadas de red. Lo que instalas son instrucciones que lee Claude Code, no un programa que corre en tu máquina.

Puedes leer los 9 archivos completos en menos de diez minutos. Esa es la idea.

## A dónde va tu transcripción

Tres destinos, y conviene tenerlos separados en la cabeza.

**1. A tu disco.** El seguimiento se guarda en `seguimientos/`, dentro de la carpeta donde estés trabajando. Esa carpeta está en `.gitignore`, así que no se sube a git aunque el directorio sea un repositorio.

**2. A Anthropic.** Claude Code manda tu transcripción a los modelos de Anthropic para procesarla. Así funciona cualquier herramienta con Claude, con este repo instalado o sin él. Si tu política interna no permite que las llamadas de clientes pasen por un proveedor de modelos, esa decisión es anterior a este repo y no la cambia tener o no tener la skill. Las condiciones de manejo de datos son las de tu plan de Anthropic.

**3. A Mycelium AI: nada.** Este repo no tiene telemetría, ni analítica, ni una URL a la que reportar. No sabemos si lo instalaste, ni cuándo lo usaste, ni con qué cliente. No podemos saberlo: no hay código que lo haga.

## Qué NO hace

- No manda correos. El bloque 4 escribe un borrador y lo deja ahí; enviarlo es tuyo.
- No escribe en tu CRM. Genera texto para que lo pegues.
- No agenda nada en tu calendario. Te dice la fecha y la hora.
- No lee tu correo, ni tu CRM, ni tus archivos fuera de la carpeta donde lo corras.

Cada acción que toca el mundo real la haces tú. Es deliberado.

## Permisos

La primera vez que guarde un seguimiento, Claude Code te va a pedir permiso para escribir. Ese prompt es la línea de control: si algún día te pide permiso para algo que no esperas, dile que no y avísanos.

## Borrar todo

```
/plugin uninstall cierre-de-llamada@cierre-de-llamada
```

Y borra la carpeta `seguimientos/`. No queda nada más.

## Reportar un problema

Abre un issue en https://github.com/mycelium-hq/cierre-de-llamada/issues.

Si crees que encontraste algo con implicaciones de seguridad y prefieres no publicarlo, usa el reporte privado de vulnerabilidades de GitHub en la pestaña Security de este repositorio.
