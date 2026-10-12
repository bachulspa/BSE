# Cómo se creó la landing page de Bachúl Spa y Estética

Documento de proceso: del encargo inicial al sitio publicado, con las imágenes usadas y la forma de citar la página en formato APA (7.ª edición).

- **Repositorio:** https://github.com/bachulspa/BSE
- **Sitio publicado:** https://bachulspa.github.io/BSE/ (una vez activado Pages)
- **Fecha de elaboración:** 11 de octubre de 2026
- **Construida con:** Claude (Anthropic), modelo Claude Sonnet 5.5, mediante Claude Code

---

## 1. El encargo (prompt)

### 1.1 Material entregado

| Material | Contenido |
|---|---|
| `Prompt_Landing_Page_Bachul_Spa.docx` | Documento Word con las instrucciones de la página (negocio, sedes, servicios, tono y requisitos). |
| 16 imágenes | Afiches y fotografías promocionales del negocio, con servicios, promociones, teléfonos y logotipo. |

> **Nota:** el texto íntegro del Word no se reproduce aquí porque no quedó almacenado en el repositorio. Para dejarlo documentado, pegue su contenido en esta sección (ver 1.3).

### 1.2 Instrucción dada en el chat

Texto literal del mensaje que inició el trabajo:

> Lea el Word y realicé una página que se pueda ver desde github como es un repo público use impecable para trabajar y agentes de UI Que sea muy buena y bonita la página tipo apple

Requisitos que se desprenden de ella y del Word:

1. Una sola página (landing) para **Bachúl Spa y Estética**, con sedes en **Cartago** y **Paseo Colón** (Costa Rica).
2. Visible desde GitHub: sitio estático publicable con **GitHub Pages**, sin proceso de compilación.
3. Diseño cuidado, de estilo Apple: mucho espacio en blanco, tipografía grande, imágenes protagonistas, animaciones sutiles.
4. Uso de habilidades de diseño y agentes de interfaz.

### 1.3 Espacio para el prompt completo del Word

```text
(Pegue aquí el contenido de Prompt_Landing_Page_Bachul_Spa.docx)
```

### 1.4 Peticiones posteriores (en orden)

| # | Petición | Resultado |
|---|---|---|
| 1 | Conectar el chat a un repositorio de GitHub y publicarlo con Pages | Sitio estático desde `main` / raíz. |
| 2 | «Solicitar cita» debe abrir WhatsApp (8318 0003) | Tres botones con `https://wa.me/50683180003?text=…` y mensaje predefinido. |
| 3 | En el formulario, botón de WhatsApp según la sede, con el texto autogenerado como mensaje | Cada sede usa su número; el enlace se actualiza en cada tecla. |
| 4 | Usar el repositorio `bachulspa/BSE` | Remoto `origin` apuntando a `https://github.com/bachulspa/BSE.git`, rama `main`. |

---

## 2. Proceso de construcción

### 2.1 Fases

1. **Lectura del Word y de los afiches.** Se catalogaron servicios, sedes, teléfonos, redes sociales y promociones.
2. **Decisiones de contenido.** Se publicaron solo datos confirmados; los precios y promociones con vigencia se dejaron fuera (ver sección 6).
3. **Dirección de diseño.** Estilo editorial sobrio inspirado en Apple.
4. **Construcción** de `index.html`, `styles.css`, `config.js` y `main.js`.
5. **Pruebas en navegador real** (Chromium con Playwright, escritorio 1440 px y móvil 390 px): 46 comprobaciones automáticas, todas aprobadas en la última ejecución.
6. **Auditoría** de accesibilidad y rendimiento; se corrigieron 8 hallazgos.
7. **Publicación** en GitHub Pages y ajustes posteriores a petición.

### 2.2 Decisiones de diseño

| Elemento | Decisión |
|---|---|
| Paleta (tomada del logotipo) | Marfil `#fcfaf8`, porcelana `#f4efea`, carmesí `#a3162a`, vino `#2e0f17`, dorado `#b08a52` |
| Tipografía | **Instrument Serif** para títulos e **Inter** (variable) para texto; alojadas en el propio repositorio |
| Imágenes | WebP optimizado; carga diferida salvo la portada |
| Movimiento | Aparición al desplazarse con `IntersectionObserver`; se desactiva con `prefers-reduced-motion` |
| Accesibilidad | Pestañas ARIA con teclado, foco visible, contraste revisado, texto alternativo en imágenes, objetivos táctiles ≥ 40 px |

### 2.3 Estructura del sitio

```
index.html              Contenido y estructura
assets/css/styles.css   Estilos y variables de diseño
assets/js/config.js     Teléfonos, Instagram y WhatsApp de cada sede
assets/js/main.js       Menú, pestañas, visor de imágenes, contacto y botón flotante
assets/img/             Logotipo, fotografías e íconos
assets/fonts/           Instrument Serif e Inter
.nojekyll               Evita el procesamiento Jekyll de GitHub Pages
README.md               Guía de uso y pendientes
```

