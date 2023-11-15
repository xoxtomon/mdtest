{
  "openapi": "3.0.1",
  "info": {
    "title": "OpenAPI definition",
    "version": "1.3.0"
  },
  "servers": [
    {
      "url": "https://tesis-springboot-backend.onrender.com/api/v1",
      "description": "Production server url (live data)"
    }
  ],
  "paths": {
    "/registration": {
      "post": {
        "tags": [
          "Registration"
        ],
        "description": "<b>Este método sirve para registrar un nuevo usuario.<b>",
        "operationId": "registerUser",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Registration"
              }
            }
          },
          "required": true
        },
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "$ref": "#/components/schemas/inline_response_200"
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          }
        }
      }
    },
    "/login": {
      "post": {
        "tags": [
          "Login"
        ],
        "description": "<b>Este método inicia sesión para un usuario ya registrado. Si el usuario no tiene ningún rol asignado o el usuariio no existe un error es lanzado junto a un codigo de respuesta 404<b>",
        "operationId": "loginUser",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Login"
              }
            }
          },
          "required": true
        },
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "$ref": "#/components/schemas/inline_response_200_1"
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          }
        }
      }
    },
    "/user/all": {
      "get": {
        "tags": [
          "User"
        ],
        "description": "<b>Este método se encarga de listar todos los usuarios que existen en el sistema, solo es posible acceder a es con credencial de administrador.<b>",
        "operationId": "getAllUsers",
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/User"
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/user/role/{id}/{role}": {
      "get": {
        "tags": [
          "User"
        ],
        "description": "<b>Este método se encarga de adicionar un rol a un usuario. Solo se puede acceder a este método con credenciales de administrador.<b>",
        "operationId": "addRole",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id of the user that will recieve the new role.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "role",
            "in": "path",
            "description": "Role that will be assigned. <br>1:Admin<br>2:Estudiante<br>3:evaluador",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "integer",
              "format": "int32"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "ok"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/user/{id}": {
      "delete": {
        "tags": [
          "User"
        ],
        "description": "<b>Este método se encarga de borrar del sistema un usuario en particular. Solo una se puede acceder a este método con credenciales de administrador.<b>",
        "operationId": "deleteById",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del usuario a eliminar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Usuario eliminado exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/fecha/entrega/{id}/{fecha}": {
      "put": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de entrega de un anteproyecto. Solo disponible para credenciales con permisos de administrador.<b>",
        "operationId": "addFechaEntrega",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del anteproyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "fecha",
            "in": "path",
            "description": "Nueva fecha a asociar con el anteproyecto.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha de entrega modificada correctamente."
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/fecha/devolucion/{id}/{fecha}": {
      "put": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de devolución de un anteproyecto. Solo es accesible con credencial de administrador.<b>",
        "operationId": "addFechaDevolucion",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del anteproyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "fecha",
            "in": "path",
            "description": "Nueva fecha a asociar con el anteproyecto.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha de devolucion modificada correctamente."
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/fecha/creacion/{id}/{fecha}": {
      "put": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de creacion de un anteproyecto. Solo se puede acceder a este método por medio de una credencial de administrador.<b>",
        "operationId": "addFechaCreacion",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del anteproyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "fecha",
            "in": "path",
            "description": "Nueva fecha a asociar con el anteproyecto.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha de creacion agregada exitosasmente."
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/estado/{estado}/{idAnteproyecto}": {
      "put": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de actualizar el estado de un anteproyecto. Solo se puede acceder a este método con credencial de administrador.<b>",
        "operationId": "changeEstado",
        "parameters": [
          {
            "name": "estado",
            "in": "path",
            "description": "Id del anteproyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "integer",
              "format": "int32"
            }
          },
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Nuevo estado a asociar con el anteproyecto.<br>1. Aprobado<br>2. No aprobado<br>\t3. Pendiente (Default)",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string"
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto": {
      "get": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para traer todos los anteproyectos con sus Autores y evaluadores asociados. Este método solo puede se accedido desde una credencial administrador.<b>",
        "operationId": "getAllAnteproyectos",
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/Anteproyecto"
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      },
      "post": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para agergar un nuevo anteproyectos con sus Autores y evaluadores asociados. Este método solo puede se accedido desde una credencial administrador.<b>",
        "operationId": "addAnteproyecto",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AnteproyectoInput"
              }
            }
          },
          "required": true
        },
        "responses": {
          "201": {
            "description": "Created",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Anteproyecto creado satisfactoriamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/evaluador/{idEvaluador}/{idAnteproyecto}": {
      "post": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para agregar un evaluador a un anteproyecto. Este método solo puede ser accedido desde una credencial de administrador.<b>",
        "operationId": "addEvaluadorToAnteproyecto",
        "parameters": [
          {
            "name": "idEvaluador",
            "in": "path",
            "description": "Id del evaluador a asociar con el anteproyecto.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto que se desea modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "isDirector",
            "in": "query",
            "description": "Boolean para determianr si este nuevo evaluador es o no el director de ese anteproyecto.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "boolean"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Evaluador agregado exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      },
      "delete": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de borrar un Evaluador de un anteproyecto. Este método solo puede se accedido por medio de una credencial de administrador.<b>",
        "operationId": "deleteEvaluador",
        "parameters": [
          {
            "name": "idEvaluador",
            "in": "path",
            "description": "Id del evaluador a eliminar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto del cual se debe eliminar el evaluador.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "El evaluador fue eliminado del anteproyecto."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/autor/{idAutor}/{idAnteproyecto}": {
      "post": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para agregar un autor a un anteproyecto. Este método solo puede ser accedido desde una credencial de administrador.<b>",
        "operationId": "addAutorToAnteproyecto",
        "parameters": [
          {
            "name": "idAutor",
            "in": "path",
            "description": "Id del autor a agregar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Se agrego al autor satisfactoriamente"
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      },
      "delete": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para borrar un autor de un anteproyecto. Este método solo puede ser accedido desde una credencial de administrador.<b>",
        "operationId": "deleteAutor",
        "parameters": [
          {
            "name": "idAutor",
            "in": "path",
            "description": "Id del autor a borrar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto de donde se quire eliminar el autor.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Autor Borrado exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/evaluador/{idAnteproyecto}": {
      "get": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para obtener todos los evaluadores asociados a un anteproyecto en particular. Este método solo puede ser accedido desde una credencial de administrador.<b>",
        "operationId": "findEvaluadorOfAnteproyecto",
        "parameters": [
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto que se desea consultar sus evaluadores.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "uniqueItems": true,
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/Evaluador"
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/autor/{idAnteproyecto}": {
      "get": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método sirve para obtener todos los autores asociados a un anteproyecto en particular. Este método solo puede ser accedido desde una credencial de administrador.<b>",
        "operationId": "findAutoresOfAnteproyecto",
        "parameters": [
          {
            "name": "idAnteproyecto",
            "in": "path",
            "description": "Id del anteproyecto que se desea consultar sus autores.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "uniqueItems": true,
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/User"
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/anteproyecto/{id}": {
      "delete": {
        "tags": [
          "Anteproyecto"
        ],
        "description": "<b>Este método se encarga de eliminar un anteproyecto y sus relaciones e.g las relaciones con usuarios que sean autores o evaluadores.<b>",
        "operationId": "deleteAnteproyecto",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del anteproyecto a borrar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Anteproyecto borrado exitosamente"
                }
              }
            }
          },
          "500": {
            "description": "Internal Server Error",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Anteproyecto no pudo ser borrado"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/sustentacion/{id}/{date}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de sustentación de un proyecto de grado.<b>",
        "operationId": "setFechaSustentacion",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto que se quiere modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "date",
            "in": "path",
            "description": "Nueva fecha.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha cambiada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/postulacion/{id}/{fecha}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de postulación de un proyecto de grado.<b>",
        "operationId": "setPostulacion",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "fecha",
            "in": "path",
            "description": "Nueva fecha.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha de postulación cambiada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/mencion/{id}/{mencion}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar si el proyecto de grado es o no mención de honor.<b>",
        "operationId": "setMencionHonor",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto ha modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "mencion",
            "in": "path",
            "description": "Valor booleano de mención de honor del proyecto.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "boolean"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Mención de Honor modificada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/fecha-creacion/{id}/{fecha}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar la fecha de creacion de un proyecto de grado.<b>",
        "operationId": "setFechaCreacion",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "fecha",
            "in": "path",
            "description": "Nueva fecha.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "date-time"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Fecha de Creación cambiada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/docs/{id}/{docs}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar si ya se hizo entrega o no de los documentos de un proyecto de grado.<b>",
        "operationId": "setEntregaDocs",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto de grado a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "docs",
            "in": "path",
            "description": "Valor boolean de la modificación.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "boolean"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Entrega de documentos cambiada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/definitiva/{id}/{nota}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar la nota final de un proyecto de grado.<b>",
        "operationId": "setFechaSustentacion_1",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto de grado a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "nota",
            "in": "path",
            "description": "Nueva nota del proyecto de grado. [0,5]",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "number",
              "format": "float"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Nota definitva cambiada exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/acta/{id}/{acta}": {
      "put": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de modificar el número de acta de un proyecto de grado.<b>",
        "operationId": "setFechaSustentacion_2",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id del proyecto de grado a modificar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "acta",
            "in": "path",
            "description": "Nuevo númeor de acta.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "integer",
              "format": "int32"
            }
          }
        ],
        "responses": {
          "202": {
            "description": "Accepted",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Número de acta cambiado exitosamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto": {
      "post": {
        "tags": [
          "Proyecto"
        ],
        "description": "Este método se encarga de crear un nuevo proyecto. Los proyectos se deben crear a partir de un anteproyecto ya existente. el unico dato para crear un proyecto es el Id del anteproyecto asociado. Solo se puede acceder a este método con una credencial de administrador.",
        "operationId": "addProyecto",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/proyecto_body"
              }
            }
          },
          "required": true
        },
        "responses": {
          "201": {
            "description": "Created",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Proyecto creado exitosamente. "
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          },
          "404": {
            "description": "Not Found",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Not found information"
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/proyecto/all": {
      "get": {
        "tags": [
          "Proyecto"
        ],
        "description": "<b>Este método se encarga de traer todos los anteproyecto que hay en el sistema. Solo se puede accedera este método con una credencial de adminstrador.<b>",
        "operationId": "getProyectos",
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/Proyecto"
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    },
    "/file/upload": {
      "post": {
        "tags": [
          "File"
        ],
        "description": "<b>Este método se encarga de hacer una entrega de documento asociado a un proyecto o anteproyecto.",
        "operationId": "uploadFile",
        "parameters": [
          {
            "name": "file",
            "in": "query",
            "description": "Archivo a subir como entrega.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "string",
              "format": "binary"
            }
          },
          {
            "name": "idAsociado",
            "in": "query",
            "description": "Id del proyecto o anteproyecto asociado.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          },
          {
            "name": "description",
            "in": "query",
            "description": "Descripción o comentarios de entrega.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "string"
            }
          },
          {
            "name": "isAnteproyecto",
            "in": "query",
            "description": "Valor booleano para saber si es una entrega asociada a un anteproyecto o a un proyecto.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "boolean"
            }
          },
          {
            "name": "nroEntrega",
            "in": "query",
            "description": "Número de entrega que se va a realizar.",
            "required": true,
            "style": "form",
            "explode": true,
            "schema": {
              "type": "integer",
              "format": "int32"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "content": {
              "*/*": {
                "schema": {
                  "type": "string",
                  "example": "Documento subido satisfactoriamente."
                }
              }
            }
          },
          "400": {
            "description": "Bad Request",
            "content": {
              "application/json": {
                "example": {
                  "error_message": "Bad request information"
                }
              }
            }
          }
        }
      }
    },
    "/file": {
      "get": {
        "tags": [
          "File"
        ],
        "operationId": "getFiles",
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "*/*": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/File"
                  }
                }
              }
            }
          }
        }
      }
    },
    "/file/download/{id}": {
      "get": {
        "tags": [
          "File"
        ],
        "description": "<b>Este método se encarga de traer el documento asociado a una entrega. No es necesaria ninguna autenticación para hacer las descargas.",
        "operationId": "downloadFile",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "description": "Id de la entrega que se desea descargar.",
            "required": true,
            "style": "simple",
            "explode": false,
            "schema": {
              "type": "string",
              "format": "uuid"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "application/pdf": {
                "schema": {
                  "type": "object"
                }
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "GrantedAuthority": {
        "type": "object",
        "properties": {
          "authority": {
            "type": "string"
          }
        }
      },
      "Role": {
        "type": "object",
        "properties": {
          "roleId": {
            "type": "integer",
            "format": "int32"
          },
          "descripcion": {
            "type": "string"
          }
        }
      },
      "User": {
        "type": "object",
        "properties": {
          "userId": {
            "type": "string",
            "format": "uuid"
          },
          "personalId": {
            "type": "integer",
            "format": "int32"
          },
          "password": {
            "type": "string"
          },
          "name": {
            "type": "string"
          },
          "lastname": {
            "type": "string"
          },
          "roles": {
            "uniqueItems": true,
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/Role"
            }
          },
          "enabled": {
            "type": "boolean"
          },
          "authorities": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/GrantedAuthority"
            }
          },
          "accountNonLocked": {
            "type": "boolean"
          },
          "accountNonExpired": {
            "type": "boolean"
          },
          "credentialsNonExpired": {
            "type": "boolean"
          },
          "email": {
            "type": "string"
          }
        }
      },
      "Proyecto": {
        "type": "object",
        "properties": {
          "proyectoId": {
            "type": "string",
            "format": "uuid"
          },
          "anteproyectoId": {
            "type": "string",
            "format": "uuid"
          },
          "fechaSustentacion": {
            "type": "string",
            "format": "date"
          },
          "fechaCreacion": {
            "type": "string",
            "format": "date"
          },
          "notaDefinitiva": {
            "type": "number",
            "format": "float"
          },
          "nroActa": {
            "type": "integer",
            "format": "int32"
          },
          "mencionHonor": {
            "type": "boolean"
          },
          "gradoPostulacion": {
            "type": "string",
            "format": "date"
          },
          "entregaDocs": {
            "type": "boolean"
          }
        }
      },
      "Registration": {
        "type": "object",
        "properties": {
          "personalId": {
            "type": "string"
          },
          "email": {
            "type": "string"
          },
          "password": {
            "type": "string"
          },
          "name": {
            "type": "string"
          },
          "lastname": {
            "type": "string"
          }
        }
      },
      "Login": {
        "type": "object",
        "properties": {
          "email": {
            "type": "string"
          },
          "password": {
            "type": "string"
          }
        }
      },
      "AnteproyectoInput": {
        "type": "object",
        "properties": {
          "nroRadicacion": {
            "type": "integer",
            "format": "int32"
          },
          "titulo": {
            "type": "string"
          },
          "autores": {
            "type": "array",
            "items": {
              "type": "string",
              "format": "email"
            }
          },
          "evaluadores": {
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/EvaluadorInfo"
            }
          }
        }
      },
      "EvaluadorInfo": {
        "type": "object",
        "properties": {
          "email": {
            "type": "string"
          },
          "director": {
            "type": "boolean"
          }
        }
      },
      "File": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "format": "uuid"
          },
          "idAsociado": {
            "type": "string",
            "format": "uuid"
          },
          "isAnteproyecto": {
            "type": "boolean"
          },
          "filename": {
            "type": "string"
          },
          "description": {
            "type": "string"
          },
          "nroEntrega": {
            "type": "integer",
            "format": "int32"
          },
          "data": {
            "type": "array",
            "items": {
              "type": "string",
              "format": "byte"
            }
          }
        }
      },
      "Anteproyecto": {
        "type": "object",
        "properties": {
          "anteproyectoId": {
            "type": "string",
            "format": "uuid"
          },
          "noRadicacion": {
            "type": "integer",
            "format": "int32"
          },
          "titulo": {
            "type": "string"
          },
          "fechaEntregaAEvaluador": {
            "type": "string",
            "format": "date"
          },
          "fechaEntregaDeEvaluador": {
            "type": "string",
            "format": "date"
          },
          "fechaCreacion": {
            "type": "string",
            "format": "date"
          },
          "fechaAprobacion": {
            "type": "string",
            "format": "date"
          },
          "estado": {
            "type": "integer",
            "format": "int32"
          },
          "autores": {
            "uniqueItems": true,
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/User"
            }
          },
          "evaluadores": {
            "uniqueItems": true,
            "type": "array",
            "items": {
              "$ref": "#/components/schemas/Evaluador"
            }
          }
        }
      },
      "Evaluador": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "format": "uuid"
          },
          "anteproyectoId": {
            "type": "string",
            "format": "uuid"
          },
          "userId": {
            "type": "string",
            "format": "uuid"
          },
          "director": {
            "type": "boolean"
          }
        }
      },
      "inline_response_200": {
        "type": "object",
        "properties": {
          "message": {
            "type": "string",
            "example": "Usuario creado satisfactoriamente"
          }
        }
      },
      "inline_response_200_1": {
        "type": "object",
        "properties": {
          "token": {
            "type": "string"
          }
        }
      },
      "proyecto_body": {
        "type": "object",
        "properties": {
          "anteproyectoId": {
            "type": "string",
            "format": "uuid"
          }
        }
      }
    },
    "responses": {
      "BadRequest": {
        "description": "Bad Request",
        "content": {
          "application/json": {
            "example": {
              "error_message": "Bad request information"
            }
          }
        }
      },
      "NotFound": {
        "description": "Not Found",
        "content": {
          "application/json": {
            "example": {
              "error_message": "Not found information"
            }
          }
        }
      }
    },
    "securitySchemes": {
      "bearerAuth": {
        "type": "http",
        "scheme": "bearer",
        "bearerFormat": "JWT"
      }
    }
  }
}
