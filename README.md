# Conector MCP — Documentos del Coordinador (multi-área)

Segundo conector, más amplio que `coordinador-mcp`. Cubre **todas las áreas de
Informes y Estudios** del Coordinador Eléctrico Nacional y lee múltiples
formatos, no solo PDF.

El primer conector sigue funcionando aparte; este es independiente para poder
compararlos y elegir.

## Áreas cubiertas

Planificación y Desarrollo · Operación · Mercados · Reportes del Coordinador ·
Parámetros Operacionales · Auditorías Técnicas · Normativa Sectorial.

## Herramientas

| Herramienta | Qué hace |
|---|---|
| `listar_areas()` | Las grandes áreas de documentos, con su URL. |
| `listar_secciones(area)` | Categorías dentro de un área. |
| `explorar(url)` | Subcarpetas y documentos de una página (título, fecha, **formato**, enlace). |
| `arbol(url, profundidad)` | Árbol anidado de una sección. |
| `buscar_documentos(consulta, seccion, anio, formato, limite)` | Busca por título; filtra por año (de la fecha o del título/URL) y formato. Avisa con `indice_parcial` si el área es grande. |
| `leer_documento(url, paginas, archivo_zip)` | Lee **PDF, XLSX/XLSM, CSV, TXT**. Para un **ZIP** lista sus archivos; con `archivo_zip` lee uno específico. |

## Despliegue (igual que el primero)

1. **GitHub:** sube estos archivos a un repo (p. ej. `coordinador-docs-mcp`).
2. **Railway:** New Project → Deploy from GitHub repo → detecta el Dockerfile →
   Settings → Networking → Generate Domain.
3. **Claude:** Configuración → Conectores → Agregar conector personalizado →
   pega `https://TU-DOMINIO.up.railway.app/mcp`.

## Notas

- Solo lectura de información pública. Sin autenticación.
- La búsqueda indexa dentro de un **presupuesto de tiempo** (~20 s) para no
  colgarse en áreas grandes; si devuelve `indice_parcial: true`, acota con
  `listar_secciones` o usa `refrescar_indice`. El índice cachea ~24 h.
- No cubre: portales con login, el Portal API (datos estructurados) ni OCR de
  PDFs escaneados. Eso sería un conector aparte.
