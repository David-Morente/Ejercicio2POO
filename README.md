# Análisis de control de tiempos en torneo universitario de atletismo

## ¿Qué propiedades y métodos tendrá cada clase?

Para el desarrollo del sistema se escogieron dos clases principales: **Atleta** y **Carrera**.

### Clase Atleta

La clase `Atleta` tendrá las siguientes propiedades:

* Nombre.
* Edad.
* Número de participante.
* Estatura.
* Peso.
* Género, utilizando un tipo enumerador.
* Carrera, que permitirá almacenar los registros correspondientes a la clase `Carrera`.

Los métodos de esta clase serán:

1. **Validar edad:** permitirá verificar que el atleta se encuentre dentro del rango de edad establecido para poder participar en el torneo de atletismo.
2. **Validar género:** permitirá identificar el género del atleta para separar las categorías del torneo en masculino y femenino.
3. **Ver lista de intentos:** permitirá consultar todos los tiempos registrados por el atleta.
4. **Ver tiempo:** permitirá consultar el tiempo correspondiente a un intento específico.
5. **Editar intento:** permitirá modificar el tiempo de un intento registrado previamente en caso de que se haya ingresado un dato incorrecto.
6. **Calcular promedio:** tomará los intentos registrados y calculará el tiempo promedio de todos ellos.
7. **Verificar mejor tiempo:** permitirá identificar el mejor tiempo dentro del arreglo de intentos registrados.
8. **Verificar intentos restantes:** permitirá conocer cuántos intentos le quedan disponibles al atleta.
9. **Verificar intentos realizados:** permitirá conocer cuántos intentos ha realizado el atleta.

### Clase Carrera

La clase `Carrera` tendrá dos propiedades principales:

* Tiempo.
* Distancia recorrida en metros.

Los métodos de esta clase serán:

1. **Validar tiempo:** permitirá verificar que el tiempo haya sido registrado correctamente.
2. **Verificar tiempo mayor que cero:** permitirá evitar el registro de tiempos negativos o iguales a cero.
3. **Verificar distancia recorrida por tiempo:** permitirá relacionar la distancia recorrida con el tiempo registrado.

---

## ¿Qué tipo deben tener las propiedades y métodos de cada clase?

### Propiedades de la clase Atleta

| Propiedad          | Tipo de dato |
| ------------------ | ------------ |
| Nombre             | `String`     |
| NumeroParticipante | `int`        |
| Edad               | `int`        |
| Estatura           | `double`     |
| Género             | `Sexo`       |
| Peso               | `double`     |
| Carrera            | `Carrera[]`  |

### Propiedades de la clase Carrera

| Propiedad  | Tipo de dato |
| ---------- | ------------ |
| Tiempo     | `double`     |
| DistanciaM | `double`     |

El tipo de retorno de cada método dependerá de su función. Por ejemplo, los métodos de validación pueden devolver un valor `boolean`, mientras que los métodos que calculan o consultan tiempos pueden devolver un `double`.

---

## ¿Cuál de las propiedades identificadas debe implementarse utilizando un arreglo? ¿Qué tipo de datos almacenará?

La propiedad que debe implementarse utilizando un arreglo es `Carrera`.

Este arreglo será de tipo `Carrera[]` y almacenará objetos de la clase `Carrera`. Cada objeto contendrá información relacionada con un intento realizado por el atleta, específicamente:

* El tiempo registrado.
* La distancia recorrida en metros.

De esta manera, cada posición del arreglo representará un intento realizado.

---

## ¿Cuáles deben ser los modificadores de visibilidad de los miembros en cada clase?

Para mantener un mejor control sobre los datos y aplicar el principio de encapsulamiento, las propiedades de las clases deberían declararse como `private`.

Por ejemplo:

### Clase Atleta

Las propiedades como `nombre`, `numeroParticipante`, `edad`, `estatura`, `peso`, `genero` y `carrera` serán privadas.

Los métodos que necesiten ser utilizados desde otras clases, como consultar intentos, calcular el promedio o verificar el mejor tiempo, serán `public`.

### Clase Carrera

Las propiedades `tiempo` y `distanciaM` serán privadas.

Los métodos encargados de validar y consultar estos valores serán `public`.

---

## ¿Qué parámetros serán requeridos por los métodos en sus clases?

### Clase Atleta

Dependiendo del método, se podrán requerir los siguientes parámetros:

* `edad`, para validar la edad del participante.
* `genero`, para validar la categoría del atleta.
* El arreglo de tipo `Carrera[]`, para trabajar con los intentos registrados.
* La posición o número del intento, cuando sea necesario consultar o editar un intento específico.
* Un nuevo tiempo, cuando se necesite editar un intento.

### Clase Carrera

Los principales parámetros serán:

* `tiempo`, para validar y registrar el tiempo obtenido.
* `distanciaM`, para trabajar con la distancia recorrida.

---

## ¿Cómo se proveerán valores iniciales a los objetos? ¿Qué valores iniciales se les asignarán?

Los valores iniciales de los objetos se proporcionarán mediante la información ingresada por el usuario.

Al crear un objeto de tipo `Atleta`, se solicitarán los datos necesarios, como nombre, número de participante, edad, estatura, género y peso.

El arreglo de carreras o intentos podrá inicializarse vacío, con una cantidad máxima de posiciones previamente establecida. Posteriormente, cada posición será ocupada conforme se registren los intentos del atleta.

Los objetos de tipo `Carrera` recibirán los valores de tiempo y distancia correspondientes a cada intento realizado.

---

## ¿Cómo se determinará cuál es la siguiente posición disponible dentro del arreglo?

La siguiente posición disponible se determinará utilizando un **contador**.

Este contador llevará el registro de la cantidad de intentos almacenados y permitirá identificar la siguiente posición disponible dentro del arreglo.

Cada vez que se registre correctamente un nuevo intento, el contador aumentará en uno.

---

## ¿Cómo se recorrerán únicamente las posiciones del arreglo que contienen tiempos registrados?

Para recorrer únicamente las posiciones que contienen intentos registrados, se utilizará el contador que lleva el control de los intentos realizados.

El recorrido se realizará desde la primera posición del arreglo hasta la posición indicada por el contador, evitando recorrer las posiciones que todavía no han sido utilizadas.

Adicionalmente, se puede verificar que el objeto almacenado en cada posición sea diferente de `null` antes de utilizar sus datos. De esta forma, se evitará procesar posiciones vacías del arreglo.
