Sección 1: Descripción.
Esta aplicación Spring Boot combina controladores MVC y REST. 
Utilizo plantillas Thymeleaf para los paneles de administración y para el doctor, mientras que el resto de módulos funcionan mediante API REST. 
La aplicación se conecta a dos bases de datos: MySQL, donde almaceno la información de pacientes, médicos, citas y administradores; y MongoDB, donde gestiono las recetas. 
Todos los controladores pasan las solicitudes a través de una capa de servicio común, que delega en los repositorios correspondientes. 
Para MySQL trabajo con entidades JPA, y para MongoDB utilizo modelos de documentos.

Sección 2: Flujo numerado de datos y control
1.  El usuario realiza una solicitud desde la interfaz web (panel de administración o médico) o mediante una petición a la API REST desde otro módulo.
2.  El controlador correspondiente (MVC o REST) recibe la solicitud. Si es una vista web, se enruta a través de un controlador MVC con Thymeleaf; si es una API, se gestiona desde un controlador REST.
3.  El controlador delega la lógica de negocio a un servicio específico. Esta capa de servicio actúa como intermediaria entre el controlador y los datos.
4.  El servicio determina qué repositorio utilizar, según el tipo de dato: JPA para entidades relacionales (MySQL) o un repositorio MongoDB para documentos (recetas).
5.  El repositorio accede a la base de datos correspondiente:
6.  MySQL para manejar pacientes, doctores, citas y administradores.
7.  MongoDB para guardar y recuperar recetas.
8.  Los datos recuperados o modificados se devuelven al servicio, que puede aplicar reglas adicionales o validaciones antes de continuar.
9.  El servicio devuelve los resultados al controlador, que:
10.  Renderiza una vista Thymeleaf (en el caso de MVC), o devuelve una respuesta JSON (en el caso de una API REST).

