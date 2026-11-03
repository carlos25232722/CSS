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