# Catálogo Semántico - Muebles Júpiter

Proyecto web desarrollado para el programa **Análisis y Desarrollo de Software (ADSO)** del SENA (Ficha: 3234206). Consiste en un prototipo de catálogo comercial estructurado bajo normas semánticas de HTML5 y un diseño modular en CSS enfocado en la mantenibilidad y la jerarquía de especificidad.

---

## 📂 Estructura de Archivos
* **`index.html`**: Contiene la arquitectura semántica del sitio (`header`, `nav`, `main`, `aside`, `section`, `article`, `footer`).
* **`estilos.css`**: Hoja de estilos encargada de la herencia global, el aislamiento de zonas mediante selectores combinados y la estandarización de un sistema plano de clases.
* **`README.md`**: Documentación técnica del proyecto y cálculo de pesos de especificidad.

---

## 📐 Cálculo y Gestión de Especificidad en CSS
Para mantener un código limpio, predecible y evitar colisiones visuales sin recurrir a la mala práctica de `!important` o selectores rígidos de ID, la hoja de estilos se rige bajo la siguiente jerarquía de puntos:

| Tipo de Selector | Puntuación | Ejemplo | Criterio de Uso en el Proyecto |
| :--- | :---: | :--- | :--- |
| **Etiquetas (Tags)** | **1 pt** | `body`, `header`, `p` | Usado para herencia global y tipografía base. |
| **Clases (Classes)** | **10 pts** | `.btn-comprar`, `.destacado` | **Sistema principal:** Usado para componentes reutilizables y variantes visuales de forma plana. |
| **Identificadores (IDs)** | **100 pts** | `#btn-destacado` | *Evaluado en fase de conflicto y descartado en la refactorización final* por generar excesiva rigidez y romper la cascada natural. |

---

## 🛠️ Flujo de Trabajo y Control de Versiones (Git)
El proyecto se estructuró y respaldó local y remotamente siguiendo buenas prácticas de desarrollo:
1. Inicialización de repositorio local (`git init`) y conexión con GitHub (`git remote add origin`).
2. Creación y gestión de la rama de trabajo (`develop`).
3. Registro de avances mediante commits atómicos y estructurados (**Conventional Commits**):
   * `chore(base): inicializar estructura html y conectar hoja de estilos`
   * `feat(html): maquetar catalogo semantico con header, main, aside y footer`
   * `feat(styles): aplicar herencia global en body y selectores combinados por zonas`
   * `feat(styles): maquetar catalogo semantico y aplicar jerarquia CSS`

## Hallazgos: El Modelo de Caja (Box Model)

1. **Diferencia práctica entre Margin y Padding:**
   - **Padding (Relleno interno):** Es el espacio que existe entre el contenido de la caja (texto, imágenes) y su borde. El color o fondo de la caja se extiende abarcando esta zona.
   - **Margin (Margen externo):** Es el espacio invisible que separa una caja de los demás elementos vecinos (elementos hermanos), funcionando como un "campo de fuerza" para evitar choques visuales.

2. **¿Por qué es obligatorio usar `box-sizing: border-box`?:**
   - Por defecto, los navegadores calculan el tamaño sumando el contenido más el padding y los bordes, lo que desborda las medidas previstas. Al implementar `box-sizing: border-box`, logramos que cualquier relleno o borde crezca *hacia adentro*, garantizando que la caja mantenga exactamente el ancho y alto programados sin romper la estructura.

3. **Efecto en los elementos hermanos al aplicar un margen grande:**
   - Cuando se incrementa considerablemente el `margin` de un elemento, este ejerce mayor presión o separación sobre sus elementos contiguos, obligándolos a alejarse o, si el espacio horizontal del contenedor padre se agota, provocando que bajen de línea automáticamente.

   ## Hallazgos: Centralización de Identidad Visual y Espaciado

1. **Lista completa de variables declaradas:**
   - **Colores:** `--color-primario` (#1d4ed8), `--color-secundario` (#047857), `--color-terciario` (#b91c1c), `--color-fondo` (#faf8f5), `--color-texto` (#333333), `--color-filtrar-categoria` (#fef3c7), `--color-footer` (#fee2e2), `--color-blanco` (#ffffff), y `--color-borde` (#e2e8f0).
   - **Tipografía:** `--fuente-principal` ('Inter', sans-serif).
   - **Espaciados:** `--espaciado-pequeno` (10px), `--espaciado-medio` (20px), y `--espaciado-grande` (25px).

2. **Ventaja de reutilizar medidas de margen y relleno:**
   Permite mantener una proporción visual estricta y armónica ("consistencia de aire") en todos los componentes. Si se requiere ajustar el espaciado general de las tarjetas o secciones, basta con modificar un único valor en la central de mando `:root` en lugar de buscar y cambiar múltiples selectores manualmente.

3. **Prevención de colisiones visuales:**
   La centralización en `:root` evita la duplicación de código (deuda técnica) y asegura que, a medida que la hoja de estilos crezca con nuevos elementos, todos hereden las mismas reglas de diseño base. Esto elimina el riesgo de desajustes visuales o valores arbitrarios dispersos por todo el código CSS.

## Hallazgos: Pseudoclases y Pseudoelementos

1. **Diferencia funcional entre Pseudoclase y Pseudoelemento:**
   - **Pseudoclases (`:hover`, `:active`, `:focus`):** Se encargan de reaccionar a estados dinámicos o eventos de interacción desencadenados por el usuario sobre la interfaz (como pasar el cursor, hacer clic o navegar con el teclado).
   - **Pseudoelementos (`::before`, `::after`):** Permiten la inyección de contenido virtual o decorativo dentro del DOM (por ejemplo, indicadores visuales o insignias) sin modificar la estructura del archivo HTML.

2. **Importancia técnica de `:focus` para la Accesibilidad Web (UX/UI):**
   - La pseudoclase `:focus` garantiza una navegación clara y accesible para usuarios que interactúan mediante la tecla `Tab` o tecnologías de asistencia. Al aplicar un contorno visible (`outline`), el navegador proporciona una pista visual inconfundible sobre el elemento activo en pantalla.

3. **Inyección decorativa desde CSS vs. HTML:**
   - Inyectar detalles visuales con `::before` o `::after` desde la hoja de estilos evita la acumulación de etiquetas HTML vacías o innecesarias. Esto mantiene el código semántico, limpio, mantenible y enfocado únicamente en la estructura del contenido.