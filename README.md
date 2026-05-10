
# **POKEMON** | Proyecto Individual

## **📌 OBJETIVOS**

-  Aprender mejores prácticas.
-  Aprender y practicar el workflow de GIT.

<br />

---


## **⚠️ IMPORTANTE**

Es necesario contar minimamente con la última versión estable de NodeJS y NPM. Asegúrate de contar con ella para poder instalar correctamente las dependecias necesarias para correr el proyecto. Actualmente las versiónes necesarias son:

-  **Node**: 12.18.3 o mayor
-  **NPM**: 6.14.16 o mayor

Para verificar que versión tienes instalada:

```bash
node -v
npm -v
```


---

## **📋 PARA COMENZAR...**

1. Deberás forkear este repositorio para tener una copia del mismo en tu cuenta personal de GitHub.

2. Clona el repositorio en tu computadora para comenzar a trabajar. Este repositorio contiene un **`BoilerPlate`** con la estructura general del proyecto, tanto del servidor como del cliente. El boilerplate cuenta con dos carpetas: **`api`** y **`client`**. En estas carpetas estará el código del back-end y el front-end respectivamente.

3. En la carpeta **`api`** deberás crear un archivo llamado: **`.env`** que tenga la siguiente forma:

   ```env
       DB_USER=usuariodepostgres
       DB_PASSWORD=passwordDePostgres
       DB_HOST=localhost
   ```

4. Reemplazar **`usuariodepostgres`** y **`passwordDePostgres`** con tus propias credenciales para conectarte a postgres. Este archivo va ser ignorado en la subida a github, ya que contiene información sensible (las credenciales).

5. Adicionalmente será necesario que crees, **desde psql (shell o PGAdmin)**, una base de datos llamada **`pokemon`**. Si no realizas este paso de manera manual no podrás avanzar con el proyecto.

<br />

---

## **📖 ENUNCIADO GENERAL**

La idea de este proyecto es construir una aplicación web a partir de la API [**pokeapi**](https://pokeapi.co/) en la que se pueda:

-  Buscar pokemones.
-  Visualizar la información de los pokemones.
-  Filtrarlos.
-  Ordenarlos.
-  Crear nuevos pokemones.

⚠️ Para las funcionalidades de filtrado y ordenamiento NO se puede utilizar los endpoints de la API externa que ya devuelven los resultados filtrados u ordenados.

### **Únicos end-points que se pueden utilizar**

-  [**PokeApi**](https://pokeapi.co/api/v2/pokemon)
-  **Por id**: _"https://pokeapi.co/api/v2/pokemon/{id}"_
-  **Por nombre**: _"https://pokeapi.co/api/v2/pokemon/{name}"_
-  **Por tipo**: _"https://pokeapi.co/api/v2/type"_

<br />

---

## **📁 INSTRUCCIONES**


<br />

### **🖱 BACK-END**

se construyo un servidor utilizando **NodeJS** y **Express**. se conecta con la base de datos mediante **Sequelize**.

El servidor cuenta con las siguientes rutas:

#### **📍 GET | /pokemons**

-  Obtiene un arreglo de objetos, donde cada objeto es un pokemon con su información.

#### **📍 GET | /pokemons/:idPokemon**

-  Esta ruta obtiene el detalle de un pokemon específico. Es decir que devuelve un objeto con la información pedida en el detalle de un pokemon.
-  El pokemon es recibido por parámetro (ID).
-  Incluye los datos del tipo de pokemon al que está asociado.
-  Funciona tanto para los pokemones de la API como para los de la base de datos.

#### **📍 GET | /pokemons/name?="..."**

-  Esta ruta obtiene todos aquellos pokemons que coinciden con el nombre recibido por query.

#### **📍 POST | /pokemons**

-  Esta ruta recibe todos los datos necesarios para crear un pokemon y relacionarlo con sus tipos solicitados.

#### **📍 GET | /types**

-  Obtiene un arreglo con todos los tipos de pokemones y los guarda en la base de datos.


<br />

### **🖱 FRONT-END**

la aplicacion utiliza **React** y **Redux** y contiene las siguientes vistas:

**📍 LANDING PAGE |**  página de inicio o bienvenida: 

-  Botón para ingresar a la **`home page`**.

<br />

**📍 HOME PAGE |** página principal, contiene:

-  SearchBar: un input de búsqueda para encontrar pokemon por nombre.
-  Sector del listado de las cards con los pokemones. 
-  Cuando se le hace click a una Card redirige al detalle de ese pokemon específico.
-  Botones/Opciones para **filtrar** por tipo, y por si su origen es de la API o de la base de datos (creados por nosotros desde el formulario).
-  Botones/Opciones para **ordenar** tanto ascendentemente como descendentemente los pokemones por orden alfabético y por ataque.
-  Paginado: el listado de pokemones se muestra por partes. Tu SPA debe contar con un paginado que muestre un total de 6 pokemones por página.

<br />

**📍 DETAIL PAGE |** Muestra la información específica de un pokemon:

-  Nombre.
-  Imagen.
-  Vida.
-  Ataque.
-  Defensa.
-  Velocidad (si tiene).
-  Altura (si tiene).
-  Peso (si tiene).
-  Tipo.

<br />

**📍 FORM PAGE |**: formulario para crear un nuevo pokemon:

-  Nombre.
-  Imagen.
-  Vida.
-  Ataque.
-  Defensa.
-  Velocidad (si tiene).
-  Altura (si tiene).
-  Peso (si tiene).
-  Posibilidad de seleccionar/agregar varios tipos en simultáneo.
-  Botón para crear el nuevo pokemon.

> [**IMPORANTE**]: el formulario de creación está validado sólo con JavaScript. como por ejemplo: El nombre del pokemon no pueda contener números, o que la defensa no pueda exceder determinado valor, etc.

<br />
