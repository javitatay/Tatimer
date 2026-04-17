# Timer · Temporizador para shows en vivo

Temporizador standalone para monitor del ponente en eventos, conferencias y shows en vivo. Se abre directamente en cualquier navegador — sin instalación, sin conexión a internet, sin dependencias.

Disponible en https://javitatay.github.io/Tatimer/
---

## Características

- Cuenta atrás y cuenta adelante
- Alertas visuales configurables en directo (amarillo y rojo)
- Continúa en negativo al terminar el tiempo, con aviso de tiempo consumido
- Mensajes al ponente en pantalla en tiempo real
- Modo limpio — solo el contador y la barra de progreso a tamaño máximo
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
| Cuenta atrás / Cuenta adelante | Panel derecho | Cambia el modo del temporizador |
| Alerta amarilla (min) | Panel derecho | Minutos restantes para activar el aviso amarillo |
| Alerta roja (min) | Panel derecho | Minutos restantes para activar el aviso rojo |
| ES / EN | Panel derecho | Cambia el idioma de la interfaz |
| Iniciar / Reanudar | Centro inferior | Arranca o reanuda el contador |
| Pausar | Centro inferior | Pausa sin perder el tiempo |
| −30 seg | Centro inferior | Resta 30 segundos al tiempo restante |
| +1 min | Centro inferior | Añade 1 minuto al tiempo restante |
| Reset | Centro inferior | Vuelve al estado inicial |
| ⊞ | Esquina inferior derecha | Activa / desactiva el modo limpio |

---

## Atajos de teclado

| Tecla | Acción |
|---|---|
| `Space` | Iniciar / Pausar |
| `R` | Reset |
| `M` | +1 minuto |
| `S` | −30 segundos |
| `C` | Modo limpio / vista completa |

---

## Mensajes al ponente

El operador escribe en la caja de texto inferior y pulsa `Enter`. El texto aparece en pantalla grande en amarillo, visible desde el escenario. `Esc` o el botón *Borrar* lo eliminan. El mensaje permanece visible en modo limpio.

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
