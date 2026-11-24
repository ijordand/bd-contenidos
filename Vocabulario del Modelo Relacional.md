# Vocabulario del modelo relacional

Una tabla dibujada con cada nombre señalado por un color. Tenla abierta mientras haces los ejercicios del Tema 2. El ejemplo es la relación ESTUDIANTE de tus apuntes (T02).

## Cada pieza de la tabla tiene su nombre

ESTUDIANTE(nombre, edad, carrera)

| nombre | edad | carrera |
| --- | --- | --- |
| "Ana" | 20 | "Informática" |
| "Carlos" | 19 | "Matemáticas" |
| "María" | 21 | "Informática" |
| "Pedro" | 22 | "Física" |

Las 4 filas juntas son la instancia

**3**grado: nº de columnas

**4**cardinalidad: nº de filas

### Esquema

El molde: nombre de la relación y sus atributos. Casi nunca cambia. `ESTUDIANTE(nombre, edad, carrera)`

### Atributo

Una columna: su nombre y lo que significa. Aquí hay tres: `nombre`, `edad`, `carrera`.

### Dominio

Los valores válidos de un atributo: qué puede ir en esa columna. `dom(edad) = {18, 19, 20, …}`

### Tupla

Una fila: un valor por cada atributo, en orden. `("Carlos", 19, "Matemáticas")`

### Valor

Lo que hay en una casilla. Debe ser uno solo (atómico) y del dominio de su columna. `"Informática"`

### Instancia (o estado)

El conjunto de filas en un momento concreto. Cambia con cada inserción, borrado o modificación.

## Palabra de la calle y palabra del examen

| Lo que ves | Cómo se llama en el modelo |
| --- | --- |
| Tabla | Relación |
| Nombre de columna | Atributo |
| Tipo de columna | Dominio |
| Fila | Tupla |
| Definición de la tabla | Esquema de la relación |
| Datos de la tabla | Estado o instancia de la relación |

## Cómo se escribe cada cosa

Esquema

```
ESTUDIANTE(nombre, edad, carrera)
```

Esquema con sus dominios

```
ESTUDIANTE(nombre: texto,
           edad: entero,
           carrera: texto)
```

Dominio de un atributo

```
dom(edad) = {18, 19, 20, …}
```

Una tupla

```
("Ana", 20, "Informática")
```

La tupla pertenece a la relación

```
("Ana", 20, "Informática") ∈ ESTUDIANTE
```

El valor de un atributo en una tupla t

```
t[edad] = 20
```

## Las tres reglas para ser una relación

Si una tabla rompe una sola, ya no es una relación.

### Valores atómicos

Un solo valor por casilla.

Rompe la regla: género = "Rock, Pop"

### Sin filas repetidas

Una relación es un conjunto, y un conjunto no repite elementos.

Rompe la regla: la misma fila dos veces

### Sin orden

Cambiar el orden de las filas no cambia la relación. Una relación sin filas también es válida (el conjunto vacío).

## Las claves, de la más amplia a la más precisa

### Superclave

Columnas cuyos valores nunca se repiten entre dos filas. Puede tener columnas de sobra.

### Clave candidata

Superclave mínima: si le quitas cualquier columna, deja de ser única.

### Clave primaria

La candidata que eliges para identificar las filas. Se subraya y nunca puede ser NULL.

### Clave alternativa

Las candidatas que no elegiste. Se resaltan.

### Atributo primo

Columna que forma parte de alguna clave candidata.

COCHE(estado, matricula, numSerie, marca, modelo, año)\
candidatas: {estado, matricula} y {numSerie} · {numSerie, marca} es superclave pero no clave

Ojo: una clave no se demuestra mirando los datos de hoy. Los datos solo pueden demostrar que algo **no** es clave (si hay dos filas repetidas en esas columnas). Que sea clave depende de las reglas del mundo real.

## Qué puede romper cada operación

| Operación | Puede violar |
| --- | --- |
| Insertar | Cualquier restricción: dominio, clave (valor repetido), integridad de entidad (clave primaria NULL) e integridad referencial. |
| Borrar | Solo la integridad referencial, si otra tabla apuntaba a esa fila. |
| Modificar | Depende de la columna. Si es la clave primaria, es como borrar e insertar, y el nuevo valor no puede repetirse. |

Basado en los apuntes del Tema 2 (T02 - Modelo Relacional) y su guía de repaso GR02.