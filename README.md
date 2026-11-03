# CSS
# Catálogo Semántico - Muebles Júpiter

Proyecto desarrollado para el programa **Análisis y Desarrollo de Software (ADSO) - SENA** (Ficha 3234206).

## Cálculo de Puntos de Especificidad en CSS
Para mantener un código limpio y evitar colisiones visuales sin recurrir a la mala práctica de `!important`, se rige bajo la siguiente jerarquía:

* **Etiquetas (Tags):** 1 punto (Ej: `header`, `p`, `a`)
* **Clases (Classes):** 10 puntos (Ej: `.btn-comprar`, `.destacado`)
* **Identificadores (IDs):** 100 puntos (Ej: `#btn-destacado` — *Descartado en la refactorización final por generar rigidez*).