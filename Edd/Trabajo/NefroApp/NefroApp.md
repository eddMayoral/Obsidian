
Documentación Aplicación Web NefroApp

# Introducción

El proyecto está realizado en React. Conecta con un backend realizado en Node.js y utiliza MongoDB como base de datos. El proyecto de Node.js (de ahora en adelante, nefro-server) en producción está alojado en Heroku en la cuenta de [jpablo.alejo@nefropolis.com](mailto:jpablo.alejo@nefropolis.com), al igual que los proyectos de Node.js de NIN y NR (como referencia).

Password: _Nefr02022sys

La base de datos de MongoDB está alojada también en la cuenta de [jpablo.alejo@nefropolis.com](mailto:jpablo.alejo@nefropolis.com), pero en esta ocasión la cuenta se ha creado con Google.

El proyecto de Google Cloud (para uso de API Google Drive) se encuentra en el correo de [no-repl@nefropolis.com](mailto:no-repl@nefropolis.com).

  

# Instalación

Repositorio del proyecto de React: [https://github.com/jfloresnfps/NefroApp](https://github.com/jfloresnfps/NefroApp)

Una vez descargado hacemos instalación de paquetes con npm install, lo ejecutamos con npm start. Procedemos con la descarga del proyecto de Node.js.

Repositorio del proyecto de Node.js: [https://github.com/jfloresnfps/nefro-server](https://github.com/jfloresnfps/nefro-server)

Al igual que con el proyecto de React, instalamos los paquetes de Node mediante npm install. Ejecutamos el proyecto con npm run dev.

Para poder visualizar los cambios en la BD, debemos descargar MongoDB Compass: ([https://www.mongodb.com/try/download/compass](https://www.mongodb.com/try/download/compass))

Una vez abierto y configurado (con los valores por defecto) procedemos a introducir la url de la BD, la cual se encuentra en nefro-server en el archivo .env ubicado en la raíz. La variable global se llamada DB_MONGO.

![](https://lh5.googleusercontent.com/FwSCJriP2VQAP5M3sgivLFNjkd8WYjOeozdKQ8e_A3q6IX4T8uAn2ZIqw14VEkvcE_HsmnMRt7tDnjuNgID4aSCg3PTU0c42Ko18XnVuzdrrGj6dCIco04pYRdqT4D5JxsJ2KFL-D3BSPPu15zI-8eE)

Introducida la url, seleccionamos la BD nefro-test, donde podremos visualizar las tablas actuales.

  

# Directorios Proyecto React (frontend)

Directorios de /src

-   /actions
    
-   /components
    
-   /helpers
    
-   /reducers
    
-   /router
    
-   /store
    

  

#### /actions

En este directorio se ubican todos aquellos archivos que se encargan de realizar las peticiones al backend, así como dispatch de eventos de la aplicación.

  

#### /components

Este directorio abarca todos los componentes de la aplicación, módulos y vistas. Se trata de manejar una carpeta por módulo, por lo que cualquier vista que pertenezca a dicho módulo se incluye dentro de su carpeta. Los módulos de administrador, están dentro de la carpeta /admin.

  

#### /helpers

En esta carpeta se ubica productHelper.js, el cual se encarga de realizar las peticiones al backend. request() se utiliza para cualquier tipo de petición. protectedReq() se utiliza para peticiones en módulos de administrador. El backend solicita un header llamado ‘x-token’, donde se envía el token de la sesión activa y se valida. useAxios() se utiliza para subida de imágenes.

  

#### /reducers

Reducers de Redux. Se trata de manejar un reducer por módulo de la aplicación, pero en algunos casos el reducer puede compartirse en más de un módulo. Los reducers de manejar cambios en las variables de estado de la aplicación. A través de un switch se conoce qué acción se ha disparado y en base a esto se realizan las operaciones correspondientes. mainReducer.js contiene todos los reducers que se están utilizando en la aplicación.

  

#### /router

Los siguientes archivos se encargan de ‘vigilar’ las rutas, para limitar el acceso a ciertas rutas:

-   PublicRoute.js
    
-   PrivateRoute.js
    
-   ProtectedRoute.js
    

Los siguientes archivos contienen rutas de la aplicación:

-   AdminRoutes.js
    
-   ShopRoute.js
    
-   UserRoute.js
    

AppRoute.js contiene todas las rutas de la aplicación, y el archivo el cual restringe el acceso. Por ejemplo, las rutas de administrador AdminRoutes.js son protegidas mediante ProtectedRoute.js.

  

#### /store

El único archivo de este directorio se encarga de integrar el funcionamiento de Redux. Más adelante se explica dónde se utiliza este archivo.

#### /types

El archivo de este directorio contiene todas las acciones de Redux. Los reducers utilizan un switch donde se evalúa un string que indica la acción a realizar. Dicho string debe coincidir con una que se encuentre declarada en el archivo types.js. También se aprovecha este archivo para describir brevemente la acción que se realiza. Mediante el complemento Redux DevTools de Google Chrome podemos apreciar la acción ejecutada y la descripción durante el desarrollo.

Con todo esto se evitan errores de escritura y crasheos.

  

En el directorio de la aplicación se encuentran los archivos .env.development y .env.production. Cada una cuenta con la url del proyecto de nefro-server, en desarrollo y producción respectivamente.

  

# Directorios Proyecto Node.js (backend)

-   /controllers
    
-   /db
    
-   /helpers
    
-   /middlewares
    
-   /models
    
-   /private
    
-   /public
    
-   /routes
    
-   /test
    

  

#### /controllers

Aquí se encuentran todas las operaciones que se realizan mediante las peticiones del frontend. Inserción, eliminación, actualización, entre otras operaciones. Las funciones se encuentran en un trycatch, cualquier error que suceda se enviará al frontend y de ese lado se procesa según convenga.

  

#### /db

Aquí se encuentra un archivo que se encarga de inicializar la base de datos en MongoDB. Para facilitar el manejo de MongoDB, Node.js cuenta con una librería, la cual es Mongoose ([https://www.npmjs.com/package/mongoose](https://www.npmjs.com/package/mongoose)).

  

#### /helpers

Aquí se ubica un archivo que se encarga de generar los tokens y almacenarlos en JSON Web Tokens ([https://jwt.io/](https://jwt.io/)). En el token almacenamos por nuestra parte, únicamente el ID del usuario que está iniciando, lo que nos permite recuperar datos de dicho usuario según convenga. Para estas y otras operaciones, se instaló la librería jsonwebtoken ([https://www.npmjs.com/package/jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)).

  

#### /middlewares

token-validator.js se encarga de validar si el token enviado sigue válido, de ser así se procede con las operaciones debidas. Caso contrario se retorna que el token ya no es válido.

validator.js retorna un objeto indicando que la petición no ha aprobado la validación, lo que indica que es posible que falten valores en el objeto, o que no cumplan con los requisitos. Por ejemplo, que la longitud de un correo sobrepase los 100 caracteres.

Para la realización de validación, se instaló express-validator ([https://www.npmjs.com/package/express-validator](https://www.npmjs.com/package/express-validator)), la cual nos ayuda a validar el objeto que se recibe en la petición.

  

#### /models

Aquí se encuentran todos los modelos que se utilizan para realizar operaciones en los documentos de MongoDB. Esto es posible gracias a la librería de Mongoose, mencionada anteriormente.

  

#### /private

Contiene un archivo .gitignore, simplemente para que tanto Github como Heroku suban el directorio. Sirve como carpeta temporal para la subida de imágenes. Una vez las imágenes son subidas a Google Drive, las imágenes se eliminan de este directorio.

#### /public

Muestra una página cualquiera por si algún usuario intenta acceder a la url del servidor (nefro-server).

  

#### /routes

Aquí llegan las peticiones según la url de donde provengan, para facilitar la lectura de las mismas. Por ejemplo, si la petición viene a /api/user/…, se procesa en el archivo user.js, si la petición viene a /api/product/…, se procesa en el archivo product.js. De todas maneras, esto puede apreciarse en index.js, que se explicará más adelante.

  

#### /test

Todos los archivos contienen código de prueba, excepto test.js. En este archivo maneja la subida de imágenes.

  

En la raíz del proyecto, está .env y index.js.

.env vienen variables globales para el proyecto.

-   PORT: Puerto en el que se ejecuta la aplicación.
    
-   DB_MONGO: url de conexión de la base de datos de MongoDB.
    
-   SECRET_SEED: semilla para la creación de JSON Web Tokens.
    
-   CLIENT_ID: ID de cliente de Google Drive
    
-   CLIENT_SECRET: llave secreta de cliente de Google Drive
    
-   REFRESH_TOKEN: token de actualización de Google Drive
    
-   EMAIL: correo electrónico por defecto.
    
-   APP_KEY: llave para el envío de correos electrónicos desde [no-reply@nefropolis.com](mailto:no-reply@nefropolis.com)
    

index.js contiene la declaración de múltiples librerías que se utilizan en el proyecto.

  

Se inicializa tanto la aplicación como la base de datos. Aquí se puede observar los endpoints y qué archivo manipula las operaciones.

  

# Base de datos

A grandes rasgos, en el diagrama actual se indica con marco aquellos documentos que no se han implementado en MongoDB, por lo que solamente es la idea de cómo será el documento (abierto a cambios). Dentro de las entidades existen propiedades de color azul, que son cambios que se desean hacer a documentos ya existentes en MongoDB. Cada documento lleva el título en singular (Account, por ejemplo), sin embargo, al momento de la creación, MongoDB utiliza el plural para sus documentos.

  

MongoDB no maneja límite de caracteres, solo tipos de dato ([https://www.tutorialspoint.com/mongodb/mongodb_datatype.htm](https://www.tutorialspoint.com/mongodb/mongodb_datatype.htm)), por lo que los caracteres que se indican en las entidades (String(100), Number(8), por ejemplo), son las validaciones de máximo caracteres permitidas que se realiza tanto en front como en back.

  

#### accounts

Esta tabla es utilizada para cuentas de usuarios y administradores sin distinción. La manera de identificar a un usuario administrador es mediante la propiedad de privileges (privilegios). Si cuenta con esta propiedad significa que el usuario es administrador. Esta propiedad objeto tiene otras propiedades que le permitirá acceder o realizar operaciones en módulos de administrador.

  

#### address

Direcciones de envío del usuario.

  

#### billings

Direcciones de facturación del usuario.

  

#### coupons

Cupones de descuento. type es manejado para el tipo de cupón (descuento por porcentaje / descuento neto). quantity es la cantidad disponible de cupones, la cual va disminuyendo conforme se concreten ventas. available indica si el cupón está activo o no.

  

#### contacts

Respaldo de los formularios de quejas y sugerencias enviados al correo electrónico. Se desea renombrar a contact_forms.

  

#### postulations

Respaldo de los formularios de bolsa de trabajo enviados al correo electrónico. Se desea renombrar a postulation_forms.

#### branches

Sucursales de Nefrópolis.

  

#### distributors

Distribuidores de Nefrópolis.

  

#### promotions

Podría ser útil para las promociones de productos en la tienda. promotion_type puede ser:

-   descuento a un producto en específico
    
-   descuento a partir de cierto subtotal
    
-   descuento en el producto cuando hay 'x' a partir cantidad en carrito
    

Aún debe definirse...

  

#### products

Productos de Nefrópolis. info contiene información adicional del producto (y variantes). category es un arreglo de todas las categorías a las que pertenece el producto. category tiene su propio documento en MongoDB, por simplicidad, se añaden los valores en el producto (se evita tener que hacer doble consulta) dentro de un arreglo de categorías. featured es una propiedad que se piensa utilizar para simplificar la sección de productos destacados. Si featured es verdadero, el producto es mostrado en la sección productos destacados. folderId es el ID de Google Drive donde se almacenan las imágenes de los productos. prod_variants es un arreglo de los ID’s (ObjectId) de las variantes. reviews son los comentarios de usuarios en los productos. reviews también contiene una propiedad folderId donde se almacenan las imágenes del comentario, y una propiedad images, la cual es un arreglo con los ID’s de las imágenes en Google Drive.

  

#### variants

Variantes de los productos de Nefrópolis. stock es la cantidad disponible de producto. Al igual que category en products, flavor y capacity almacenan tanto _id como el valor. pkg es cantidad de productos en paquete. available indica si el producto se mostrará en la tienda. images contiene el arreglos de ID’s de las imágenes en Google Drive.

  

#### categories

Categorías de los productos de Nefrópolis.

  

#### capacities

Capacidades de los productos de Nefrópolis.

  

#### flavors

Sabores de los productos de Nefrópolis.

  

#### order

Contiene los pedidos de Nefrópolis. En este documento se incluye información de la venta, subtotal, total, datos del cupón (si aplica), datos del cliente, datos de facturación (si aplica), método de pago, arreglos con los productos adquiridos, estado del envío, fecha de venta y notas adicionales.

  

# Librerías NefroApp

  

#### React Router DOM

[https://www.npmjs.com/package/react-router-dom](https://www.npmjs.com/package/react-router-dom). Navegación dinámica en aplicación web.

  

#### React Redux

[https://www.npmjs.com/package/react-redux](https://www.npmjs.com/package/react-redux). Librería de Redux para React.

  

#### React Thunk

[https://www.npmjs.com/package/redux-thunk](https://www.npmjs.com/package/redux-thunk). Permite trabajar con lógica asíncrona para interactuar con el Store. Va de la mano con React Redux.

  

sweetalert2

[https://www.npmjs.com/package/sweetalert2](https://www.npmjs.com/package/sweetalert2)

[https://sweetalert2.github.io/](https://sweetalert2.github.io/)

Popup para mostrar mensajes al usuario.

  

axios

[https://www.npmjs.com/package/axios](https://www.npmjs.com/package/axios). Permite hacer peticiones HTTP. Para lo que se utiliza específicamente en el proyecto es para enviar imágenes al backend para su subida a Google Drive.

  

# Librerías nefro-server

  

#### nodemon

[https://www.npmjs.com/package/nodemon](https://www.npmjs.com/package/nodemon). nodemon reinicia la aplicación de node cuando hacemos cambios en el proyecto, lo que facilita el desarrollo. Es necesario instalar como dependencia de desarrollo: npm install -D nodemon.

  

#### Mongoose

[https://www.npmjs.com/package/mongoose](https://www.npmjs.com/package/mongoose)

[https://mongoosejs.com/](https://mongoosejs.com/)

Permite crear modelos de documentos y realizar operaciones en MongoDB.

  

#### dotenv

[https://www.npmjs.com/package/dotenv](https://www.npmjs.com/package/dotenv)

Permite utilizar variables de entorno en el proyecto.

  

#### CORS

[https://www.npmjs.com/package/cors](https://www.npmjs.com/package/cors). Configura CORS para peticiones.

  

#### Express

[https://www.npmjs.com/package/express](https://www.npmjs.com/package/express). Se encarga de darle estructura al proyecto, proporcionando funcionalidades como el enrutamiento.

  

#### Express Validator

[https://www.npmjs.com/package/express-validator](https://www.npmjs.com/package/express-validator). Middleware para validar los objetos de las peticiones recibidas antes de proceder con las operaciones.

  

#### Multer

[https://www.npmjs.com/package/multer](https://www.npmjs.com/package/multer). Middleware para manejar multipart/form-data. De esta forma podemos enviar y subir archivos al backend. Se utiliza para recibir y almacenar las imágenes en el servidor (de manera temporal). Enseguida se suben a Google Drive y las imágenes se eliminan del servidor.

  

#### bcrypt.js

[https://www.npmjs.com/package/bcryptjs](https://www.npmjs.com/package/bcryptjs). Encriptación de contraseñas.

  

#### jsonwebtoken

[https://www.npmjs.com/package/jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)

[https://jwt.io/](https://jwt.io/)

Permite compartir información segura en forma de un objeto JSON entre dos medios. Se utiliza para guardar el ID del usuario que inicia sesión (creación de sesión) y establecer fecha de expiración. Se retorna el token generado por medio de esta librería al frontend.

  

#### googleapis

[https://www.npmjs.com/package/googleapis](https://www.npmjs.com/package/googleapis). Permite utilizar las API’s de Google. En este proyecto se utiliza la API de Google Drive.

  

#### async

[https://www.npmjs.com/package/async](https://www.npmjs.com/package/async). Instalado cuando se trabajaba con Google Drive. No se utiliza por el momento.

  

# NefroApp

A partir de este punto, se comenzará a explicar más detalladamente el desarrollo del proyecto, específicamente, sobre sus módulos. Se explicará más que nada la parte del frontend, dado que una vez sabiendo la operación que está sucediendo de este lado y qué variables se están utilizando, es muy sencillo deducir las operaciones del backend, además de que cada función se encuentra comentada.

  

## Redux

Recapitulando, los archivos que permiten la integración de Redux son ./store/store.js, ./types/types.js (que bien podría ser opcional) y los reducers en ./reducers. El dispatch de acciones se realizan en componentes, pero mayormente dentro de ./actions. Para integrar debidamente el proyecto podemos observar en la raíz, en App.js, que <AppRoute /> está dentro de un <Provider></Provider>, este Provider incluye el store.js, que a su vez inicializa el mainReducer.js, el cual contiene todos los reducers utilizados en el proyecto.

Esto es lo único que debemos hacer para integrar Redux en el proyecto, además de, por supuesto, la instalación de React Redux y Redux Thunk.

  

## Rutas

El proyecto se encuentra dividido en 4 rutas. Se tiene un archivo principal de rutas llamado AppRoute.js. Este archivo contiene las rutas de toda la aplicación web, donde a su vez, se encuentran divididas en subrutas en los archivos AdminRoutes.js, ShopRoutes.js, UserRoutes.js y Start.js. Dichas rutas son vigiladas” por 3 archivos, los cuales son PublicRoute.js, PrivateRoute.js, ProtectedRoute.js, dentro de la carpeta ./router. Más adelante se explica la funcionalidad de estos 3 archivos.

Para el manejo del estado de la aplicación se utiliza Redux (se ha visto Redux en acción, trabajando de manera precisa y elegante con el estado de la aplicación, por lo que se decidió implementar en el proyecto).

Los usuarios deben haber iniciado sesión y tener privilegios para acceder a la ruta de /nefro-admin, la validación se hace en ./router/ProtectedRoute.js. Para que los usuarios puedan acceder a la ruta de /mi-cuenta, deben haber iniciado sesión, la validación la lleva a cabo en ./router/PrivateRoute.js. Los usuarios (sean administradores o no) no pueden acceder a la ruta /inicio si cuentan con una sesión activa, validación en el archivo ./router/PublicRoute.js. Cualquier visitante puede acceder al resto de rutas (/*), no es necesario tener cuenta ni haber iniciado sesión.

## Login/Sign Up

En el registro de usuarios no se utiliza por el momento ningún recaptcha. El usuario crea su cuenta, se guarda en la base de datos y se le activa una sesión. La sesión expira en 3 horas.

En el inicio de sesión, se verifica que el usuario exista y la contraseña coincida. Sea el caso que fuere, no se le hace saber a la persona tratando de acceder si el usuario existe/está ingresando una contraseña incorrecta, simplemente se le notifica que usuario y contraseña no coinciden.

Para el manejo de sesiones utilizamos JSON Web Tokens ([https://jwt.io/](https://jwt.io/)). El cual se encarga de manejar la autenticación mediante un objeto JSON. Al registrarse/iniciar sesión el usuario se genera un token de lado del backend mediante la función tokenGen(), ubicada en el archivo ./helpers/makeJWT.js. Dicho token almacena el ID del usuario, lo que nos permite recuperar datos del usuario si el token sigue válido, en lugar de guardar los datos del usuario (tales como el correo electrónico y nombre de usuario) en el token, lo cual no es recomendado. La sesión se renueva automáticamente cada vez que se recarga la aplicación web (no confundir con navegar entre páginas) y cada que se realiza un dispatch. En ./router/AppRoute.js se lleva a cabo la comprobación de la sesión y la renovación en caso de dispatch. Mientras se recibe la respuesta, se muestra un “Espere…”. Una vez recibimos respuesta, podemos mostrar el contenido al usuario. De no hacer esto de esta manera, no podremos acceder a las rutas "vigiladas", ya que debemos esperar a que termine la petición. Próximamente se buscará una manera más eficiente de llevar a cabo este proceso.

  

El token generado se envía al frontend y se guarda en el localStorage. Cada vez que se hace la renovación se envía dicho token y se retorna un token renovado. Este proceso se realiza en la función renew(), que a su vez utiliza requestProtected(). Esta última función se utiliza para realizar todas las peticiones en módulos de administradores. Para este tipo de peticiones se envía un header de tipo "...". El backend verifica que el header se incluya en la petición, y de ser así, procede con las operaciones.

  

Además de retornar el token, también se retornan los datos del usuario, los cuales se almacenan en el estado de la aplicación gracias a Redux, a través del archivo userReducer.js. Los datos que se almacenan son correo electrónico, nombre de usuario y privilegios (en caso de ser administrador).

  

[admin@nefropolis.com](mailto:admin@nefropolis.com)

99990

## Módulos de productos

  

### Lista productos

Este módulo muestra la lista de productos registrados. Al seleccionar uno se muestran las variantes de dicho producto. Esta es la lógica que se está siguiendo para el registro de productos. Un producto de la tienda puede ser producto único, sin embargo, se registra el producto y una variante (de esta manera se toma como producto único).

Al cargar el módulo se carga la lista de productos, las categorías y los sabores. Las categorías y los sabores se cargan en caso de que se necesite hacer alguna edición a uno de los productos.

Desde este módulo se puede editar y eliminar variantes, editar y eliminar el producto. En caso de eliminar una variante, su carpeta con imágenes son eliminadas de Google Drive. En caso de eliminar un producto, variantes y carpetas de imágenes de variantes son eliminadas de Google Drive.

Cuando una de estas acciones se completa, se ejecuta otra acción para actualizar las variables de entorno en Redux. Cuando la respuesta del backend no es exitosa, se muestra un mensaje con el incidente.

  

### Nuevo producto

En este módulo podemos registrar un producto y su variantes(s). A continuación se muestran las validaciones que se realizan en los campos.

  

#### Validaciones en campos de producto

Título: minLength(2), maxLength(100)

url: minLength(2), maxLength(100)

Arreglo de categorías: minLength(1), categorías a las que pertenece el producto

Información adicional: minLength(2), maxLength(1000)

Destacado: indiferente

Arreglo de variantes: minLength(1)

  

#### Validaciones en campos de variante

Precio: minLength(1), maxLength(10)

SKU: minLength(3), maxLength(60)

Descripción: minLength(3), maxLength(100)

Stock: minLength(1), maxLength(5)

Sabor: no requerido, sabor del producto, debe haberse registrado previamente

Capacidad: no requerido, capacidad del producto, debe haberse registrado previamente

Piezas de paquete (pkg): no requerido

Disponibilidad: indiferente, mostrar en sección Productos destacados

Arreglo de imágenes: minLength(1), maxLength(6), mínimo una imagen por variante, máximo 6 imágenes

  

Cualquier duda respecto a estos campos puede resolverse accediendo a la sección de products y variants dentro de Base de datos.

  

Existen múltiples propiedades para diferenciar a la variante. Estas propiedades son; sabor, capacidad, piezas (del paquete). No es obligatorio seleccionar una de estas, ni combinar dos de estas para el registro de la variante.

Primero se registra el producto y las variantes, se retorna el ID de la carpeta de imágenes de Google Drive y el arreglo de los ID's de las variantes. Hecho esto podemos proceder con la subida de imágenes. Para la subida de imágenes, en uploadImages() dentro de product.js, enviamos el ID de la carpeta de Google Drive que previamente retornó el backend (carpeta del producto), así como el ID de la variante. Se hace una petición por variante para almacenar sus imágenes. Si el número de respuestas exitosas es igual al número de peticiones, entonces todo el proceso ha resultado exitoso y se redirige al administrador a la lista de productos.

#### Imágenes de productos

Las imágenes son almacenadas en Google Drive, en la cuenta de [no-reply@nefropolis.com](mailto:no-reply@nefropolis.com), dentro de la carpeta NefroApp/Productos. Dicha carpeta fue creada manualmente, y el ID se puede recuperar en la url.

![](https://lh6.googleusercontent.com/_BJopkwpehjjExp7uw2o4aQ58qqzNteXSZGXOpAWspD5Q5LsW77m0Aoi-nkvMLL71eo6CmcpQIyQrSuDy-B1HYkMsbPkaAwGIMbybHHELrBAMRZx2oTaZIzU1ogVD0SowSwG4ATvKUeKwpPheT1h-1g)

En la propiedad prod_variants de products se almacenan los ID’s de las variantes, mientras que en la propiedad images de variants se almacenan los ID’s de las imágenes en Google Drive de la variante. De esta manera, para mostrar la imagen solo es necesario concatenar el ID en el src de la imagen, de esta manera: [https://drive.google.com/uc?export=view&id=${ID](https://drive.google.com/uc?export=view&id=$%7BID)}

De lado del backend, utilizamos Multer para subir las imágenes. Se vieron otras dos alternativas pero Multer estaba mejor documentado, además su implementación no es nada complicada. En ./routes/product.js podemos observar un ejemplo de cómo lo declaramos para empezar a utilizarlo:

const multer = require('multer');

const storage = multer.diskStorage({

    destination: function (req, file, cb) {

      cb(null, 'public');

    },

    filename: function (req, file, cb) {

      cb(null, file.originalname);

    }

});

// subir imágenes de variante existente

router.post('/variant/images-append', upload.any(), variantAppendImages);

  

Aquí indicamos que la carpeta pública va a ser el lugar donde se van a almacenar las imágenes, en filename indicamos que se guardarán con su nombre original.

En la ruta podemos observar que se implementa multer como middleware mediante upload.any(). Tal como viene en su documentación, existen múltiples formas de recoger la imagen o imágenes que vienen en la petición, como upload.single() o upload.array(), sin embargo, la única forma que permitió recoger las variables que vienen en la petición fue mediante upload.any(). De esta forma sabemos el ID de la variable y la carpeta padre en Google Drive. Para cada variante, se crea una nueva carpeta con el ID como nombre.

  

### Cupón

En este módulo podemos visualizar la lista de cupones, registrar un cupón nuevo, editar o eliminar cupones existentes.

  

#### Validaciones de cupón

Nombre: minLength(3), maxLength(60)

Cantidad: minLength(1), maxLength(5)

Tipo de cupón: percentage, net_value (descuento por porcentaje, descuento neto, fijos mediante un select)

Descuento:

Existen dos tipos de descuento para el cupón. Descuento neto es una cantidad fija de descuento (en pesos mexicanos). Descuento por porcentaje, como su nombre lo indica, aplica un descuento según el porcentaje registrado. Dicho esto, la validación depende según el tipo de descuento.

Descuento por porcentaje: Valor entre 5% y 100%

Descuento neto: minLength(2), maxLength(10)

Disponible: indiferente

  

## Mensajes

Dentro de ./actions, en swal_msg.js se encuentran todos los tipos de mensajes que se utilizan en la aplicación. Estos mensajes son mayormente utilizados por otros archivos en ./actions, pero también hay casos (pocos) en los que estos mensajes se utilizan en componentes. Estos mensajes funcionan gracias a la librería sweetalert2.

  

## UI

Existen casos en los que hay que hacer actualizaciones de un componente al completar una acción, fuera de ese componente, por ejemplo, abrir y cerrar un modal. Para esto también empleamos Redux. Cuando un registro de un cupón es exitoso (por mencionar un ejemplo), hay que cerrar el modal automáticamente y regresar a los valores por defecto de los campos del modal. Para limpiar los campos la función estará dentro de ./actions/coupon.js, pues es el módulo que le corresponde, pero para manejar el estado de un componente UI (cerrar el modal), la acción estará dentro de ./actions/ui.js, o al menos es un estándar que se ha estado siguiendo, pero no desde el comienzo del desarrollo del proyecto.

  

## Google Drive

Para configurar Google Cloud y empezar a utilizar la API de Google Drive, se siguieron los siguientes pasos:

[https://youtu.be/1y0-IfRW114](https://youtu.be/1y0-IfRW114)

Necesitaremos estos dos enlaces.

[https://console.cloud.google.com/getting-started](https://console.cloud.google.com/getting-started)

[https://developers.google.com/oauthplayground](https://developers.google.com/oauthplayground/)

Si queremos empezar a utilizar la API de Google Drive, necesitamos inicializar oauth2Client en cada controlador donde se vaya a utilizar. Las siguientes líneas son las necesarias para cada controlador:

const { google } = require('googleapis');

const REDIRECT_URI = '';

const oauth2Client = new google.auth.OAuth2(

    process.env.CLIENT_ID,

    process.env.CLIENT_SECRET,

    REDIRECT_URI

);

oauth2Client.setCredentials({ refresh_token: process.env.REFRESH_TOKEN });

const drive = google.drive({

  version: 'v3',

  auth: oauth2Client

});

  

Como se puede apreciar, se están utilizando variables de entorno. CLIENT_ID, CLIENT_SECRET y REFRESH_TOKEN son las variables que nos interesan.

**