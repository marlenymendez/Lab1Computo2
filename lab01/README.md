# Gestión de Tareas Inteligente - Aplicación con Vue.js


## 1. Situación problemática

En el entorno académico actual, muchos estudiantes enfrentan dificultades para organizar sus actividades debido a la acumulación de tareas, exámenes y responsabilidades personales. Esta falta de organización provoca olvidos frecuentes, incumplimiento de fechas de entrega, estrés académico y bajo rendimiento.

Aunque existen herramientas digitales para la gestión del tiempo, muchas de ellas resultan complejas o poco accesibles, lo que limita su uso en estudiantes que buscan soluciones rápidas y sencillas.

Por ello, surge la necesidad de desarrollar una aplicación web intuitiva que permita gestionar tareas de manera eficiente, facilitando el seguimiento de actividades y priorizando aquellas más urgentes.


## Sectores beneficiados

* Estudiantes de educación media y superior
* Sector educativo en general
* Personas que desean mejorar su organización personal


## 2. Solución propuesta

Se desarrolló una aplicación web utilizando Vue.js que permite gestionar tareas de forma interactiva, dinámica y visualmente clara.

A diferencia de soluciones básicas, esta aplicación incorpora funcionalidades avanzadas como:

* Asignación de fechas de entrega
* Priorización de tareas (alta, media, baja)
* Identificación de tareas urgentes según su fecha
* Búsqueda y filtrado dinámico
* Visualización del progreso del usuario

### Funcionamiento del sistema

El usuario puede ingresar una tarea junto con su fecha límite y nivel de prioridad.
El sistema valida los datos y los almacena en una lista reactiva.

Posteriormente:

* Las tareas se ordenan automáticamente por fecha
* Se clasifican según su urgencia (urgente, próxima o normal)
* Se pueden filtrar por estado (completadas o pendientes)
* Se puede visualizar el progreso total mediante un indicador porcentual

Esto permite al usuario tomar decisiones rápidas sobre qué tareas atender primero.


## 3. Tecnologías utilizadas

* HTML → estructura de la aplicación
* CSS → diseño y estilos visuales
* JavaScript → lógica del sistema
* Vue.js → manejo de la reactividad y la interfaz dinámica


## 4. Funcionalidades implementadas

* Gestión completa de tareas (CRUD)
* Validación de datos en tiempo real
* Filtros dinámicos de tareas
* Sistema de prioridades
* Indicador de progreso
* Interfaz moderna y responsiva

### - Directivas de Vue utilizadas

* `v-model` → enlaza los datos de los inputs
* `v-bind` → permite atributos dinámicos (clases, estilos, etc.)
* `v-for` → renderiza listas dinámicas
* `v-if` → muestra elementos según condiciones

### - Eventos utilizados

* `@click` → interacción con botones
* `@keyup.enter` → agregar tareas con teclado
* `@change` → actualizar estado de tareas


##  5. Preguntas

### - Explique con sus propias palabras qué es Vue.js y cuál es su función dentro de la página web desarrollada.

Vue.js es un framework progresivo de JavaScript que permite desarrollar interfaces de usuario interactivas mediante un sistema reactivo. Esto significa que cualquier cambio en los datos se refleja automáticamente en la interfaz sin necesidad de recargar la página.

En esta aplicación, Vue.js se utiliza para gestionar las tareas, actualizar la lista dinámicamente y mejorar la experiencia del usuario.


### - Describa qué variables reactivas utilizó en su aplicación y cuál es la función de cada una dentro del sistema.

* **nuevaTarea**: almacena el texto ingresado por el usuario
* **fechaEntrega**: guarda la fecha límite de la tarea
* **prioridad**: define el nivel de importancia de la tarea
* **tareas**: contiene la lista de tareas registradas
* **error**: muestra mensajes de validación
* **errorCampo**: identifica qué campo presenta error
* **filtroActual**: controla el tipo de tareas mostradas
* **busqueda**: permite buscar tareas específicas


### - Explique la diferencia entre las siguientes directivas utilizadas en su proyecto: v-bind y v-model

* **v-model** permite la sincronización bidireccional entre el input y los datos del sistema.
* **v-bind** permite enlazar atributos dinámicos como clases, estilos o valores.

En la aplicación, v-bind se utiliza para aplicar estilos según el estado de la tarea.


### - Mencione al menos un ejemplo de evento utilizado dentro de su aplicación.

Se utilizaron eventos como:

* `@click` para agregar, eliminar y editar tareas
* `@keyup.enter` para mejorar la experiencia del usuario
* `@change` para actualizar el estado de completado


### - Explique para qué utilizó la directiva v-for dentro de su aplicación.

Se utilizó para recorrer la lista de tareas y mostrarlas dinámicamente en la interfaz, permitiendo visualizar múltiples elementos de forma automática.


### - Describa en qué situación utilizó v-if y qué problema resuelve dentro de su interfaz.

Se utilizó para mostrar mensajes condicionales, como errores de validación o estados vacíos, mejorando la interacción con el usuario.


### - Explique cómo se realiza la validación de datos en su aplicación y por qué es importante validar la información ingresada por el usuario.

La validación se realiza verificando:

* Que los campos no estén vacíos
* Que la fecha no sea anterior al día actual

Esto es fundamental para evitar datos incorrectos y garantizar el correcto funcionamiento del sistema.

##  6. Ejecución del proyecto

```bash
npm install
npm run dev
```

##  7. Deploy

El proyecto fue publicado en GitHub y desplegado utilizando GitHub Pages, permitiendo su acceso desde cualquier navegador web.


##  Estudiantes

* Marleny Jamileth Martínez Méndez – SMSS018924.
* Mayerlin Yisel Aguilar Cruz – SMSS067424.