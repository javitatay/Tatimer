# Timer · Temporizador para shows en vivo

Temporizador standalone para monitor del ponente en eventos, conferencias y shows en vivo. Incluye gestión de sesiones con ponentes, tiempos y títulos de ponencia, y vistas independientes para escenario y sala.

**→ [javitatay.github.io/Tatimer](https://javitatay.github.io/Tatimer/)**

Disponible online sin instalación. También funciona descargando `index.html` y abriéndolo localmente en cualquier navegador — sin dependencias, sin servidor.

---

## Características

- Cuenta atrás, cuenta adelante y reloj en tiempo real
- **Gestión de sesiones** — panel lateral con ponentes, títulos y tiempos individuales
- **Vista Escenario** — timer a pantalla completa sincronizado para el monitor del ponente
- **Vista Audience** — pantalla de sala con nombre y título del ponente activo, controlada manualmente por el operador
- Alertas visuales configurables en directo (amarillo y rojo)
- Barra de progreso segmentada en tres zonas de color con marcador triangular de posición
- Continúa en negativo al terminar el tiempo, con aviso de tiempo consumido
- Mensajes al ponente en pantalla en tiempo real, visibles también en la vista Escenario
- Modo limpio — solo el contador y la barra de progreso a tamaño máximo
- Blackout — pantalla negra completa, el contador sigue corriendo por debajo
- Tema oscuro / claro
- Selector de idioma ES / EN
- Totalmente adaptativo — funciona en cualquier resolución y tamaño de ventana
- Control por URL para integración con QLab u otras herramientas de show control

---

## Uso

### Online

Abre [javitatay.github.io/Tatimer](https://javitatay.github.io/Tatimer/) en Safari o Chrome y arrastra la ventana al monitor del ponente. No necesita instalación ni conexión posterior.

### Local (offline)

1. Descarga `index.html`
2. Ábrelo en Safari o Chrome
3. Arrastra la ventana al monitor del ponente

Las fuentes de Google Fonts quedan en caché tras la primera carga. Para uso completamente offline desde el primer momento, las fuentes se cargarán con las del sistema.

---

## Vistas adicionales

El operador puede abrir dos vistas independientes desde los botones de la esquina inferior derecha o con los atajos de teclado. Cada vista se abre en una ventana nueva que se puede arrastrar a otra pantalla y poner en pantalla completa (`F11`). La comunicación entre ventanas usa `localStorage` y funciona tanto en local (`file://`) como publicado en cualquier servidor.

### Vista Escenario (`E`)

Pensada para el **monitor del ponente** en el escenario. Muestra únicamente el timer a pantalla completa con fondo negro, la barra de progreso con los mismos umbrales de color configurados en el operador, el banner de tiempo consumido al pasar de cero, y los mensajes que el operador envía desde la interfaz principal. Se actualiza en tiempo real, tick a tick.

Si la ventana pierde la señal más de 4 segundos muestra un indicador de conexión perdida.

### Vista Audience (`A`)

Pensada para proyectar en la **sala de espera o hall** mientras se hace el cambio entre ponentes. Muestra el nombre del ponente en grande, el título de su ponencia, la duración asignada y el nombre de la sesión. El contenido no cambia automáticamente — el operador decide el momento exacto pulsando el botón **Publicar** en el panel de sesiones, lo que permite preparar el cambio sin que la sala lo vea antes de tiempo.

Al abrir la ventana carga el último ponente publicado, si lo hay.

### Flujo de trabajo con vistas

1. Pulsa `E` — se abre la vista Escenario; arrástrala al monitor del escenario y pon pantalla completa
2. Pulsa `A` — se abre la vista Audience; arrástrala al proyector de sala y pon pantalla completa
3. Trabaja desde la ventana principal del operador con normalidad
4. Cuando llegue el turno de un ponente, cárgalo desde el panel de sesiones, pulsa **Publicar** para que aparezca en la sala, y arranca el timer

---

## Panel de sesiones

El panel lateral de sesiones permite organizar un congreso o evento con varias ponencias antes del show. Se abre desde el tab `❮❮` del borde izquierdo o con la tecla `P`.

### Estructura

Cada **sesión** agrupa una lista de **ponentes**, cada uno con:
- Nombre del ponente
- Título de la ponencia
- Duración asignada (minutos : segundos)

Se pueden crear y gestionar múltiples sesiones — una por bloque del evento, por ejemplo. Las sesiones se guardan automáticamente en el navegador (`localStorage`) y persisten entre recargas.

### Flujo de trabajo habitual

1. Abre el panel (`P` o el tab lateral)
2. Crea una sesión nueva y ponle nombre
3. Añade los ponentes con sus tiempos desde el formulario inferior
4. Reordena las tarjetas arrastrando si es necesario
5. Durante el evento, haz clic en la tarjeta del ponente activo: el tiempo se carga automáticamente en el timer y hace reset
6. Pulsa **Publicar** para enviar ese ponente a la vista Audience
7. Pulsa `Space` para arrancar

### Opciones del panel

| Elemento | Función |
|---|---|
| Campo de nombre | Nombre de la sesión activa. `Enter` o *Guardar* para confirmar |
| *Nueva* | Crea una sesión vacía |
| *Eliminar sesión* | Borra la sesión activa con confirmación |
| Tarjeta de ponente | Click para cargar su tiempo en el timer |
| `⠿` (asa de arrastre) | Reordena ponentes por drag & drop |
| `✕` | Elimina el ponente de la lista |
| Total | Duración acumulada de todos los ponentes de la sesión |
| **Publicar** | Envía el ponente actualmente cargado a la vista Audience |
| `↓ JSON` | Exporta la sesión activa como archivo `.json` |
| `↑ JSON` | Importa una sesión desde un archivo `.json` |

### Formato de exportación / importación

```json
{
  "id": "abc123",
  "name": "Mañana — Bloque A",
  "speakers": [
    { "id": "x1", "name": "Ana García", "title": "Inteligencia artificial aplicada", "min": 20, "sec": 0 },
    { "id": "x2", "name": "Marc Puig",  "title": "Diseño de experiencia sonora",    "min": 15, "sec": 0 }
  ]
}
```

También se acepta un array plano de ponentes sin envoltura de sesión.

---

## Controles en pantalla

| Elemento | Ubicación | Función |
|---|---|---|
| `❮❮` / `❯❯` | Borde izquierdo | Abre / cierra el panel de sesiones |
| Minutos / Segundos | Panel izquierdo | Configura el tiempo inicial. Se actualiza en tiempo real al editar. |
| Cuenta atrás / Cuenta adelante / Reloj | Panel derecho | Cambia el modo del temporizador |
| Alerta amarilla (min) | Panel derecho | Minutos restantes para activar el aviso amarillo |
| Alerta roja (min) | Panel derecho | Minutos restantes para activar el aviso rojo |
| ES / EN | Panel derecho | Cambia el idioma de la interfaz |
| ◐ | Panel derecho | Alterna entre tema oscuro y tema claro |
| Iniciar / Reanudar | Centro inferior | Arranca o reanuda el contador |
| Pausar | Centro inferior | Pausa sin perder el tiempo |
| −30 seg | Centro inferior | Resta 30 segundos al tiempo |
| +1 min | Centro inferior | Añade 1 minuto al tiempo |
| Reset | Centro inferior | Vuelve al estado inicial |
| Blackout | Centro inferior | Cubre la pantalla con negro. El contador sigue corriendo. |
| Escenario | Esquina inferior derecha | Abre / enfoca la vista Escenario |
| Audience | Esquina inferior derecha | Abre / enfoca la vista Audience |
| ⊞ | Esquina inferior derecha | Activa / desactiva el modo limpio |

---

## Atajos de teclado

| Tecla | Acción |
|---|---|
| `Space` | Iniciar / Pausar |
| `R` | Reset |
| `M` | +1 minuto |
| `S` | −30 segundos |
| `B` | Blackout |
| `C` | Modo limpio / vista completa |
| `P` | Abrir / cerrar panel de sesiones |
| `E` | Abrir / enfocar vista Escenario |
| `A` | Abrir / enfocar vista Audience |

---

## Modos

**Cuenta atrás** — introduce minutos y segundos antes de empezar. Al llegar a cero el contador continúa en negativo para no interrumpir, y aparece un aviso de tiempo consumido en la parte superior.

**Cuenta adelante** — arranca desde cero y cuenta el tiempo transcurrido.

**Reloj** — muestra la hora actual en formato HH:MM:SS. No requiere iniciar ni pausar.

---

## Barra de progreso

La barra muestra tres zonas de color fijas — verde, amarillo y rojo — cuyo tamaño proporcional se calcula a partir de los umbrales de alerta configurados. Un marcador triangular blanco indica la posición actual del tiempo. A medida que avanza el cronómetro, la zona ya consumida se oscurece y el marcador viaja hacia la izquierda.

Los umbrales se pueden ajustar en directo durante el show sin reiniciar el contador; la barra se recalcula al instante. La vista Escenario refleja los mismos umbrales y colores.

---

## Alertas de tiempo

Dos umbrales independientes configurables en el panel derecho:

- **Alerta amarilla** — minutos restantes para que el display y el marcador cambien a amarillo
- **Alerta roja** — minutos restantes para que el display y el marcador cambien a rojo

---

## Mensajes al ponente

El operador escribe en la caja de texto inferior y pulsa `Enter`. El texto aparece en pantalla grande en amarillo tanto en la ventana principal como en la vista Escenario, visible desde el escenario. `Esc` o el botón *Borrar* lo eliminan en ambas pantallas simultáneamente.

---

## Blackout

El botón *Blackout* (o la tecla `B`) cubre toda la pantalla con negro. El contador sigue corriendo por debajo. Pulsar de nuevo el botón, la tecla `B` o hacer clic en cualquier parte de la pantalla negra desactiva el blackout y muestra el tiempo real transcurrido.

---

## Modo limpio

El botón de maximizar (esquina inferior derecha) oculta todos los controles y muestra únicamente el contador y la barra de progreso a tamaño máximo. El panel de sesiones y los botones de vistas también se ocultan en este modo. Útil cuando el monitor del ponente está cerca del público. La tecla `C` hace lo mismo.

---

## Control por URL

El temporizador acepta parámetros en la URL para integrarse con herramientas de show control como QLab:

```
https://javitatay.github.io/Tatimer/?action=start
https://javitatay.github.io/Tatimer/?action=pause
https://javitatay.github.io/Tatimer/?action=reset
https://javitatay.github.io/Tatimer/?action=addminute
https://javitatay.github.io/Tatimer/?action=subtractthirty
https://javitatay.github.io/Tatimer/?action=start&minutes=10&seconds=0
https://javitatay.github.io/Tatimer/?action=start&mode=countup
https://javitatay.github.io/Tatimer/?action=start&mode=clock
https://javitatay.github.io/Tatimer/?lang=en
```

Las vistas también se pueden abrir directamente por URL:

```
https://javitatay.github.io/Tatimer/?view=escenario
https://javitatay.github.io/Tatimer/?view=audience
```

---

## Estructura del repositorio

```
Tatimer/
│
├── README.md
├── LICENSE
└── index.html
```

---

## Licencia

MIT — libre para uso en producción comercial y no comercial.

---

## Autor

Javier Tatay Rubio
*Probado en macOS Sonoma 14 · Safari · Google Chrome 124+*
