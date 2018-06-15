<!-- TOC -->

- [1. Arranque/Apagado de la BD](#1-arranqueapagado-de-la-bd)
    - [1.1. Inicio de Sesión](#11-inicio-de-sesión)
    - [1.2. Cerrar Sesión](#12-cerrar-sesión)
    - [1.3. Acceso a Enterprise Manager](#13-acceso-a-enterprise-manager)
- [2. Introducción a Enterprise Manager](#2-introducción-a-enterprise-manager)
    - [2.1. Otorgar privilegios administrarivos sobre EM a otros usuarios](#21-otorgar-privilegios-administrarivos-sobre-em-a-otros-usuarios)
    - [2.2. Definir períodos de interrupción](#22-definir-períodos-de-interrupción)
    - [2.3. Definición de credenciales preferidas](#23-definición-de-credenciales-preferidas)
- [3. Configuración del entorno de red](#3-configuración-del-entorno-de-red)
    - [3.1. Uso de la página de Administración de EM Manager Net Services](#31-uso-de-la-página-de-administración-de-em-manager-net-services)
    - [3.2. Inicio y detención del proceso de escucha mediante la utilidad de control del listener](#32-inicio-y-detención-del-proceso-de-escucha-mediante-la-utilidad-de-control-del-listener)
    - [3.3. Configuración de nombres "Local Naming" para conectarse a otras BD](#33-configuración-de-nombres-local-naming-para-conectarse-a-otras-bd)
        - [3.3.1. Configuración de nomenclatura local utilizando Net Manager](#331-configuración-de-nomenclatura-local-utilizando-net-manager)
        - [3.3.2. Configuración de nomenclatura local utilizando Enterprise Manager](#332-configuración-de-nomenclatura-local-utilizando-enterprise-manager)
- [4. Manejo de la Instancia Oracle](#4-manejo-de-la-instancia-oracle)
    - [4.1. Cerrar la instancia](#41-cerrar-la-instancia)
    - [4.2. Iniciar la instancia](#42-iniciar-la-instancia)
    - [4.3. Visualización de los parámetros de inicialización](#43-visualización-de-los-parámetros-de-inicialización)
    - [4.4. Administración de los parámetros de memoria](#44-administración-de-los-parámetros-de-memoria)
- [5. Gestión de las Estructuras de Almacenamiento de la Base de Datos](#5-gestión-de-las-estructuras-de-almacenamiento-de-la-base-de-datos)
    - [5.1. Exploración de la estructura de almacenamiento de la base de datos](#51-exploración-de-la-estructura-de-almacenamiento-de-la-base-de-datos)
    - [5.2. Creación de un nuevo Tablespace](#52-creación-de-un-nuevo-tablespace)
    - [5.3. Modificación de un Tablespace](#53-modificación-de-un-tablespace)
    - [5.4. Multiplexación del Redo Log](#54-multiplexación-del-redo-log)
    - [5.5. Gestión de Undo en su base de datos](#55-gestión-de-undo-en-su-base-de-datos)
        - [5.5.1. Uso de la página de Gestión Automática de Deshacer](#551-uso-de-la-página-de-gestión-automática-de-deshacer)
        - [5.5.2. Uso del Asesor de Deshacer](#552-uso-del-asesor-de-deshacer)
- [6. Administración de usuarios y seguridad](#6-administración-de-usuarios-y-seguridad)
    - [6.1. Administración de usuarios de la base de datos](#61-administración-de-usuarios-de-la-base-de-datos)
        - [6.1.1. Crear nuevos usuarios](#611-crear-nuevos-usuarios)
        - [6.1.2. Cambiar atributos de un usuario](#612-cambiar-atributos-de-un-usuario)
        - [6.1.3. Desbloqueo de cuentas y restablecimiento de contraseñas](#613-desbloqueo-de-cuentas-y-restablecimiento-de-contraseñas)
        - [6.1.4. Concesión de privilegios](#614-concesión-de-privilegios)
    - [6.2. Administración de Roles](#62-administración-de-roles)
        - [6.2.1. Creación de Roles](#621-creación-de-roles)
        - [6.2.2. Concesión de Roles](#622-concesión-de-roles)
- [7. Realización de Copia de seguridad y restauración](#7-realización-de-copia-de-seguridad-y-restauración)
- [8. Administración de objetos de un esquema de la base de datos](#8-administración-de-objetos-de-un-esquema-de-la-base-de-datos)
    - [8.1. Acceso a Objetos de Esquema](#81-acceso-a-objetos-de-esquema)
    - [8.2. Gestión de Tablas](#82-gestión-de-tablas)
        - [8.2.1. Visualización de los atributos de una tabla](#821-visualización-de-los-atributos-de-una-tabla)
        - [8.2.2. Ver el contenido de una tabla](#822-ver-el-contenido-de-una-tabla)
        - [8.2.3. Creación de una nueva tabla](#823-creación-de-una-nueva-tabla)
        - [8.2.4. Modificación de una tabla](#824-modificación-de-una-tabla)
        - [8.2.5. Eliminación de una tabla](#825-eliminación-de-una-tabla)
    - [8.3. Gestión de Indices](#83-gestión-de-indices)
        - [8.3.1. Visualización de los atributos de un índice](#831-visualización-de-los-atributos-de-un-índice)
        - [8.3.2. Creación de un nuevo índice](#832-creación-de-un-nuevo-índice)
    - [8.4. Administración de Vistas](#84-administración-de-vistas)
        - [8.4.1. Acceso a Vistas](#841-acceso-a-vistas)
        - [8.4.2. Definición de una nueva vista](#842-definición-de-una-nueva-vista)
    - [8.5. Gestión de Unidades Programa Almacenadas en la BD](#85-gestión-de-unidades-programa-almacenadas-en-la-bd)
    - [8.6. Carga de datos en tablas](#86-carga-de-datos-en-tablas)

<!-- /TOC -->

# 1. Arranque/Apagado de la BD

## 1.1. Inicio de Sesión

1. Iniciamos el listener: `lsnrctl start`.
2. Entramos en la shell de SQL: `sqlplus /nolog`.
3. Conectamos como administrador: `connect sys as sysdba`.
4. Iniciamos la base de datos: `startup`.
5. En otro terminal iniciamos el servicio OEM: `emctl start dbconsole`.

## 1.2. Cerrar Sesión

1. Derribamos el OEM: `emctl stop dbconsole`.
2. Iniciamos la BD: `sqlplus sys as sysdba`.
3. Derribamos la BD: `shutdown immediate`.
4. En otro terminal derribamos el listener: `lsnrctl stop`.

## 1.3. Acceso a Enterprise Manager 

1. Accedemos con el navegador al EM: [https://pclab.localdomain:1158/em](https://pclab.localdomain:1158/em).
2. Introducimos como usuario `sys`, contraseña `ABD3oradba` y conectar como `SYSDBA`.

# 2. Introducción a Enterprise Manager

## 2.1. Otorgar privilegios administrarivos sobre EM a otros usuarios

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Configurar`.
3. Hacemos clic en `Administradores`.
4. Hacemos clic en `Crear` para crear un nuevo usuario de EM.
5. En la página `Crear Administrador: Propiedades` escribimos el `Nombre` y seleccionamos `Superadministrador` en Privilegios de Administrador.
6. Hacemos clic en `Revisar` y a continuación en `Terminar`.

## 2.2. Definir períodos de interrupción

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Configurar`.
3. Hacemos clic en `Interrupciones`.
4. Hacemos clic en `Crear`.
5. Escribimos el `Nombre`de la interrupción un `Comentario` opcional.
6. Seleccionamos un `motivo`.
7. Seleccionamos la `instancia de la base de datos` en el menú desplegable.
8. Seleccionamos la BD y hacemos clic en `Mover` para añadirla a la lista de destinos seleccionados.
9. Hacemos clic en `siguiente`.
10. Seleccionamos la `Hora de comienzo de la interrupción` y si queremos que se `repita`.
11. Hacemos clic en terminar.
12. Se recibe un mensaje de confirmación de que la interrupción ha sido definida.

## 2.3. Definición de credenciales preferidas

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Preferencias`.
3. Hacemos clic en `Credenciales Preferidas`.
4. Hacemos clic en el icono bajo `Definir Credenciales` en la fila `Instancia de Base de Datos`.
5. Introducimos `nombre de usuario` y `contraseña` para las conexiones `normal, SYSDBA y de Host`.
6. Hacemos clic en `Prueba`
7. Se recibe un mensaje de confirmación de que los credenciales se han verificado.
8. Hacemos clic en `Aplicar`.

# 3. Configuración del entorno de red

## 3.1. Uso de la página de Administración de EM Manager Net Services

1. Entramos en el Enterprise Manager.
2. clic en `Listener` en la sección `General` de la página de inicio de la BD.
3. clic en `Administración de Servicios de Red` en la sección de enlaces relacionados en la parte inferior de la página.
4. Aquí podemos administrar los `listener`, `nomenclatura de directorios`, `nomenclatura local`, y `especificación de la ubicación del archivo`.

## 3.2. Inicio y detención del proceso de escucha mediante la utilidad de control del listener

1. Para ver el estado del listener escribimos en una terminal `lsnrctl status`.
2. Para detener el listener escribimos en una terminal `lsnrctl stop listener`.
3. Para iniciar el listener escribimos en una terminal `lsnrctl start listener`.

## 3.3. Configuración de nombres "Local Naming" para conectarse a otras BD

### 3.3.1. Configuración de nomenclatura local utilizando Net Manager

1. Abrimos una terminal y escribimos `netmgr`.
2. Expandimos `Local` y seleccionamos `Nomenclatura de Servicios`.
3. Hacemos clic en `Editar > Crear` o hacemos clic en el `icono más` del lateral.
4. Introducimos un `Nombre de Servicio de Red` y hacemos clic en `Siguiente`.
5. Seleccionamos el `protocolo` que se utilizará para conectarse a la BD. Se puede elegir por defecto `TCP/IP (Protocolo Internet)`. El listener de la BD debe estar configurado para usar el mismo protocolo de red. Hacemos clic en `Siguiente`.
6. Introducimos el `Nombre del Host` de la máquina de la BD y el `Número de puerto`. Hacemos clic en `Siguiente`.
7. Introducimos el `Nombre del Servicio de la BD` y seleccionamos el `Tipo de conexión` ya sea `compartida` o `dedicada`. Si no estamos seguros seleccionamos `Valor por defecto de la BD` y hacemos clic en `Siguiente`.
8. Probamos la conexión utilizando la información que hemos introducido haciendo clic en `Probar`.
9. Por defecto se usa el usuario llamado Scott para realizar la prueba. Si esta cuenta está bloqueada se puede cambiar el nombre de usuario por defecto haciendo clic en `Cambiar conexión`.
10. Utilizamos el usuario `system` y la contraseña `ABD3oradba`, hacemos clic en `Aceptar` y a continuación hacemos clic en `Probar`.
11. Una vez finalizada la prueba hacemos clic en `Cerrar`.
12. Por ultimo podemos observar que el nuevo servicio aparece en la carpeta de servicio de nombres, desde donde podemos modificar la configuración.
13. Guardamos los cambios haciendo clic en `Archivo > Guardar` y a continuación en `Archivo > Salir`.

### 3.3.2. Configuración de nomenclatura local utilizando Enterprise Manager

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Listener` en la sección `General` de la página de inicio de la BD.
3. Hacemos clic en `Administración de Sercvicios de Red` en la sección de enlaces relacionados.
4. Seleccionamos el archivo `Ubicación del archivo de Configuración`. Seleccionamos `Nomenclatura Local` de la lista `Administrar` y hacemos clic en `Ir`.
5. Introducimos el `nombre de usuario` y la `contraseña del host`. Seleccionamos `Guardar como Credencial Preferida` y hacemos clic en `Conectar`.
6. Se muestra la página de `Nomenclatura Local`. Hacer clic en el boton `crear` o seleccionar un nombre de Servicio de Red existente y hacer clic en `Crear como`.
7. Escribimos un nombre en el campo `Nombre de Servicio de Red`. En la sección `Información de Base de Datos` configuramos un soporte de servicio mediante la introducción de un servicio de destino y seleccionamos un tipo de conexión de base de datos. Si el servicio de destino es una BD Oracle 8i seleccionamos el `Nombre de Servicio` y lo introducimos. Si la version es 8.0 seleccionamos `Usar SID` y lo introducimos. A continuación hacemos clic en `Editar` en `Agregar`.
8. Seleccionamos el `Protocolo` deseado e introducimos el `Puerto` y `Host` y hacemos clic en `Aceptar`.
9. Por último, revisamos la configuración y hacemos clic en `Aceptar` y probamos todo utilizando el usuario `dbsnmp`.

# 4. Manejo de la Instancia Oracle

## 4.1. Cerrar la instancia

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Cerrar` en la sección `General` de la página de inicio de la BD.
3. Aparece la página `Iniciar/Cerrar: Especificar Credenciales de Host y Base de datos de Destino` e introducimos las credenciales del host y de la BD y hacemos clic en `Aceptar`.
4. Confirmamos que queremos realizar la operación y hacemos clic en `Refrescar`. Con esto podremos volver a autenticarnos y realizar las copias de seguridad y recuperación de la BD.
5. Una vez finalizado debemos reiniciar la BD antes de poder acceder a los datos.

## 4.2. Iniciar la instancia

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Cerrar` en la sección `General` de la página de inicio de la BD.
3. Aparece la página `Iniciar/Cerrar: Especificar Credenciales de Host y Base de datos de Destino` e introducimos las credenciales del host y de la BD y hacemos clic en `Aceptar`.
4. Confirmamos que queremos realizar la operación y se mostrara la página `Iniciar/Cerrar: Información de Actividad`.
5. Tras iniciarse la instancia podremos volver a autenticarnos.

## 4.3. Visualización de los parámetros de inicialización

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Parámetros de inicialización > Configuración de la Base de Datos`.
3. En la página de `Parámetros de Inicialización` buscamos por el campo que deseemos cualquier parámetro de la BD.

## 4.4. Administración de los parámetros de memoria

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Asesores de Memoria > Configuración de la Base de Datos`.
3. Para volver a la página principal hacemos clic en `Base de datos`.

# 5. Gestión de las Estructuras de Almacenamiento de la Base de Datos

## 5.1. Exploración de la estructura de almacenamiento de la base de datos

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Archivos de Control`. Los archivos de control y su estado se muestran en la página `General`. En la página `Avanzado` podemos ver información adicional acerca de los archivos de control. En la página `Sección de Registros` podemos ver la información almacenada en el archivo de control.
3. Volvemos a la página `Servidor > Instancia de Base de Datos > Tablespaces` para ver la cantidad de espacio asignado a cada tablespace y que parte de él se está utilizando.
4. Si hacemos clic en `Archivos de datos` en la página de `Servidor` accedemos a las propiedades de los archivos de datos.
5. Si hacemos clic en `Grupo de Redo Logs` en la página de `Servidor` accedemos a las propiedades del grupo de Redo Logs.
6. Si hacemos clic en `Archive Logs` en la página de `Almacenamiento` accedemos a las propiedades de los Archive Logs.

## 5.2. Creación de un nuevo Tablespace

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Tablespaces > Crear`. 
3. Introducimos `FSDATA` en el campo `Nombre`. Seleccionamos `Gestionadas Localmente` bajo `Gestión de Extensiones`. Seleccionamos `Permanente` bajo la sección `Tipo`. Seleccionamos `Lectura y Escritura` en la sección del `Estado`. Hacemos clic en `Agregar`.
4. Aparece la página `Agregar Archivo de Datos` e introducimos `fsdata01.dbf` en el campo `Nombre de Archivo`. Aceptamos los valores predeterminados o introducimos nuevos valores. Seleccionamos `Reutilizar Archivo Existente` y ` Ampliar automáticamente el archivo de datos cuando esté lleno (AUTOEXTEND)` y especificamos la cantidad en el campo `Incrementado` con la que se desea ampliar el archivo de datos cada vez que se llena. Hacemos clic en `Continuar` y volverá a la página general de `Crear Tablespaces`.
5. Hacemos clic en `Almacenamiento` y aceptamos todos los valores predeterminados. Hacemos clic en `Aceptar` para crear el tablespace.

## 5.3. Modificación de un Tablespace

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Tablespaces`, seleccionamos `UNDOTBS1` y hacemos clic en `Editar`.
3. Seleccionamos el archivo de datos asociado a dicho tablespace y hacemos clic en `Editar`.
4. Seleccionamos `Ampliar automáticamente el archivo de datos cuando esté lleno (AUTOEXTENDED)` y especificamos `1 MB` para el valor de incremento y `70 MB` para el tamaño máximo del archivo y hacemos clic en `Continuar > Aplicar`.

## 5.4. Multiplexación del Redo Log

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Grupo de Redo Logs`, seleccionamos el grupo 1 y hacemos clic en `Editar`.
3. Hacemos clic en `Agregar` en la sección `Miembros de Redo Logs` y aparecerá la página `Agregar Miembro de Redo Log`.
4. Introducimos `redo01a.log` en el campo `Nombre de Archivo` y hacemos clic en `Continuar` (Es recomendable crear los miembros en discos duros separados para poder tener un miembro del grupo operativo en caso de fallo). Verificamos la entrada y hacemos clic en `Aceptar`.

## 5.5. Gestión de Undo en su base de datos

### 5.5.1. Uso de la página de Gestión Automática de Deshacer
1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Gestión Automática de Deshacer`, aquí podemos ver los valores actuales de deshacer y utilizar el `Asesor de Deshacer` para analizar los requisitos de espacio para el tablespace Undo.
3. Hacemos clic en `Actividad del Sistema` donde podemos ver la actividad del sistema durante un periodo de tiempo especificado. Hacemos clic en `Instancia de Base de Datos` y volvemos a la página `Servidor

### 5.5.2. Uso del Asesor de Deshacer

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Gestión Automática de Deshacer > Asesor de Deshacer`. Hacemos clic en el menú desplegable `Periodo de Tiempo Análisis` y seleccionamos `Último día` y `Ejecutamos el analisis`.
3. Hacemos clic en `Mostrar Gráfico` si queremos ver una representación gráfica.
4. El tamaño del tablespace necesario para cumplir con sus especificaciones se muestra en la sección `Resultados de Análisis`.

# 6. Administración de usuarios y seguridad

## 6.1. Administración de usuarios de la base de datos

### 6.1.1. Crear nuevos usuarios

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Usuarios` y hacemos clic en `Crear`.
3. Introducimos los datos del usuario. para el ejemplo utilizaremos el siguiente:

    ```
    Nombre: FSOWNER
    Contraseña: FSOWNER
    Tablespace por defecto: FSDATA
    Tablespace temporal: TEMP
    Estado: Desbloqueado
    ```
4. Se muestra la página de propiedades de usuarios con un mensaje de actualización que confirma la creación del usuario.

### 6.1.2. Cambiar atributos de un usuario

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Usuarios` seleccionamos el usuario `FSOWNER` y hacemos clic en `Editar`.
3. Hacemos clic en la seccion `Cuotas` y seleccionamos `Ilimitado` para la cuota del tablespace `FSDATA` y hacemos clic en `Aplicar`.
4. Aparece un mensaje con la confirmación de los cambios.

### 6.1.3. Desbloqueo de cuentas y restablecimiento de contraseñas

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Usuarios` seleccionamos el usuario `HR` y hacemos clic en `Desbloquear Usuario` en el menú `Acciones`.
3. Confirmamos que deseamos realizar el desbloqueo.
4. Seleccionamos el usuario `HR` y hacemos clic en `Editar` e introducimos la nueva contraseña y aplicamos los cambios.

### 6.1.4. Concesión de privilegios

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Usuarios` seleccionamos el usuario `FSOWNER` y hacemos clic en `Editar`.
3. Hacemos clic en el enlace `Privilegios del Sistema` y hacemos clic en `Editar Lista`.
4. Se muestra la página `Modificar Privilegios del Sistema`. Seleccionamos `CREATE ANY INDEX` y `CREATE ANY TABLE` y aceptamos. Aplicamos los cambios.

## 6.2. Administración de Roles

### 6.2.1. Creación de Roles

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Roles` y hacemos clic en `Crear`.
3. Aparece la página `Crear Rol` e introducimos `fsclerk` en el campo Nombre.
4. Hacemos clic en `Privilegios del Sistema > Editar Lista` y seleccionamos los roles de `CREATE SESSION` de `Privilegios disponibles del Sistema`.
5. Confirmamos estos cambios.

### 6.2.2. Concesión de Roles

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Servidor > Usuarios`, seleccionamos el usuario `FSOWNER` y hacemos clic en `Editar`.
3. Hacemos clic en `Roles > Editar Lista` seleccionamos el rol `FSCLERK` de los roles disponibles, lo movemos y aplicamos los cambios.

# 7. Realización de Copia de seguridad y restauración


# 8. Administración de objetos de un esquema de la base de datos

## 8.1. Acceso a Objetos de Esquema

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Esquema > Tablas` y hacemos clic en el icono de la `Linterna` para seleccionar un esquema particular.
3. Seleccionamos `HR` y hacemos clic en `Seleccionar`.
4. Introducimos `emp` en el campo `Nombre del Objeto` y hacemos clic en `Ir` para mostrar los objetos que coinciden con los criterios de búsqueda.

## 8.2. Gestión de Tablas

Para la realización de los siguientes pasos hay que completar el punto [8.1. Acceso a Objetos de Esquema](#81-acceso-a-objetos-de-esquema)

### 8.2.1. Visualización de los atributos de una tabla

1. Hacemos clic en el enlace de la tabla `EMPLOYEES`.
2. Aparece la página `Ver Tabla: HR.EMPLOYEES` mostrando los atributos de la tabla, incluyendo columnas, restricciones y opciones de almacenamiento.

### 8.2.2. Ver el contenido de una tabla

1. Hacemos clic en el enlace de la tabla `EMPLOYEES` y seleccionamos `Ver Datos` de la lista `Acciones` y hacemos clic en ir.
2. Aparece la página `Ver Datos para Tabla: HR.EMPLOYEES` mostrando las tuplas de la tabla en la sección `Resultado`.

### 8.2.3. Creación de una nueva tabla

1. Hacemos clic en `Crear` en la página de propiedades de `Tablas`.
2. Aparece la página `Crear Tabla: Organización de Tabla` y seleccionamos `Estándar (Organización en Pilas) y hacemos clic en continuar.
3. Aparece la página `Crear Tabla`. Introducimos como `Nombre: employees`, `Esquema: fsownter` y `Tablespace: fsdata`, agregamos cinco columnas e introducimos los siguientes datos para el ejemplo:

    ```
    Nombre: EMPLOYEE_ID, Tipo de dato: NUMBER, Tamaño: 6
    Nombre: FIRST_NAME, Tipo de dato: VARCHAR2, Tamaño: 20
    Nombre: LAST_NAME, Tipo de dato: VARCHAR2, Tamaño: 25
    Nombre: EMAIL_ADDRESS, Tipo de dato: VARCHAR2, Tamaño: 25
    Nombre: PHONE_NUMBER, Tipo de dato: VARCHAR2, Tamaño: 20
    Nombre: HIRE_DATE, Tipo de Dato: DATE, Tamaño: 
    Nombre: JOB_ID, Tipo de Dato: VARCHAR2, Tamaño: 10    
    Nombre: SALARY, Tipo de Dato: NUMBER, Tamaño: 8
    Nombre: MANAGER_ID, Tipo de Dato: NUMBER, Tamaño: 6
    ```

4. Seleccionamos `PRIMARY` de la lista desplegable `Restricciones` e introducimos `emp_id_pk` en el campo `Nombre`. Seleccionamos `EMPLOYEE_ID` de la lista y hacemos clic en `Continuar`. Aceptamos todo y la tabla se creará con éxito.

### 8.2.4. Modificación de una tabla

1. Seleccionamos la tabla `EMPLOYEES` y hacemos clic en `Editar`.
2. Marcamos `No nulo` el atributo `EMAIL_ADDRESS` y aplicamos los cambios.

### 8.2.5. Eliminación de una tabla

1. Seleccionamos la tabla que deseemos eliminar y hacemos clic en `Suprimir con Opciones`.
2. Seleccionamos `Suprimir la definición de tabla, todos sus datos y los objetos dependientes (Borrar)` y hacemos clic en `Si`. Se muestra un mensaje de confirmación de que la tabla ha sido suprimida.


## 8.3. Gestión de Indices

### 8.3.1. Visualización de los atributos de un índice
1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Esquema > Indices`, introducimos `Esquema: FSOWNER` y hacemos clic en `Ir`.
3. Se muestran los indices creados al definir las claves primarias. Seleccionamos el índice `EMP_ID_PK` definido en la tabla `EMPLOYEES` haciendo clic en el enlace del nombre de índice.
4. Se muestra la página `Ver Indice: FSOWNER.EMP_ID_PK`.


### 8.3.2. Creación de un nuevo índice

1. Entramos en el Enterprise Manager.
2. Hacemos clic en `Esquema > Indices`, introducimos `Esquema: FSOWNER` y hacemos clic en `Ir`.
3. Seleccionamos la tabla deseada y seleccionamos `Crear Indice` de la lista `Acciones` y hacemos clic en `Ir`.
4. Aparece la página `Crear Indice` e introducimos el nombre del indice, el nombre del tablespace y seleccionamos que el tipo de indice sea `Estandard - Arbol B`. Seleccionamos la columna deseada mediante un 1 en la columna `Orden`. Aceptamos `ACS` como el orden de clasificación y hacemos clic en `Aceptar.

## 8.4. Administración de Vistas

### 8.4.1. Acceso a Vistas

1. Seleccionamos `Vistas` de la página `Esquema` y en la página propiedades de vistas, introducimos `Esquema: HR` y hacemos clic en `Ir`.
2. Seleccionamos `EMP_DETAILS_VIEW` y hacemos clic en ver para ver su defición.

### 8.4.2. Definición de una nueva vista


1. Seleccionamos `Vistas` de la página `Esquema` y en la página propiedades de vistas hacemos clic en `Crear`.
2. Introducimos la siguiente información y hacemos clic en `Aceptar`.

    ```
    Nombre: CLERK10_ORDS
    Esquema: FSOWNER
    Texto de la consulta: SELECT order_id, customer_id, order_total FROM orders WHERE sales_clerk_id = 10
    ```

3. Aparece la página de Vistas confirmando la creación de la vista.

## 8.5. Gestión de Unidades Programa Almacenadas en la BD

1. Seleccionamos `Procedimientos` en la página `Esquema` e introducimos `Esquema: HR` y hacemos clic en `Ir`.
2. Seleccionamos el procedimiento `ADD_JOB_HISTORY`. Seleccionamos `Privilegios de Objeto` de la lista `Acciones`, pulsamos `Ir` y a continuación `Agregar`.
3. Seleccionamos `EXECUTE` como el privilegio y `FSOWNER` como el usuario, hacemos clic en `Aceptar` y a continuación en `Aplicar`.

## 8.6. Carga de datos en tablas

1. Hacemos clic en `Movimiento de Datos > Cargar Datos de Archivos de Usuario` y aparece la página `Cargar Datos: Generar o Usar Archivos de Control Existente`. Seleccionamos `Utilizar archivo de control existente` e introducimos también el nombre de usuario y la contraseña para la máquina host y hacemos clic en `Continuar`. Introducimos la ruta completa del archivo de control en el campo que aparece y hacemos clic en `Siguiente`.
2. En el segundo paso proporcionamos la ruta completa y el nombre de la máquina servidor de bases de datos y hacemos clic en siguiente.
3. A continuación marcamos `Ruta de Acceso Convencional` como método de almacenamiento y hacemos clic en `Siguiente`.
4. Se pasará al paso `Cargar Datos: Opciones` y seleccionamos `Generar archivo de log para almacenar información de registro` y hacemos clic en siguiente.
5. Aparece ahora la página `Cargar Datos: Planificar` e introducimos un nombre en el campo `Nombre del trabajo` y una descripción en el campo `Descripción`. Seleccionamos `Inmediatamente` para ejecutar el trabajo ahora y hacemos clic en `Siguiente`.
6. Revisamos los datos introducidos y hacemos clic en `Ejecutar Trabajo` para iniciar la carga. Se muestra un mensaje que el trabajo ha sido correcto.
7. Para confirmar la carga de datos vamos a la página `Tablas` introducimos `FSOWNER` en el campo `Esquema`, hacemos clic en `Ir`, seleccionamos la tabla `customers` y seleccionamos `ver datos` de la lista de `Acciones` y hacemos clic en `Ir`.
8. Aparece la página `Ver datos para la Tabla: FSOWNER.CUSTOMERS` donde se muestran las filas que acaba de cargar. Hacemos clic en Aceptar para volver a la página de propiedades de las tablas.