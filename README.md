# Plan 5 Fases — App de seguimiento de entrenamiento

Panel de seguimiento para un plan de recomposición corporal, con soporte para
múltiples ciclos/programas, constructor visual de fases/días/ejercicios,
respaldo manual y funcionamiento 100% offline.

## Estructura del proyecto

```
index.html      → la app completa (HTML + CSS + JS en un solo archivo, sin build ni dependencias)
manifest.json   → metadata para instalarla como ícono de app en el celular (Android/Chrome)
icon192.png     → ícono 192x192 (requerido por el manifest)
icon512.png     → ícono 512x512 (requerido por el manifest)
```

No hay paso de build. `index.html` es autocontenido.

## Cómo correrla localmente

Abrir `index.html` directamente en cualquier navegador. No requiere servidor.

## Dónde viven los datos

Todo el progreso (ciclos creados, ejercicios editados, pesos, checks marcados)
se guarda en el `localStorage` del navegador de **cada dispositivo** — no se
sube a este repositorio ni a ningún servidor. Este repo versiona el **motor
de la app**, no tus datos de entrenamiento.

Para mover el progreso entre dispositivos o tener una copia de seguridad,
usar los botones **"Descargar respaldo"** / **"Restaurar respaldo"** dentro
de la app (genera/lee un `.json`).

## Deploy

Alojado en **GitHub Pages**, servido directo desde este repositorio
(rama `main`, carpeta raíz). Todas las rutas del proyecto (manifest, íconos)
son relativas, por lo que funcionan sin importar la subcarpeta en la que
GitHub Pages publique el sitio.

Para actualizar: cualquier cambio en `main` (push desde Git, o edición
directa de un archivo en la web de GitHub) dispara un redeploy automático
en 1-2 minutos. No hace falta ningún paso manual de subida.

## Historial

- v1 — Panel de seguimiento con gauge de cumplimiento, backup, modo edición rápida.
- v2 — Header fijo (sticky) al hacer scroll.
- v3 — Arquitectura multi-programa: constructor visual de ciclos completos
  (fases, semanas, deload, días, ejercicios), selector de programa activo,
  progreso independiente por ciclo.
- v4 — Corrección de geometría del gauge (se recortaba visualmente al
  acercarse al 100%), columna de Observaciones por ejercicio/semana,
  personalización de ejercicios por semana individual dentro de una fase
  (antes el mismo día se repetía igual en todas las semanas), y backup con
  estrategia de descarga en cascada + feedback visual (toast) para el caso
  de PWA instalada donde la descarga podía fallar en silencio.
