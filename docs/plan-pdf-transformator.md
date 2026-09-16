# plan.md — pdf-transformator

## Qué hay que construir
Recibe el JSON estructurado que produce `pdf-extractor` (bloques de texto con tamaño de fuente y posición/tabla) y lo convierte a HTML — el formato canónico que se persiste.

## Cómo construirlo, en orden
1. Definir umbrales simples: bloques con tamaño de fuente por encima de cierto valor → `<h1>`/`<h2>`; bloques marcados como parte de una tabla → `<table>`/`<tr>`/`<td>` según su posición de celda; el resto → `<p>`.
2. Implementar el mapeo bloque a bloque siguiendo esas reglas.
3. Probar contra la salida real de `pdf-extractor` con los mismos PDFs de prueba (simple + con tabla), no con JSON inventado a mano.
4. Ajustar los umbrales según lo que salga mal en la prueba — es la parte que más iteración va a necesitar, porque los umbrales "correctos" dependen de PDFs reales, no se pueden adivinar de antemano.

## Depende de
El shape del JSON de `pdf-extractor` — no puede arrancar en serio hasta que ese contrato esté definido.
