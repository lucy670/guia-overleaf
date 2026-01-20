# Solución de Problemas Comunes

LaTeX es un lenguaje compilado. Esto significa que si cometes un error de sintaxis, el documento no se generará (o saldrá roto) y el sistema te lanzará un mensaje de error. Aprender a leer estos mensajes es parte del aprendizaje.

## Cómo leer los errores en Overleaf

Cuando la compilación falla, el botón de "Recompile" mostrará un icono rojo con el número de errores. Si haces clic en el icono de "Logs and output files" (el folio junto al botón de compilar), verás el detalle.

Aquí recopilamos los 5 errores más frecuentes y cómo solucionarlos.

## 1. "Missing $ inserted"

Este es, con diferencia, el error número 1.

**Causa:** Has utilizado un carácter reservado para matemáticas (como `_`, `^`, `\alpha`, `\sum`) dentro de un texto normal. LaTeX intenta arreglarlo insertando un signo de dólar `$` automáticamente, pero suele fallar.

* ✘ **Mal:** El valor de x_2 es la suma de a+b.
* ✓ **Bien:** El valor de $x_2$ es la suma de $a+b$.

!!! tip "Solución"
    Busca guiones bajos `_` o circunflejos `^` en tu texto y asegúrate de que están rodeados por signos de dólar `$ ... $`.

## 2. "Undefined control sequence"

**Causa:** Has escrito un comando que LaTeX no conoce. Suele ser por dos razones:
1.  **Un error tipográfico:** Escribiste `\textbff{}` en lugar de `\textbf{}` o `\sectionn{}`.

2.  **Falta un paquete:** Estás intentando usar un comando (ej: `\includegraphics`) sin haber cargado la librería necesaria en el preámbulo (`\usepackage{graphicx}`).

```latex
! Undefined control sequence.
l.15 \textbff
            {Texto en negrita}
```
*En este ejemplo, sobra una 'f' en `textbf`.*

## 3. "File not found"

**Causa:** LaTeX intenta cargar una imagen o una bibliografía que no encuentra.

* **Razón A:** Te has equivocado en el nombre. Recuerda que **Linux es sensible a mayúsculas**. `Logo.png` no es lo mismo que `logo.png`.
* **Razón B:** La ruta es incorrecta. Si la imagen está en una carpeta, debes indicarlo.
* **Razón C:** El nombre del archivo tiene espacios (LaTeX odia los espacios en nombres de archivo).

!!! failure "Ejemplo de Error"
    `LaTeX Error: File 'img/Mi Foto.png' not found.`
    
    **Solución:** Renombra el archivo a `mi_foto.png` (sin espacios) y actualiza el código.

## 4. "Runaway argument?" / "File ended while..."

**Causa:** Has abierto una llave `{` o un entorno `\begin{...}` y se te ha olvidado cerrarlo. LaTeX sigue leyendo buscando el cierre hasta que se acaba el archivo.

```latex
\textbf{Esto es un texto en negrita muy largo...
\section{Siguiente sección}
```
*Aquí falta cerrar la llave después de "largo...".*

**Solución:** Busca el último lugar donde editaste antes del error y cuenta las llaves.

## 5. "Timeout" (Tiempo de espera agotado)

A veces Overleaf se queda pensando y al final dice "Compile Error: Timeout".

**Causa:** Probablemente has creado un **bucle infinito** en tus comandos o estás intentando procesar una imagen de altísima resolución que satura la memoria.

**Solución:**

1.  Revisa si tienes definiciones recursivas.

2.  Comprime tus imágenes (usa JPG en lugar de PNG pesados).

3.  Si es un documento muy largo, utiliza la función "Draft mode" para compilar sin imágenes temporalmente.

!!! note "El Pánico Nuclear"
    Si tienes **demasiados errores** y no sabes por dónde empezar:
    
    1.  Borra el archivo `.aux` (icono de papelera en el panel de logs de Overleaf).
    2.  Comenta (`%`) lo último que escribiste.
    3.  Intenta compilar de nuevo.
    4.  Ve descomentando línea a línea hasta encontrar el culpable.