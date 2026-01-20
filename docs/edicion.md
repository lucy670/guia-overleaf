# Editando Documentos

Lo mejor de Overleaf es que puedes escribir código LaTeX directamente.

## Estructura Básica

Todo documento debe empezar con esta estructura de código:

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}

\title{Mi Primer Paper}
\author{Tu Nombre}
\date{Enero 2026}

\begin{document}

\maketitle

\section{Introducción}
Aquí escribimos el texto normal.

\end{document}
