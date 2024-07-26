Desarrolla un módulo de selector de grupos en un sistema para escuelas.

La escuelas tienen una estructura jerárquica para llegar hasta los grupos, la cual es la siguiente:
Niveles académicos:
- Primaria
- Secundaria
- Etc.

Cada Nivel académico tiene sus respectivos Grados:
- 1
- 2
- 3
- Etc.

Cada Grado tiene sus Grupos:
- P1A
- P1B
- Etc.

Ahora bien, lo que quiero es que desarrolles un selector con las siguientes características.

Características visuales:
- Debe existir un contenedor que contenga el selector de grupos. El contenedor debe estar maquetado. 
  - Sección Título. Una sección será para el título, y abarcará todo el ancho del contenedor.
  - Sección Ver grupos. La siguiente sección será un contenedor con el checkbox que diga Ver grupos y estará alineado a la derecha.
  - Sección Seleccionar todo. La siguiente sección deberá contener una etiqueta que diga Seleccionar todo.
  - Sección Selector de grupos. La siguiente sección será el selector.
  - Sección Aceptar selección. Por último, la última sección deberá contener un botón que diga Aceptar selección. Ubicado en la parte inferior del contenedor principal y alineado a la izquierda.

Sección Selector de grupos:
Cuando no esté activado el checkbox Ver grupos.
- Debe mostrar solo los Niveles académicos con sus respectivos Grados.
- En esta primera vista deberá mostrar la lista vertical los Niveles académicos y sus respectivos grados. Los Grados deberán mostrarse a la derecha de su respectivo Nivel académico. Ejemplo:
|Primaria|1|2|3|4|5|6|
|Secundaria|1|2|3|

Cuando sí esté activado el checkbox Ver grupos.
- Debe mostrar los Niveles académicos con sus respectivos grados, además de mostrar los respectivos grupos de cada grado. Las posiciones de los elementos quedará como se muestra en el siguiente ejemplo. Ejemplo:
|Primaria|
1|P1A|P1B|
2|P1A|P1B|
3|...
4|...
5|...
6|...
|Secundaria|
1|Secundaria 1A|S1B|
2|...
3|...

Los datos que se mostrarán como nombre del Nivel académico, Nombre del Grado y Nombre del grupo serán alimentadas a través de un archivo json con la siguiente estructura:
{
  "P": { // Nivel académico
    "ClaveSeccion": "P",
    "NombreCorto": "Primaria",
    "Grupos": {
          "1": { // Grado
            "P1A": { // Grupo
                  "Grupo": "P1A",
                  "Alias": "P1A"
              }
          }
    }
  }
}

Características funcionales
- Al seleccionar un grupo me deberá pintar el grupo seleccionado.
- Al seleccionar un grado me deberá pintar los grupos seleccionados (si no está habilitado Ver grupos solo me pinta el grado seleccionado).
- Al seleccionar el Nivel académico me deberá seleccionar los grados y grupos correspondientes (si no está habilitado Ver grupos solo deberá seleccionar los grados correspondientes).
- Al seleccionar la etiqueta Seleccionar todo pintar todos los elementos del selector que se muestran en pantalla: grupos, grados y niveles académicos. Al volver a presionar Seleccionar todo se despinta todo. Optimiza de la mejor manera la funcionalidad de la etiqueta Seleccionar todo.