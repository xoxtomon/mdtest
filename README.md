components:
  responses:
    BadRequest:
      content:
        application/json:
          example:
            error_message: Bad request information
      description: Bad Request
    NotFound:
      content:
        application/json:
          example:
            error_message: Not found information
      description: Not Found
  schemas:
    Anteproyecto:
      properties:
        anteproyectoId:
          format: uuid
          type: string
        autores:
          items:
            $ref: '#/components/schemas/User'
          type: array
          uniqueItems: true
        estado:
          format: int32
          type: integer
        evaluadores:
          items:
            $ref: '#/components/schemas/Evaluador'
          type: array
          uniqueItems: true
        fechaAprobacion:
          format: date
          type: string
        fechaCreacion:
          format: date
          type: string
        fechaEntregaAEvaluador:
          format: date
          type: string
        fechaEntregaDeEvaluador:
          format: date
          type: string
        noRadicacion:
          format: int32
          type: integer
        titulo:
          type: string
      type: object
    AnteproyectoInput:
      properties:
        autores:
          items:
            format: email
            type: string
          type: array
        evaluadores:
          items:
            $ref: '#/components/schemas/EvaluadorInfo'
          type: array
        nroRadicacion:
          format: int32
          type: integer
        titulo:
          type: string
      type: object
    Evaluador:
      properties:
        anteproyectoId:
          format: uuid
          type: string
        director:
          type: boolean
        id:
          format: uuid
          type: string
        userId:
          format: uuid
          type: string
      type: object
    EvaluadorInfo:
      properties:
        director:
          type: boolean
        email:
          type: string
      type: object
    File:
      properties:
        data:
          items:
            format: byte
            type: string
          type: array
        description:
          type: string
        filename:
          type: string
        id:
          format: uuid
          type: string
        idAsociado:
          format: uuid
          type: string
        isAnteproyecto:
          type: boolean
        nroEntrega:
          format: int32
          type: integer
      type: object
    GrantedAuthority:
      properties:
        authority:
          type: string
      type: object
    Login:
      properties:
        email:
          type: string
        password:
          type: string
      type: object
    Proyecto:
      properties:
        anteproyectoId:
          format: uuid
          type: string
        entregaDocs:
          type: boolean
        fechaCreacion:
          format: date
          type: string
        fechaSustentacion:
          format: date
          type: string
        gradoPostulacion:
          format: date
          type: string
        mencionHonor:
          type: boolean
        notaDefinitiva:
          format: float
          type: number
        nroActa:
          format: int32
          type: integer
        proyectoId:
          format: uuid
          type: string
      type: object
    Registration:
      properties:
        email:
          type: string
        lastname:
          type: string
        name:
          type: string
        password:
          type: string
        personalId:
          type: string
      type: object
    Role:
      properties:
        descripcion:
          type: string
        roleId:
          format: int32
          type: integer
      type: object
    User:
      properties:
        accountNonExpired:
          type: boolean
        accountNonLocked:
          type: boolean
        authorities:
          items:
            $ref: '#/components/schemas/GrantedAuthority'
          type: array
        credentialsNonExpired:
          type: boolean
        email:
          type: string
        enabled:
          type: boolean
        lastname:
          type: string
        name:
          type: string
        password:
          type: string
        personalId:
          format: int32
          type: integer
        roles:
          items:
            $ref: '#/components/schemas/Role'
          type: array
          uniqueItems: true
        userId:
          format: uuid
          type: string
      type: object
    inline_response_200:
      properties:
        message:
          example: Usuario creado satisfactoriamente
          type: string
      type: object
    inline_response_200_1:
      properties:
        token:
          type: string
      type: object
    proyecto_body:
      properties:
        anteproyectoId:
          format: uuid
          type: string
      type: object
  securitySchemes:
    bearerAuth:
      bearerFormat: JWT
      scheme: bearer
      type: http
