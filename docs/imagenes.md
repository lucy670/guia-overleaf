# Inserción de Imágenes y Gráficos

Una de las tareas más comunes en la documentación técnica es la inclusión de figuras. En Overleaf, esto se gestiona mediante el paquete estándar `graphicx`.

## 1. Configuración Previa

Antes de poder insertar cualquier imagen, debes asegurarte de que tu documento está listo para procesar gráficos. 

Añade esta línea en el **preámbulo** de tu archivo `.tex` (es decir, antes de `\begin{document}`):

```latex
\usepackage{graphicx}
```

## 2. Subir Imágenes a Overleaf

A diferencia de Word, no puedes "copiar y pegar" una imagen directamente en el texto. Debes seguir estos pasos:

1.  En la barra lateral izquierda del proyecto, haz clic en el icono de **Upload** (flecha hacia arriba).
2.  Arrastra tus archivos desde tu ordenador (formatos soportados: `.jpg`, `.png`, `.pdf`).
3.  **Recomendación:** Crea una carpeta nueva llamada `img` o `images` y guarda ahí los archivos para mantener el proyecto ordenado.

## 3. Insertar una Imagen (Entorno Figure)

Para insertar una imagen de forma profesional (centrada, con título y numeración automática), utilizamos el entorno flotante `figure`.

Copia este bloque de código donde quieras que aparezca tu imagen:

```latex
\begin{figure}[h]
    \centering
    % Ajustamos el tamaño al 70% del ancho del texto
    \includegraphics[width=0.7\textwidth]{img/mi-foto.png}
    
    \caption{Descripción de la imagen que aparecerá debajo}
    \label{fig:mi-referencia}
\end{figure}
```

### Explicación de los Parámetros

El código anterior utiliza varios comandos específicos que detallamos en esta tabla:

| Comando | Función |
| :--- | :--- |
| `\begin{figure}[h]` | Inicia el entorno. La `[h]` significa *Here* (intentar ponerla "Aquí"). |
| `\centering` | Centra la imagen horizontalmente en la página. |
| `\includegraphics` | Es el comando que carga el archivo real. |
| `width=0.7\textwidth` | Redimensiona la imagen para que ocupe el 70% del ancho del texto. |
| `\caption{...}` | Añade el pie de foto (ej: "Figura 1: Descripción..."). |
| `\label{...}` | Crea una etiqueta invisible para poder citar la imagen luego. |

## 4. Referencias Cruzadas

Una de las grandes potencias de LaTeX es que numera las figuras automáticamente. Si insertas una imagen nueva al principio, todas las demás se renumeran solas.

Para mencionar una imagen en tu texto, usa el comando `\ref` apuntando al `label` que definiste antes:

```latex
Como podemos observar en la Figura \ref{fig:mi-referencia}, los resultados son positivos.
```

Al compilar el PDF, LaTeX sustituirá `\ref{fig:mi-referencia}` por el número correcto (por ejemplo: "Figura 1").

!!! warning "Cuidado con los Nombres de Archivo"
    Evita usar espacios o caracteres especiales (tildes, ñ) en los nombres de los archivos de imagen.
    
    * ✘ **Mal:** `foto de la niña.png`
    * ✓ **Bien:** `foto_nina.png`
    
    Si usas espacios, el comando `\includegraphics` fallará y dará error.

## 5. Cambiar el Tamaño de la Imagen

Puedes controlar el tamaño exacto modificando los parámetros dentro de los corchetes `[]`:

* **Por ancho de texto:** `width=0.5\textwidth` (mitad del ancho de página).
* **Por centímetros:** `width=5cm`.
* **Por altura:** `height=10cm`.
* **Rotar imagen:** `angle=90` (gira la imagen 90 grados).

Ejemplo combinado:
```latex
\includegraphics[width=5cm, angle=45]{img/foto.png}
```