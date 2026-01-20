# Gestión de Bibliografía con BibTeX

La gestión de citas y referencias bibliográficas es, sin duda, la característica más potente de LaTeX. Olvídate de ordenar alfabéticamente tu lista de fuentes o de pelearte con el formato APA o IEEE a mano.

El sistema estándar para hacer esto se llama **BibTeX**. Funciona separando la información de tus fuentes (base de datos) del formato visual.

## 1. El Archivo de Base de Datos (.bib)

En lugar de escribir la bibliografía al final del documento, creamos un archivo externo que contiene toda la información de los libros y artículos que hemos leído.

1.  En el panel izquierdo de Overleaf, crea un **New File**.
2.  Llámalo `referencias.bib`.
3.  Dentro, pegamos las entradas en formato BibTeX.

### Ejemplo de contenido para `referencias.bib`:

```bibtex
% Entrada para un Libro
@book{hawking1988,
  title={A Brief History of Time},
  author={Hawking, Stephen},
  year={1988},
  publisher={Bantam Books},
  address={New York}
}

% Entrada para un Artículo Científico
@article{einstein1905,
  title={Zur Elektrodynamik bewegter Körper},
  author={Einstein, Albert},
  journal={Annalen der Physik},
  volume={322},
  number={10},
  pages={891--921},
  year={1905}
}

% Entrada para una Página Web
@misc{overleafDoc,
  title={Overleaf Documentation},
  author={Overleaf},
  year={2023},
  howpublished={\url{[https://www.overleaf.com/learn](https://www.overleaf.com/learn)}},
  note={Accedido: 20-01-2026}
}
```

## 2. Conectar la Bibliografía al Documento

Una vez tienes tu archivo `.bib` listo, debes decirle a tu documento principal (`main.tex`) que lo use.

Añade estas dos líneas al final de tu documento, justo antes de cerrar el cuerpo (`\end{document}`):

```latex
% ... Resto del documento ...

\newpage % Salto de página para que la biblio quede separada

% 1. Elegimos el estilo de cita
\bibliographystyle{plain} 

% 2. Indicamos el archivo .bib (sin la extensión)
\bibliography{referencias} 

\end{document}
```

## 3. Cómo Citar en el Texto

Para que una referencia aparezca en la lista final, **tienes que citarla** dentro del texto. Si tienes un libro en el archivo `.bib` pero no lo citas, no aparecerá en el PDF.

Se usa el comando `\cite{clave}`. La "clave" es la primera palabra que pusimos en el archivo .bib (ej: `hawking1988`).

```latex
\section{Estado del Arte}

Como discutió Stephen Hawking en su famoso libro \cite{hawking1988}, el tiempo es relativo. 
Por otro lado, la teoría de la relatividad especial fue introducida años antes \cite{einstein1905}.

Según la documentación oficial \cite{overleafDoc}, es fácil aprender.
```

### Resultado Visual

Al compilar, LaTeX transformará el código en algo así:

> Como discutió Stephen Hawking en su famoso libro [1], el tiempo es relativo...

Y generará automáticamente la sección "Referencias" al final ordenada correctamente.

## 4. Estilos de Bibliografía

Puedes cambiar radicalmente cómo se ven las citas simplemente cambiando una palabra en el comando `\bibliographystyle{...}`. No tienes que reescribir nada.

| Estilo | Comando | Resultado Visual | Uso Común |
| :--- | :--- | :--- | :--- |
| **Numérico** | `plain` | [1], [2] | Ciencias, Ingeniería |
| **Abreviado** | `abbrv` | [1] (Nombres abreviados) | Matemáticas |
| **Autor-Año** | `apalike` | (Hawking, 1988) | Psicología, Sociales (APA) |
| **IEEE** | `ieeetr` | [1] (Orden de aparición) | Ingeniería Eléctrica |

!!! tip "Truco: Google Scholar"
    No escribas las fichas BibTeX a mano. Ve a [Google Scholar](https://scholar.google.com), busca el libro o artículo, pulsa en el botón de comillas ("Citar") y selecciona **BibTeX**. Copia el código que te da y pégalo en tu archivo `referencias.bib`.

!!! warning "Compilación"
    A veces, al añadir bibliografía nueva, Overleaf necesita compilar varias veces para actualizar los números. Si ves signos de interrogación `[?]` en lugar de números, pulsa el botón "Recompile" de nuevo.