### 2.4 Secciones de la página

Encabezado con menú · Portada (hero) · Presentación · Servicios en cuatro pestañas (18 servicios con «Consultar este servicio») · Galería con visor ampliable · Sedes · Contacto con formulario que genera el mensaje · Pie de página · Botón flotante de cita.

### 2.5 Botones de WhatsApp

- Los botones «Solicitar cita» abren `https://wa.me/50683180003?text=` seguido del mensaje codificado con `encodeURIComponent`.
- El formulario de contacto arma un mensaje con servicio, sede, nombre y fecha. El botón principal de WhatsApp usa el número de la sede elegida y ese mismo texto.
- Los números se configuran en `assets/js/config.js`.

### 2.6 Historial de cambios (Git)

| Commit | Descripción |
|---|---|
| `0ddbc8a` | Landing page de Bachúl Spa y Estética |
| `e45160a` | Botones «Solicitar cita» abren WhatsApp (8318 0003) |
| `83deb9b` | Botón de WhatsApp desde el inicio en el bloque de contacto |
| `9a5179a` | Formulario: botón de WhatsApp según la sede elegida |

---

## 3. Imágenes utilizadas

**Origen:** las 16 imágenes entregadas por el negocio (afiches y fotografías promocionales). Las de la página son **recortes sin texto** de esos materiales, convertidos a WebP. No se usaron imágenes de bancos externos.

| Archivo en `assets/img/` | Uso en la página | Descripción (texto alternativo) |
|---|---|---|
| `logo-wordmark.webp` | Encabezado | Logotipo horizontal «Bachúl Spa y Estética» |
| `logo.webp` | Sección de presentación | Logotipo con lema «Belleza natural» |
| `mark.png` | Detalle decorativo | Marca del logotipo (decorativa, sin texto alternativo) |
| `hero.webp` | Portada | Mujer relajada con los ojos cerrados recibiendo un tratamiento facial |
| `depilacion.webp` | Galería | Persona aplicando cera tibia sobre una pierna con una espátula de madera |
| `facial.webp` | Galería | Mujer con diadema blanca y ojos cerrados, con manos enguantadas sobre su rostro |
| `cabello.webp` | Galería | Mujer de perfil con cabello largo, ondulado y brillante |
| `laser.webp` | Galería | Dispositivo de mano aplicado sobre una pierna, con una mano enguantada |
| `velas.webp` | Galería | Velas encendidas, toallas blancas y una flor de plumeria en un ambiente de spa |
| `manicure.webp` | Galería | Manos con uñas rosadas sobre una toalla blanca, junto a flores |
| `favicon.png` | Ícono de pestaña | Derivado del logotipo |
| `apple-touch-icon.png` | Ícono en iOS | Derivado del logotipo |

**Limitaciones conocidas:** al ser recortes de afiches, la resolución es limitada. Lo recomendable es reemplazarlas por fotografías propias de las instalaciones y el equipo, conservando los mismos nombres de archivo. También conviene sustituir el logotipo por el original en vector o PNG con fondo transparente.

**Derechos:** el negocio debe confirmar que tiene los derechos de uso de las fotografías incluidas en sus afiches (por ejemplo, si provienen de un banco de imágenes o de un proveedor).

---

## 4. Software, herramientas y fuentes

| Componente | Función |
|---|---|
| HTML, CSS y JavaScript sin dependencias | Sitio estático |
| GitHub y GitHub Pages | Alojamiento y publicación |
| Instrument Serif | Tipografía de títulos |
| Inter | Tipografía de texto |
| Playwright y Chromium | Pruebas automáticas en navegador |
| Claude Code (Claude Sonnet 5.5) | Desarrollo asistido |

---

## 5. Cómo citar en APA (7.ª edición)

Convenciones que se aplican en todas las referencias:

- Sangría francesa en la lista de referencias (en Word: Párrafo → Sangría especial → Francesa).
- Las referencias van en orden alfabético por el autor.
- Los títulos de páginas web y software van en cursiva.
- Las URL se escriben completas, sin punto final y sin la etiqueta «Recuperado de» (salvo contenido que cambia con el tiempo).

### 5.1 La página web (referencia principal)

**Plantilla:**
Organización o autor. (Año, día mes). *Título de la página* [Descripción]. Sitio. URL

**Referencia:**

> Bachúl Spa y Estética. (2026, 11 de octubre). *Bachúl Spa y Estética: Belleza natural* [Página web]. GitHub Pages. https://bachulspa.github.io/BSE/

**Cita en el texto:**
- Entre paréntesis: (Bachúl Spa y Estética, 2026)
- Narrativa: Bachúl Spa y Estética (2026) presenta…

