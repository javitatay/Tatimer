# Timer · Temporizador para shows en vivo

Temporizador standalone para monitor del ponente en eventos, conferencias y shows en vivo. Se abre directamente en cualquier navegador — sin instalación, sin conexión a internet, sin dependencias.

---

## Características

- Cuenta atrás, cuenta adelante y reloj en tiempo real
- Alertas visuales configurables en directo (amarillo y rojo)
- Barra de progreso segmentada en tres zonas de color con marcador triangular de posición
- Continúa en negativo al terminar el tiempo, con aviso de tiempo consumido
- Mensajes al ponente en pantalla en tiempo real
- Modo limpio — solo el contador y la barra de progreso a tamaño máximo
- Blackout — pantalla negra completa, el contador sigue corriendo por debajo
- Tema oscuro / claro
- Selector de idioma ES / EN
- Totalmente adaptativo — funciona en cualquier resolución y tamaño de ventana
- Control por URL para integración con QLab u otras herramientas de show control

---

## Uso

1. Descarga `timer.html`
2. Ábrelo en Safari o Chrome
3. Arrastra la ventana al monitor del ponente

No necesita servidor, ni conexión a internet después de cargar las fuentes de Google Fonts la primera vez. Para uso completamente offline, las fuentes se cargarán con las del sistema.

---

## Controles en pantalla

| Elemento | Ubicación | Función |
|---|---|---|
| Minutos / Segundos | Panel izquierdo | Configura el tiempo inicial. Se actualiza en tiempo real al editar. |
| Cuenta atrás / Cuenta adelante / Reloj | Panel derecho | Cambia el modo del temporizador |
| Alerta amarilla (min) | Panel derecho | Minutos restantes para activar el aviso amarillo |
| Alerta roja (min) | Panel derecho | Minutos restantes para activar el aviso rojo |
| ES / EN | Panel derecho | Cambia el idioma de la interfaz |
| ◐ / ○ | Panel derecho | Cambia entre tema oscuro y tema claro |
| Iniciar / Reanudar | Centro inferior | Arranca o reanuda el contador |
| Pausar | Centro inferior | Pausa sin perder el tiempo |
| −30 seg | Centro inferior | Resta 30 segundos al tiempo restante |
| +1 min | Centro inferior | Añade 1 minuto al tiempo restante |
| Reset | Centro inferior | Vuelve al estado inicial |
| Blackout | Centro inferior | Cubre la pantalla con negro. El contador sigue corriendo. |
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

---

## Modos

**Cuenta atrás** — introduce minutos y segundos antes de empezar. Al llegar a cero el contador continúa en negativo para no interrumpir, y aparece un aviso de tiempo consumido en la parte superior.

**Cuenta adelante** — arranca desde cero y cuenta el tiempo transcurrido.

**Reloj** — muestra la hora actual en formato HH:MM:SS. No requiere iniciar ni pausar.

---

## Barra de progreso

La barra muestra tres zonas de color fijas — verde, amarillo y rojo — cuyo tamaño proporcional se calcula a partir de los umbrales de alerta configurados. Un marcador triangular blanco indica la posición actual del tiempo. A medida que avanza el cronómetro, la zona ya consumida se oscurece y el marcador viaja hacia la izquierda.

Los umbrales se pueden ajustar en directo durante el show sin reiniciar el contador; la barra se recalcula al instante.

---

## Alertas de tiempo

Dos umbrales independientes configurables en el panel derecho:

- **Alerta amarilla** — minutos restantes para que el display y el marcador cambien a amarillo
- **Alerta roja** — minutos restantes para que el display y el marcador cambien a rojo

---

## Mensajes al ponente

El operador escribe en la caja de texto inferior y pulsa `Enter`. El texto aparece en pantalla grande en amarillo, visible desde el escenario. `Esc` o el botón *Borrar* lo eliminan. El mensaje permanece visible en modo limpio.

---

## Blackout

El botón *Blackout* (o la tecla `B`) cubre toda la pantalla con negro. El contador sigue corriendo por debajo. Pulsar de nuevo el botón, la tecla `B` o hacer clic en cualquier parte de la pantalla negra desactiva el blackout y muestra el tiempo real transcurrido.

---

## Modo limpio

El botón de maximizar (esquina inferior derecha) oculta todos los controles y muestra únicamente el contador y la barra de progreso a tamaño máximo. Útil cuando el monitor del ponente está cerca del público. La tecla `C` hace lo mismo.

---

## Control por URL

El temporizador acepta parámetros en la URL para integrarse con herramientas de show control:

```
timer.html?action=start
timer.html?action=pause
timer.html?action=reset
timer.html?action=addminute
timer.html?action=subtractthirty
timer.html?action=start&minutes=10&seconds=0
timer.html?action=start&mode=countup
timer.html?action=start&mode=clock
timer.html?lang=en
```

---

## Estructura del repositorio

```
timer/
│
├── README.md
├── LICENSE
└── timer.html
```

---

## Licencia

MIT — libre para uso en producción comercial y no comercial.

---

## Autor

Javier Tatay Rubio
*Probado en macOS Sonoma 14 · Safari · Google Chrome 124+*