info:
  title: OpenAPI definition
  version: 1.3.0
openapi: 3.0.1
paths:
  /anteproyecto:
    get:
      description: >+

        <b>Este método sirve para traer todos los anteproyectos con sus Autores
        y evaluadores asociados. Este método solo puede se accedido desde una
        credencial administrador.<b>

      operationId: getAllAnteproyectos
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/Anteproyecto'
                type: array
          description: OK
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
    post:
      description: "\n<b>Este método sirve para agergar un nuevo anteproyectos con sus Autores y evaluadores asociados. Este método solo puede se accedido desde una credencial administrador.<b>\n\n###### Body Params\n\n|Name|Type|Required|Description|\r\n|---|---|---|---|\r\n|autores|[string]|false||\r\n|evaluadores|[EvaluadorInfo]|false||\r\n|▹ director|boolean|false||\r\n|▹ email|string|false||\r\n|nroRadicacion|integer(int32)|false||\r\n|titulo|string|false||\n\n"
      operationId: addAnteproyecto
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/AnteproyectoInput'
        required: true
      responses:
        '201':
          content:
            '*/*':
              schema:
                example: Anteproyecto creado satisfactoriamente.
                type: string
          description: Created
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/autor/{idAnteproyecto}':
    get:
      description: >+

        <b>Este método sirve para obtener todos los autores asociados a un
        anteproyecto en particular. Este método solo puede ser accedido desde
        una credencial de administrador.<b>

      operationId: findAutoresOfAnteproyecto
      parameters:
        - description: Id del anteproyecto que se desea consultar sus autores.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/User'
                type: array
                uniqueItems: true
          description: OK
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/autor/{idAutor}/{idAnteproyecto}':
    delete:
      description: >+

        <b>Este método sirve para borrar un autor de un anteproyecto. Este
        método solo puede ser accedido desde una credencial de administrador.<b>

      operationId: deleteAutor
      parameters:
        - description: Id del autor a borrar.
          explode: false
          in: path
          name: idAutor
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Id del anteproyecto de donde se quire eliminar el autor.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '204':
          content:
            '*/*':
              schema:
                example: Autor Borrado exitosamente.
                type: string
          description: No Content
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
    post:
      description: >+

        <b>Este método sirve para agregar un autor a un anteproyecto. Este
        método solo puede ser accedido desde una credencial de administrador.<b>

      operationId: addAutorToAnteproyecto
      parameters:
        - description: Id del autor a agregar.
          explode: false
          in: path
          name: idAutor
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Id del anteproyecto a modificar.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Se agrego al autor satisfactoriamente
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/estado/{estado}/{idAnteproyecto}':
    put:
      description: >+

        <b>Este método se encarga de actualizar el estado de un anteproyecto.
        Solo se puede acceder a este método con credencial de administrador.<b>

      operationId: changeEstado
      parameters:
        - description: Id del anteproyecto a modificar.
          explode: false
          in: path
          name: estado
          required: true
          schema:
            format: int32
            type: integer
          style: simple
        - description: "Nuevo estado a asociar con el anteproyecto.<br>1. Aprobado<br>2. No aprobado<br>\t3. Pendiente (Default)"
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                type: string
          description: OK
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/evaluador/{idAnteproyecto}':
    get:
      description: >+

        <b>Este método sirve para obtener todos los evaluadores asociados a un
        anteproyecto en particular. Este método solo puede ser accedido desde
        una credencial de administrador.<b>

      operationId: findEvaluadorOfAnteproyecto
      parameters:
        - description: Id del anteproyecto que se desea consultar sus evaluadores.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/Evaluador'
                type: array
                uniqueItems: true
          description: OK
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/evaluador/{idEvaluador}/{idAnteproyecto}':
    delete:
      description: >+

        <b>Este método se encarga de borrar un Evaluador de un anteproyecto.
        Este método solo puede se accedido por medio de una credencial de
        administrador.<b>

      operationId: deleteEvaluador
      parameters:
        - description: Id del evaluador a eliminar.
          explode: false
          in: path
          name: idEvaluador
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Id del anteproyecto del cual se debe eliminar el evaluador.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '204':
          content:
            '*/*':
              schema:
                example: El evaluador fue eliminado del anteproyecto.
                type: string
          description: No Content
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
    post:
      description: >+

        <b>Este método sirve para agregar un evaluador a un anteproyecto. Este
        método solo puede ser accedido desde una credencial de administrador.<b>

      operationId: addEvaluadorToAnteproyecto
      parameters:
        - description: Id del evaluador a asociar con el anteproyecto.
          explode: false
          in: path
          name: idEvaluador
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Id del anteproyecto que se desea modificar.
          explode: false
          in: path
          name: idAnteproyecto
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: >-
            Boolean para determianr si este nuevo evaluador es o no el director
            de ese anteproyecto.
          explode: true
          in: query
          name: isDirector
          required: true
          schema:
            type: boolean
          style: form
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Evaluador agregado exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/fecha/creacion/{id}/{fecha}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de creacion de un
        anteproyecto. Solo se puede acceder a este método por medio de una
        credencial de administrador.<b>

      operationId: addFechaCreacion
      parameters:
        - description: Id del anteproyecto a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha a asociar con el anteproyecto.
          explode: false
          in: path
          name: fecha
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                example: Fecha de creacion agregada exitosasmente.
                type: string
          description: OK
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/fecha/devolucion/{id}/{fecha}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de devolución de un
        anteproyecto. Solo es accesible con credencial de administrador.<b>

      operationId: addFechaDevolucion
      parameters:
        - description: Id del anteproyecto a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha a asociar con el anteproyecto.
          explode: false
          in: path
          name: fecha
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                example: Fecha de devolucion modificada correctamente.
                type: string
          description: OK
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/fecha/entrega/{id}/{fecha}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de entrega de un
        anteproyecto. Solo disponible para credenciales con permisos de
        administrador.<b>

      operationId: addFechaEntrega
      parameters:
        - description: Id del anteproyecto a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha a asociar con el anteproyecto.
          explode: false
          in: path
          name: fecha
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                example: Fecha de entrega modificada correctamente.
                type: string
          description: OK
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  '/anteproyecto/{id}':
    delete:
      description: >+

        <b>Este método se encarga de eliminar un anteproyecto y sus relaciones
        e.g las relaciones con usuarios que sean autores o evaluadores.<b>

      operationId: deleteAnteproyecto
      parameters:
        - description: Id del anteproyecto a borrar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '204':
          content:
            '*/*':
              schema:
                example: Anteproyecto borrado exitosamente
                type: string
          description: No Content
        '500':
          content:
            '*/*':
              schema:
                example: Anteproyecto no pudo ser borrado
                type: string
          description: Internal Server Error
      security:
        - bearerAuth: []
      tags:
        - Anteproyecto
  /file:
    get:
      operationId: getFiles
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/File'
                type: array
          description: OK
      tags:
        - File
      description: |+

  '/file/download/{id}':
    get:
      description: >+

        <b>Este método se encarga de traer el documento asociado a una entrega.
        No es necesaria ninguna autenticación para hacer las descargas.

      operationId: downloadFile
      parameters:
        - description: Id de la entrega que se desea descargar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '200':
          content:
            application/pdf:
              schema:
                type: object
          description: OK
      tags:
        - File
  /file/upload:
    post:
      description: >+

        <b>Este método se encarga de hacer una entrega de documento asociado a
        un proyecto o anteproyecto.

      operationId: uploadFile
      parameters:
        - description: Archivo a subir como entrega.
          explode: true
          in: query
          name: file
          required: true
          schema:
            format: binary
            type: string
          style: form
        - description: Id del proyecto o anteproyecto asociado.
          explode: true
          in: query
          name: idAsociado
          required: true
          schema:
            format: uuid
            type: string
          style: form
        - description: Descripción o comentarios de entrega.
          explode: true
          in: query
          name: description
          required: true
          schema:
            type: string
          style: form
        - description: >-
            Valor booleano para saber si es una entrega asociada a un
            anteproyecto o a un proyecto.
          explode: true
          in: query
          name: isAnteproyecto
          required: true
          schema:
            type: boolean
          style: form
        - description: Número de entrega que se va a realizar.
          explode: true
          in: query
          name: nroEntrega
          required: true
          schema:
            format: int32
            type: integer
          style: form
      responses:
        '201':
          content:
            '*/*':
              schema:
                example: Documento subido satisfactoriamente.
                type: string
          description: Created
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
      tags:
        - File
  /login:
    post:
      description: "\n<b>Este método inicia sesión para un usuario ya registrado. Si el usuario no tiene ningún rol asignado o el usuariio no existe un error es lanzado junto a un codigo de respuesta 404<b>\n\n###### Body Params\n\n|Name|Type|Required|Description|\r\n|---|---|---|---|\r\n|email|string|false||\r\n|password|string|false||\n\n"
      operationId: loginUser
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Login'
        required: true
      responses:
        '200':
          content:
            '*/*':
              schema:
                $ref: '#/components/schemas/inline_response_200_1'
          description: OK
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
      tags:
        - Login
  /proyecto:
    post:
      description: "\nEste método se encarga de crear un nuevo proyecto. Los proyectos se deben crear a partir de un anteproyecto ya existente. el unico dato para crear un proyecto es el Id del anteproyecto asociado. Solo se puede acceder a este método con una credencial de administrador.\n\n###### Body Params\n\n|Name|Type|Required|Description|\r\n|---|---|---|---|\r\n|anteproyectoId|string(uuid)|false||\n\n"
      operationId: addProyecto
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/proyecto_body'
        required: true
      responses:
        '201':
          content:
            '*/*':
              schema:
                example: 'Proyecto creado exitosamente. '
                type: string
          description: Created
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/acta/{id}/{acta}':
    put:
      description: >+

        <b>Este método se encarga de modificar el número de acta de un proyecto
        de grado.<b>

      operationId: setFechaSustentacion_2
      parameters:
        - description: Id del proyecto de grado a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nuevo númeor de acta.
          explode: false
          in: path
          name: acta
          required: true
          schema:
            format: int32
            type: integer
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Número de acta cambiado exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  /proyecto/all:
    get:
      description: >+

        <b>Este método se encarga de traer todos los anteproyecto que hay en el
        sistema. Solo se puede accedera este método con una credencial de
        adminstrador.<b>

      operationId: getProyectos
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/Proyecto'
                type: array
          description: OK
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/definitiva/{id}/{nota}':
    put:
      description: >+

        <b>Este método se encarga de modificar la nota final de un proyecto de
        grado.<b>

      operationId: setFechaSustentacion_1
      parameters:
        - description: Id del proyecto de grado a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: 'Nueva nota del proyecto de grado. [0,5]'
          explode: false
          in: path
          name: nota
          required: true
          schema:
            format: float
            type: number
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Nota definitva cambiada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/docs/{id}/{docs}':
    put:
      description: >+

        <b>Este método se encarga de modificar si ya se hizo entrega o no de los
        documentos de un proyecto de grado.<b>

      operationId: setEntregaDocs
      parameters:
        - description: Id del proyecto de grado a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Valor boolean de la modificación.
          explode: false
          in: path
          name: docs
          required: true
          schema:
            type: boolean
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Entrega de documentos cambiada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/fecha-creacion/{id}/{fecha}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de creacion de un
        proyecto de grado.<b>

      operationId: setFechaCreacion
      parameters:
        - description: Id del proyecto a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha.
          explode: false
          in: path
          name: fecha
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Fecha de Creación cambiada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/mencion/{id}/{mencion}':
    put:
      description: >+

        <b>Este método se encarga de modificar si el proyecto de grado es o no
        mención de honor.<b>

      operationId: setMencionHonor
      parameters:
        - description: Id del proyecto ha modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Valor booleano de mención de honor del proyecto.
          explode: false
          in: path
          name: mencion
          required: true
          schema:
            type: boolean
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Mención de Honor modificada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/postulacion/{id}/{fecha}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de postulación de un
        proyecto de grado.<b>

      operationId: setPostulacion
      parameters:
        - description: Id del proyecto a modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha.
          explode: false
          in: path
          name: fecha
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Fecha de postulación cambiada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  '/proyecto/sustentacion/{id}/{date}':
    put:
      description: >+

        <b>Este método se encarga de modificar la fecha de sustentación de un
        proyecto de grado.<b>

      operationId: setFechaSustentacion
      parameters:
        - description: Id del proyecto que se quiere modificar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: Nueva fecha.
          explode: false
          in: path
          name: date
          required: true
          schema:
            format: date-time
            type: string
          style: simple
      responses:
        '202':
          content:
            '*/*':
              schema:
                example: Fecha cambiada exitosamente.
                type: string
          description: Accepted
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
        '404':
          content:
            application/json:
              example:
                error_message: Not found information
          description: Not Found
      security:
        - bearerAuth: []
      tags:
        - Proyecto
  /registration:
    post:
      description: "\n<b>Este método sirve para registrar un nuevo usuario.<b>\n\n###### Body Params\n\n|Name|Type|Required|Description|\r\n|---|---|---|---|\r\n|email|string|false||\r\n|lastname|string|false||\r\n|name|string|false||\r\n|password|string|false||\r\n|personalId|string|false||\n\n"
      operationId: registerUser
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Registration'
        required: true
      responses:
        '200':
          content:
            '*/*':
              schema:
                $ref: '#/components/schemas/inline_response_200'
          description: OK
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
      tags:
        - Registration
  /user/all:
    get:
      description: >+

        <b>Este método se encarga de listar todos los usuarios que existen en el
        sistema, solo es posible acceder a es con credencial de
        administrador.<b>

      operationId: getAllUsers
      responses:
        '200':
          content:
            '*/*':
              schema:
                items:
                  $ref: '#/components/schemas/User'
                type: array
          description: OK
      security:
        - bearerAuth: []
      tags:
        - User
  '/user/role/{id}/{role}':
    get:
      description: >+

        <b>Este método se encarga de adicionar un rol a un usuario. Solo se
        puede acceder a este método con credenciales de administrador.<b>

      operationId: addRole
      parameters:
        - description: Id of the user that will recieve the new role.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
        - description: >-
            Role that will be assigned.
            <br>1:Admin<br>2:Estudiante<br>3:evaluador
          explode: false
          in: path
          name: role
          required: true
          schema:
            format: int32
            type: integer
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                example: ok
                type: string
          description: OK
      security:
        - bearerAuth: []
      tags:
        - User
  '/user/{id}':
    delete:
      description: >+

        <b>Este método se encarga de borrar del sistema un usuario en
        particular. Solo una se puede acceder a este método con credenciales de
        administrador.<b>


      operationId: deleteById
      parameters:
        - description: Id del usuario a eliminar.
          explode: false
          in: path
          name: id
          required: true
          schema:
            format: uuid
            type: string
          style: simple
      responses:
        '200':
          content:
            '*/*':
              schema:
                example: Usuario eliminado exitosamente.
                type: string
          description: OK
        '400':
          content:
            application/json:
              example:
                error_message: Bad request information
          description: Bad Request
      security:
        - bearerAuth: []
      tags:
        - User
servers:
  - description: Production server url (live data)
    url: 'https://tesis-springboot-backend.onrender.com/api/v1'
