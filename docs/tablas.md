# Creación de Tablas

Las tablas son una herramienta fundamental para organizar datos de forma estructurada. En LaTeX, crear tablas puede parecer complejo al principio porque debemos definir cada línea y columna manualmente, pero esto permite un control absoluto sobre el diseño.

## 1. La Estructura Básica (Entorno Tabular)

El entorno fundamental para crear una cuadrícula de datos es `tabular`.

Copia este ejemplo para ver una tabla sencilla con bordes:

```latex
\begin{center}
    \begin{tabular}{|l|c|r|}
        \hline
        \textbf{Producto} & \textbf{Cantidad} & \textbf{Precio (€)} \\
        \hline
        Teclado Mecánico & 5 & 120.00 \\
        Ratón Gaming     & 12 & 45.50 \\
        Alfombrilla XXL  & 20 & 15.00 \\
        \hline
    \end{tabular}
\end{center}
```

### Desglose de la Sintaxis

Para entender el código anterior, mira esta tabla de referencia:

| Símbolo | Significado | Ejemplo |
| :--- | :--- | :--- |
| `\begin{tabular}{...}` | Inicia la tabla y define las columnas. | `{lcr}` |
| `l`, `c`, `r` | Alineación de columna: **L**eft (Izquierda), **C**enter (Centro), **R**ight (Derecha). | `c` |
| `|` (Barra vertical) | Dibuja una línea vertical entre columnas. | `{|c|c|}` |
| `&` (Ampersand) | Separa el contenido de una celda y la siguiente. | `Dato 1 & Dato 2` |
| `\\` (Doble barra) | Indica el final de la fila (Salto de línea). | `Dato final \\` |
| `\hline` | Dibuja una línea horizontal (**H**orizontal **Line**). | `\hline` |

## 2. Tablas Profesionales (Entorno Table)

Al igual que con las imágenes, raramente queremos una tabla "suelta" en el texto. Lo correcto es usar un entorno "flotante" que permita ponerle **título**, **número** y **centrado**.

Para ello, envolvemos el `tabular` dentro de un entorno `table`:

```latex
\begin{table}[h]
    \centering % Centra la tabla en la página
    
    \begin{tabular}{||c c c||} 
        \hline
        ID & Nombre & Nota \\ [0.5ex] 
        \hline\hline
        1 & Ana García & 9.5 \\ 
        2 & Luis Bo & 4.2 \\
        3 & Clara Sanz & 8.0 \\
        \hline
    \end{tabular}
    
    \caption{Calificaciones del examen final}
    \label{tabla:notas}
\end{table}
```

### Ventajas del entorno `table`:
1.  **Numeración automática:** La tabla se llamará "Cuadro 1" o "Tabla 1".
2.  **Lista de Tablas:** Permite generar un índice de tablas al inicio del documento con el comando `\listoftables`.
3.  **Referencias:** Puedes citarla en el texto usando `\ref{tabla:notas}`.

## 3. Unir Celdas (Multicolumn)

A veces necesitamos que una celda ocupe el espacio de varias columnas (por ejemplo, para un título de cabecera).

Se usa el comando `\multicolumn{número}{alineación}{texto}`.

```latex
\begin{tabular}{|c|c|}
    \hline
    \multicolumn{2}{|c|}{\textbf{Lista de Precios}} \\
    \hline
    Producto & Coste \\
    \hline
    Papel & 5€ \\
    \hline
\end{tabular}
```

## 4. Generadores Automáticos (¡Truco Pro!)

Escribir tablas grandes a mano (`&`, `&`, `\\`) es propenso a errores y muy tedioso.

!!! tip "Recomendación de Experto"
    No pierdas tiempo escribiendo el código de tablas complejas desde cero.
    
    Utiliza la herramienta gratuita online **[Tables Generator](https://www.tablesgenerator.com)**.
    
    1.  Dibujas la tabla como si fuera Excel.
    2.  Pulsas "Generate".
    3.  Copias el código y lo pegas en Overleaf.
    
    Es la forma más rápida y segura de trabajar.

!!! warning "Estilo Académico"
    En publicaciones científicas profesionales (IEEE, ACM), se recomienda **no usar líneas verticales** (`|`) para separar columnas, ya que dificultan la lectura. Se prefiere usar solo líneas horizontales para separar la cabecera de los datos.