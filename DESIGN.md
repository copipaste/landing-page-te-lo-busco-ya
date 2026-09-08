# Design system — Te lo busco Ya

## Dirección

**Mundo visual:** despacho operativo y enrutamiento de cotizaciones. La portada debe sentirse como una solicitud que entra en una red de proveedores: precisa, rápida, técnica y confiable; nunca como un marketplace ruidoso ni una campaña aspiracional.

**Modo de persuasión:** reducir fricción y hacer visible el siguiente paso. La promesa se sostiene con proceso concreto (conversación guiada, proveedores auditados, facturación y devolución), categorías claras y el dato verificable de `+500` distribuidores; no se inventan precios, clientes ni testimonios.

## Fundamentos visuales

### Color

No se usa lila. La paleta es neutra industrial —azules pizarra, blanco frío y gris— con rojo de acción y señales verdes/rosadas solo cuando su semántica lo pide.

| Token | Valor | Uso |
| --- | --- | --- |
| `--color-primary` | `#1E293B` | Bloques técnicos oscuros y base industrial. |
| `--color-secondary` | `#334155` | Apoyo de superficies oscuras. |
| `--color-accent` | `#DC2626` | Acción, enlaces de marca, conteos y sección de respaldo. |
| `--color-background` | `#F8FAFC` | Fondo general. |
| `--color-surface` | `#FFFFFF` | Superficies de lectura. |
| `--color-ink` | `#0F172A` | Texto principal y pie. |
| `--color-muted` | `#475569` | Texto secundario. |
| `--color-border` | `#E2E8F0` | Separadores y estructura. |
| `--color-on-dark` | `#F8FAFC` | Texto sobre fondos oscuros. |

El rojo oscuro de hover (`#B91C1C`) confirma interacción. Verde (`#86EFAC`) significa que Lyra está en línea y el rosa claro (`#FCA5A5` / `#FECACA`) queda reservado para acentos secundarios sobre la consola y motivos circulares.

### Tipografía y forma

La familia visible es `TLBY`, autoalojada desde `/inter.woff2`, con reserva `sans-serif`: una interpretación Inter compacta y pragmática. Titulares muy grandes, de peso alto, tracking negativo y líneas cortas dan contundencia; la lectura de apoyo aumenta interlineado y usa gris pizarra. Los números de pasos y el `+500` usan cifras tabulares.

La forma combina reglas finas, cuadrículas, paneles rectos, sombras flotantes profundas y anillos circulares de baja presencia. Los CTA conservan una altura táctil mínima de 44 px (40 px en la cabecera móvil).

## Composición de la portada

1. **Cabecera fija.** Marca, navegación de anclas y CTA rojo. Fondo translúcido con desenfoque para mantener contexto durante el scroll.
2. **Hero / consola.** Copia de problema, CTA inmediato y pruebas de confianza a la izquierda; a la derecha, una ventana embebida de Lyra. Piezas aisladas y órbitas muestran flujo, no catálogo.
3. **Ruta.** Tres pasos numerados, con bordes horizontales: describir, enrutar, comparar.
4. **Índice de piezas.** Panel oscuro de dos columnas con imágenes de radiador/pistón y lista de categorías navegable visualmente.
5. **Respaldo.** Bloque rojo de alto contraste que ancla el dato `+500` y vuelve a invitar al chat.
6. **Pie.** Marca, cobertura y contacto, sin información superflua.
7. **Solicitud especial.** Ruta de excepción para quien no encuentra la pieza: dos columnas a pantalla alta, con contexto técnico azul pizarra y arte de repuestos tenue a la izquierda, y una superficie blanca dedicada al formulario a la derecha. La lectura se apila en una sola columna en anchos reducidos, manteniendo el contexto antes del formulario.

En escritorio predominan las composiciones de dos columnas. A 980 px la hero, ruta y respaldo se apilan; a 700 px se oculta la navegación, el arte baja de prioridad y las secciones conservan ritmo vertical amplio.

## Patrones de componentes

- **Marca:** símbolo WebP más nombre textual; “Ya” toma el rojo de acción.
- **CTA primario:** rojo sólido, texto fuerte e icono de flecha. Hover: rojo más oscuro y elevación de 1 px.
- **Enlace textual:** subrayado visible y flecha; en hover pasa a rojo.
- **Listas operativas:** bordes de separación, números o flechas y estados hover modestos. No se convierten en tarjetas decorativas.
- **Consola Lyra:** panel oscuro con barra de estado, luz verde, nombre, estado “en línea” y contexto “Cotización guiada”. La ventana no es una burbuja flotante: ocupa un área persistente de 570 px (530 px móvil) dentro del hero.
- **Formulario de solicitud especial:** superficie blanca de lectura con encabezado breve, campos apilados y CTA primario a ancho completo. Usa el mismo foco rojo de 3 px y bordes pizarra; tras un intento de envío, los campos inválidos se marcan en rojo y un estado en vivo explica el siguiente paso.

## Comportamiento, accesibilidad y rendimiento

- Lyra se carga como `custom-chatbot` con su script diferido; sus parámetros de marca conservan el rojo `#DC2626`, el nombre y el saludo configurados.
- El único ingreso es una animación breve de la consola (opacidad y desplazamiento vertical); hover y enlaces usan transiciones de 180 ms con curva de salida. Con `prefers-reduced-motion`, se eliminan animaciones, transiciones y scroll suave.
- Se ofrece enlace “Saltar al asistente”, foco visible rojo de 3 px, navegación por anclas, etiquetas ARIA y títulos de sección. Las imágenes puramente decorativas tienen `alt=""`; el título del chat está disponible para lectores de pantalla.
- La solicitud especial ofrece un salto directo al formulario, validación local con los controles nativos y mensajes de estado `aria-live`. Al superar la validación, prepara un correo `mailto:` dirigido a `info@telobuscoya.com`; no añade una dependencia de envío ni promete confirmación de recepción.
- Las fotos de piezas se importan mediante `astro:assets` y se entregan como imágenes optimizadas WebP; las piezas del hero son eager con decodificación asíncrona y las de contenido usan carga diferida. Se evitan dependencias visuales innecesarias y el sitio conserva una carga ligera para conexión móvil.

## Guardrails

- Mantener el chat embebido como centro de conversión y el CTA anclado a `#cotizar`.
- Priorizar evidencias concretas y lenguaje de proceso antes que promesas vagas.
- Preservar contraste alto, tamaños táctiles y la respuesta móvil; añadir movimiento solo si aporta orientación y siempre con alternativa de movimiento reducido.
- Usar el logo entregado y fotografía real de repuestos; no sustituirlos por stock genérico ni inventar prueba social.