> Verifique el título exacto que muestra la pestaña del navegador y use la URL con la que finalmente se publique.

### 5.2 El código fuente (repositorio)

**Plantilla:**
Autor. (Año). *Título* [Software]. Plataforma. URL

**Referencia:**

> Bachúl Spa y Estética. (2026). *BSE* [Código fuente]. GitHub. https://github.com/bachulspa/BSE

**Cita en el texto:** (Bachúl Spa y Estética, 2026)

### 5.3 Contenido generado con inteligencia artificial

APA recomienda citar la herramienta como software y describir en el texto cómo se usó. El autor del software es la empresa que la desarrolla. Si el contenido no puede recuperarse por un enlace, se describe en el cuerpo del trabajo.

**Plantilla:**
Empresa. (Año). *Nombre del modelo* (versión) [Modelo de lenguaje]. URL

**Referencia:**

> Anthropic. (2026). *Claude* (Claude Sonnet 5.5) [Modelo de lenguaje de gran tamaño]. https://claude.ai

**Cita en el texto:** (Anthropic, 2026)

**Sugerencia de redacción para el apartado de metodología:**

> El sitio fue desarrollado con la asistencia de Claude (Anthropic, 2026), a partir de un documento de requisitos y de material gráfico entregado por el negocio. El código fue revisado y probado en navegador antes de su publicación.

### 5.4 Las tipografías

> Andersson, R. (2020). *Inter* [Fuente tipográfica]. https://rsms.me/inter/

> Instrument. (2022). *Instrument Serif* [Fuente tipográfica]. Google Fonts. https://fonts.google.com/specimen/Instrument+Serif

**Citas en el texto:** (Andersson, 2020); (Instrument, 2022)

> Antes de entregar el trabajo, confirme los años y autores en la ficha oficial de cada fuente; los datos de las tipografías aquí son los de su catálogo público, no se verificaron para este documento.

### 5.5 Las imágenes

Las imágenes son material del propio negocio, así que se cita al autor del material o al negocio.

**Plantilla:**
Autor o empresa. (Año). *Título o descripción* [Fotografía]. Fuente.

**Referencia (ejemplo con la portada):**

> Bachúl Spa y Estética. (s. f.). *Mujer relajada recibiendo un tratamiento facial* [Fotografía]. Material promocional del negocio.

**Pie de figura en el trabajo:**

> *Figura 1.* Imagen de portada de la landing page. Fuente: Bachúl Spa y Estética (s. f.).

Si el fotógrafo o el banco de imágenes de origen es otro, cítelos como autor en su lugar.

### 5.6 Ejemplo de lista de referencias completa

> Andersson, R. (2020). *Inter* [Fuente tipográfica]. https://rsms.me/inter/
>
> Anthropic. (2026). *Claude* (Claude Sonnet 5.5) [Modelo de lenguaje de gran tamaño]. https://claude.ai
>
> Bachúl Spa y Estética. (2026). *BSE* [Código fuente]. GitHub. https://github.com/bachulspa/BSE
>
> Bachúl Spa y Estética. (2026, 11 de octubre). *Bachúl Spa y Estética: Belleza natural* [Página web]. GitHub Pages. https://bachulspa.github.io/BSE/
>
> Instrument. (2022). *Instrument Serif* [Fuente tipográfica]. Google Fonts. https://fonts.google.com/specimen/Instrument+Serif

---

## 6. Pendientes de confirmar con el negocio

- **Teléfono de Cartago:** la solicitud indica +506 2552 1010 y los afiches muestran 8318 0003. La página usa el primero para llamadas y el segundo para WhatsApp.
- **WhatsApp de Paseo Colón (7252 8996):** tomado de los afiches, sin confirmar.
- **Sede de Pérez Zeledón** (7123 9639): aparece en los afiches, pero no en el Word; no se publicó.
- **Precios y promociones:** omitidos por tener vigencia limitada.
- **Direcciones exactas, horarios y mapas** de cada sede.
- **Fotografías propias y logotipo original** en alta resolución.
- **Reels de Facebook:** se enlazan, no se incrustan.
- **Derechos de las imágenes** de los afiches.

## 7. Cómo editar la página

- **Teléfonos y redes:** `assets/js/config.js` y las tarjetas de sedes, el pie y los datos estructurados de `index.html` (tres lugares).
- **WhatsApp de «Solicitar cita»:** `citaWhatsapp` en `config.js` y el enlace de los tres botones en `index.html`.
- **Fotografías:** reemplazar los archivos de `assets/img/` conservando el nombre.
- **Servicios:** cada tarjeta con `data-service` en `index.html` alimenta también el selector del formulario.

## 8. Cómo publicar

1. En el repositorio: **Settings → Pages**.
2. *Build and deployment*: **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Guardar. En uno o dos minutos la página queda en línea.
