# NormativIA

Normativa aplicable a instalaciones eléctricas de baja tensión, con fuentes trazadas. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/normativia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23430567.svg)](https://doi.org/10.5281/zenodo.23430567)

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **Describe la instalación**: país, provincia, municipio, tipo (25 tipos, de vivienda a quirófanos, recarga de vehículo eléctrico o autoconsumo), potencia, periodo de búsqueda y características (nuevo suministro, generación, baterías, recarga, domótica, ascensor, calefacción, motores, alumbrado exterior).
- **Base de referencia sin IA**: el código calcula las ITC-BT aplicables (01 a 52) y las leyes y reales decretos estatales pertinentes, cada uno con su enlace al BOE y el motivo por el que aplica, más las guías técnicas del Ministerio.
- **Trámites del REBT**: memoria técnica de diseño o proyecto (umbrales de la ITC-BT-04) e inspección inicial y periódica por organismo de control (ITC-BT-05), con el grupo que lo motiva.
- **Distribuidora por el CUPS**: identifica la distribuidora por su prefijo y comprueba las letras de control (algoritmo contrastado con python-stdnum). El CUPS no sale nunca del navegador.
- **Búsqueda web con IA (opcional)**, una consulta por tabla: ITC-BT y guías, normas de la distribuidora, leyes, reales decretos, normativa autonómica y municipal. OpenAI (Responses API con `web_search`), Claude (`web_search`) o Gemini (`google_search`).
- **La IA propone, el código comprueba**: cada enlace se traza contra las fuentes que la herramienta de búsqueda consultó de verdad (URL, solo dominio o no trazado); se detectan ITC inexistentes, la ITC-BT-53 (proyecto no publicado), años imposibles o incoherentes con la referencia (y se corrigen), normas derogadas conocidas, páginas de búsqueda en lugar de documentos, fuentes secundarias y normas en la tabla equivocada (se reubican). Lo que repite la base se fusiona con ella.
- **Revisión**: filtros por resultado, decisión de incluir o descartar cada norma y alta manual de normas (que pasan las mismas comprobaciones).
- **Salidas**: Word horizontal con una tabla por tipo de norma, trámites, comprobaciones y enlaces; Excel con una hoja por tabla, URL clicables, fuentes consultadas, descartadas y avisos; ZIP con ambos; CSV; proyecto JSON que, al abrirse, repite todas las comprobaciones.
- Interfaz en español, inglés y portugués. Ejemplo sin clave (Elche, local de pública concurrencia de 15 kW) con errores sembrados a propósito para ver cómo los detecta el código.

## Cómo se usa la IA

Solo en la búsqueda web, con la propia clave de OpenAI, Google Gemini o Anthropic Claude y un modelo que admita búsqueda web. La clave se guarda solo en el navegador. La búsqueda web tiene coste por consulta en la cuenta de cada persona; se puede probar con una sola categoría.

## Privacidad

Todo se procesa y se guarda en el navegador (IndexedDB). Solo al pedir la búsqueda salen hacia el proveedor la ubicación, el tipo, la potencia, el periodo y el nombre de la distribuidora, tras un aviso previo con la muestra exacta. El CUPS y la clave no salen nunca ni se exportan.

## Límites

- Es un documento de ayuda para localizar normas: no sustituye la revisión de un técnico competente ni acredita que un inventario sea exhaustivo o que una norma esté vigente.
- La base de referencia (revisada en octubre de 2026) cubre el REBT y las principales disposiciones estatales; no incluye disposiciones autonómicas ni ordenanzas concretas: esas salen de la búsqueda y deben verificarse.
- Los trámites se calculan con la potencia total declarada y los umbrales estatales; las comunidades autónomas pueden exigir más.
- Con Gemini la traza solo puede hacerse por dominio (devuelve enlaces de redirección).
- Probado con IA simulada de los tres proveedores; no se ha probado con claves reales.

## Origen de la idea

Cuaderno de Colab de Sergio Valero Verdú: búsqueda web con la API de OpenAI por categorías (ITC-BT y guías, distribuidora, leyes, reales decretos, autonómica y municipal), con trazabilidad de los enlaces respecto de las fuentes devueltas por la búsqueda y salida en Word, Excel y ZIP. NormativIA conserva ese principio de trazabilidad y lo amplía con la base determinista, los trámites, el CUPS, las comprobaciones por código, la revisión y los tres proveedores.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Sergio Valero Verdú (Universidad Miguel Hernández de Elche).

A partir del cuaderno de Colab «Buscador de normativa eléctrica BT · Word + Excel» de Sergio Valero Verdú (búsqueda web con IA de ITC-BT, normas de distribuidora, leyes y reales decretos, con trazabilidad de enlaces).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Sergio Valero Verdú [0000-0002-9222-9173](https://orcid.org/0000-0002-9222-9173)

## Cómo citar

Borrás Rocher, F. y Valero Verdú, S. (2026). *NormativIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23430567](https://doi.org/10.5281/zenodo.23430567)

## Licencia

MIT. Véase [LICENSE](LICENSE).
