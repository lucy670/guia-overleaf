# Edición de Texto y Estructura

En este apartado aprenderás los conceptos fundamentales para escribir en LaTeX. A diferencia de Word, aquí no aplicamos formato seleccionando texto y pulsando botones, sino que utilizamos **comandos** que definen la estructura lógica del documento.

## 1. Estructura de un Archivo .tex

Todo documento en Overleaf debe seguir una estructura estricta dividida en dos partes: el **Preámbulo** (configuración) y el **Cuerpo** (contenido).

Copia este esqueleto básico para empezar cualquier proyecto:

```latex
\documentclass[12pt, a4paper]{article}

% --- PREÁMBULO ---
% Aquí cargamos los paquetes necesarios
\usepackage[utf8]{inputenc} % Permite escribir tildes y ñ
\usepackage[spanish]{babel} % Traduce "Table of Contents" a "Índice", etc.
\usepackage{geometry}       % Para configurar márgenes

% Datos para la portada
\title{Mi Primer Documento en Overleaf}
\author{Nombre del Autor}
\date{\today}

% --- CUERPO DEL DOCUMENTO ---
\begin{document}

\maketitle % Genera el título automáticamente

\section{Introducción}
Aquí empieza el contenido real de nuestro trabajo.

\end{document}
```

## 2. Formato de Texto

Para dar énfasis a ciertas palabras, utilizamos comandos específicos. Estos son los más comunes:

| Estilo | Comando LaTeX | Resultado Visual |
| :--- | :--- | :--- |
| **Negrita** | `\textbf{Texto}` | **Texto** |
| *Cursiva* | `\textit{Texto}` | *Texto* |
| Subrayado | `\underline{Texto}` | <u>Texto</u> |
| Monoespacio | `\texttt{Texto}` | `Texto` (tipo máquina de escribir) |
| MAYÚSCULAS | `\textsc{Texto}` | Versalitas (Small Caps) |

!!! tip "Consejo de Edición"
    Evita usar el subrayado (`\underline`) en documentos académicos profesionales. Se prefiere el uso de *cursiva* para énfasis o **negrita** para destacar términos clave.

## 3. Organización por Secciones

LaTeX numera automáticamente los apartados. No tienes que escribir "1. Introducción" a mano, el sistema lo hace por ti si usas estos comandos:

```latex
\section{Título del Nivel 1}
Texto de la sección principal.

\subsection{Título del Nivel 2}
Texto de la subsección.

\subsubsection{Título del Nivel 3}
Texto del apartado más específico.
```

## 4. Listas y Viñetas

Las listas son esenciales para organizar la información. Existen dos tipos principales:

### Listas No Ordenadas (itemize)
Se usan para puntos (bullets) sin orden específico.

```latex
\begin{itemize}
    \item Primer punto importante.
    \item Segundo punto importante.
    \item Tercer punto con \textbf{negrita} incluida.
\end{itemize}
```

### Listas Ordenadas (enumerate)
Se usan para pasos secuenciales (1, 2, 3...).

```latex
\begin{enumerate}
    \item Abrir el archivo.
    \item Escribir el código.
    \item Compilar el PDF.
\end{enumerate}
```

## 5. Caracteres Especiales (¡Cuidado!)

En LaTeX, hay símbolos que tienen un significado reservado y **no se pueden escribir directamente** en el texto. Si los escribes, te dará error al compilar.

Si necesitas que aparezcan en tu texto, debes "escaparlos" poniendo una barra invertida `\` delante:

* **Porcentaje %:** Se usa para comentarios. Escribe `\%` para mostrarlo.
* **Dólar $:** Se usa para matemáticas. Escribe `\$` para mostrarlo.
* **Llaves { }:** Se usan para agrupar comandos. Escribe `\{` y `\}`.
* **Ampersand &:** Se usa para tablas. Escribe `\&`.
* **Barra invertida \:** Usa el comando `\textbackslash`.

!!! failure "Error Común"
    Si escribes algo como "El 50% de los usuarios..." sin la barra, todo el texto siguiente desaparecerá porque LaTeX pensará que es un comentario.
    **Correcto:** "El 50\% de los usuarios..."