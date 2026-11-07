# Word-D Phrase Dataset (Catálogo Abierto de Frases)

[![Phrases Count](https://img.shields.io/badge/Total%20Phrases-1200-blue)](catalogue/phrases.json)
[![Categories Count](https://img.shields.io/badge/Categories-12-indigo)](catalogue/catalogue_manifest.json)
[![Content Rating](https://img.shields.io/badge/Rating-PEGI%203%20%2F%20Family%20Safe-success)](schema/phrase_schema.json)
[![Schema Version](https://img.shields.io/badge/Schema%20Version-v2-blueviolet)](schema/phrase_schema.json)
[![Integrity](https://img.shields.io/badge/Integrity-SHA--256%20Verified-emerald)](catalogue/catalogue_manifest.json)
[![License](https://img.shields.io/badge/License-CC--BY--4.0-lightgrey)](LICENSE)

Dataset abierto, verificado y clasificado de frases en español orientado a videojuegos de palabras, agilidad mental, aplicaciones educativas y procesamiento de lenguaje natural (NLP).

Todas las frases han sido normalizadas, clasificadas por dificultad (1 a 3), acompañadas de una pista pedagógica y filtradas bajo estándares estrictos de aptitud familiar (**PEGI 3 / Todo Público**).

---

## 📊 Estructura del Catálogo

El dataset contiene **1,200 frases únicas**, distribuidas equitativamente en **12 categorías temáticas** (100 frases por categoría):

| Categoría | Identificador | Temática Principal | Frases |
| :--- | :--- | :--- | :---: |
| **Países y Capitales** | `paises` | Geografía, capitales del mundo y gentilicios | 100 |
| **Refranes y Dichos** | `refranes` | Proverbios, refranes populares y sabiduría tradicional | 100 |
| **Cine y Películas** | `peliculas` | Títulos cinematográficos clásicos y contemporáneos | 100 |
| **Ciencia y Naturaleza** | `ciencia` | Astronomía, física, biología y conceptos científicos | 100 |
| **Literatura Universal** | `literatura` | Obras clásicas, autores y personajes literarios | 100 |
| **Series y Televisión** | `television` | Series icónicas y cultura televisiva | 100 |
| **Fauna y Animales** | `animales` | Especies del reino animal, hábitats y biología | 100 |
| **Gastronomía y Comidas** | `comidas` | Platos tradicionales, ingredientes y arte culinario | 100 |
| **Oficios y Profesiones** | `profesiones` | Profesiones, oficios tradicionales y disciplinas | 100 |
| **Marcas Emblemáticas** | `marcas` | Empresas históricas, invenciones y tecnología | 100 |
| **Objetos Cotidianos** | `objetos` | Herramientas, utensilios e instrumentos de uso diario | 100 |
| **Colores y Tonalidades** | `colores` | Colores, matices cromáticos y teoría del color | 100 |

---

## 📁 Archivos del Repositorio

- [`catalogue/phrases.json`](catalogue/phrases.json): Dataset principal con las 1,200 frases y la metadata de categorías.
- [`catalogue/catalogue_manifest.json`](catalogue/catalogue_manifest.json): Manifiesto de metadatos, conteos oficiales, versión del catálogo y hash SHA-256.
- [`catalogue/phrases.json.sig`](catalogue/phrases.json.sig): Manifiesto criptográfico con firma digital ECDSA (secp256r1) para verificación de autenticidad en clientes móviles.
- [`schema/phrase_schema.json`](schema/phrase_schema.json): Esquema formal JSON Schema v2 que define las reglas sintácticas y restricciones de los datos.
- [`LICENSE`](LICENSE): Términos de uso de la licencia Creative Commons Attribution 4.0 International (CC BY 4.0).

---

## 📐 Esquema de Datos

Cada entrada del archivo `catalogue/phrases.json` cumple la siguiente estructura:

```json
{
  "id": "com_001",
  "category": "comidas",
  "text": "PAELLA VALENCIANA CON ARROZ Y MARISCOS",
  "hint": "Plato tradicional español preparado en sartén ancha",
  "difficulty": 2,
  "language": "es"
}
```

### Reglas de Normalización y Validación

1. **Texto (`text`):**
   - Letras mayúsculas del alfabeto español (`A-Z` y `Ñ`).
   - Sin tildes ortográficas (`Á`, `É`, `Í`, `Ó`, `Ú` se normalizan a `A`, `E`, `I`, `O`, `U` para compatibilidad con tableros de letras).
   - Longitud total entre 10 y 60 caracteres.
   - Longitud de cada palabra entre 3 y 12 caracteres.
2. **Pista (`hint`):**
   - Texto descriptivo en español neutro de hasta 140 caracteres que orienta al jugador sin revelar directamente la respuesta.
3. **Dificultad (`difficulty`):**
   - `1`: Fácil (frases cortas de uso cotidiano).
   - `2`: Media (longitud moderada con vocabulario específico).
   - `3`: Difícil (mayor longitud o conceptos más especializados).
4. **Filtro de Seguridad Familiar (PEGI 3):**
   - Todo el contenido debe ser apto para todas las edades. No se admiten palabras ofensivas, violencia explícita ni contenido para adultos.

---

## 🔒 Verificación de Integridad

Puedes verificar de forma autónoma la integridad del archivo `catalogue/phrases.json` calculando su hash criptográfico SHA-256:

### En Linux / macOS
```bash
sha256sum catalogue/phrases.json
```

### En Windows (PowerShell)
```powershell
Get-FileHash -Algorithm SHA256 catalogue/phrases.json
```

El valor resultante debe coincidir con el campo `sha256` registrado en [`catalogue/catalogue_manifest.json`](catalogue/catalogue_manifest.json).

---

## 🤝 Cómo Contribuir

Las contribuciones de nuevas frases, correcciones de pistas o sugerencias de categorías son bienvenidas mediante **Pull Requests**:

1. Realiza un **Fork** de este repositorio.
2. Añade o edita entradas en `catalogue/phrases.json` respetando las reglas de formato y el esquema [`schema/phrase_schema.json`](schema/phrase_schema.json).
3. Asegúrate de que el contenido sea apto para todo público (PEGI 3).
4. Envía un **Pull Request** explicando el cambio propuesto.

El pipeline de integración continua (CI) en GitHub Actions validará automáticamente la sintaxis JSON y el cumplimiento del esquema en cada Pull Request.

---

## 📄 Licencia

Este dataset y su documentación se distribuyen bajo la licencia [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). Eres libre de compartir, copiar, distribuir y adaptar el material para cualquier propósito, incluso comercial, siempre que otorgues el crédito correspondiente.
