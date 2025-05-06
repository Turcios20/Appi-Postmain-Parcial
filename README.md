# POSTMAIL - API para la Gestión Integral de Envíos y Control de Créditos.

Este proyecto consiste en una API para la gestión de envíos de la empresa POSTMAIL. Permite a los usuarios realizar operaciones como registrar nuevos envíos, consultar los créditos disponibles y administrar los productos a enviar. La aplicación utiliza MongoDB como sistema de base de datos y Express.js como framework para la creación del servidor y el manejo de rutas.

# Especificación de la API

# 1. Crear un usuario con créditos según el plan
- **Método:** `POST`
- **Ruta:** `/crear-usuario`  
- **Descripción:** Registra un nuevo usuario y asigna créditos de acuerdo al plan seleccionado.  
  **Planes disponibles:**
  - Plan 1: 30 envíos por $135
  - Plan 2: 40 envíos por $160
  - Plan 3: 60 envíos por $180

**Ejemplo de cuerpo (JSON):**
```json
{
  "nombre": "Ronaldo Turcios",
  "plan": 1
}
```

**Respuesta esperada:**
```json
{
  "mensaje": "El usuario ha sido registrado con éxito.",
  "usuario": {
    "nombre": "Ronaldo Turcios",
    "creditos": 30,
    "costoPorEnvio": 4.5
  }
}
```


# 2. Ver créditos de un usuario
- **Método:** `GET`  
- **Ruta:** `/credito/:id`  
- **Descripción:** Consultar los créditos disponibles del usuario.

**Respuesta esperada:**
```json
{
  "nombre": "Ronaldo Turcios",
  "creditosDisponibles": 30,
  "costoPorEnvio": 4.5
}
```


# 3. Registrar un nuevo envío
- **Método:** `POST`  
- **Ruta:** `/envio/:id`  
- **Descripción:** Registrar un nuevo envío para un usuario, incluyendo el producto y la información detallada del envío.

**Ejemplo de cuerpo (JSON):**
```json
{
  "nombre": "Ronaldo Turcios",
  "direccion": "Calle Las Flores 0780",
  "telefono": "123456789",
  "referencia": "Porton Negro",
  "observacion": "Entregar de Lunes a Sabado",
  "descripcion": "Paquete con producto",
  "peso": 2,
  "bultos": 1,
  "fecha_entrega": "2025-05-10T10:00:00Z"
}
```

**Respuesta esperada:**
```json
{
  "mensaje": "El envío ha sido registrado con éxito."
}
```


# 4. Consultar todos los envíos de un usuario
- **Método:** `GET`  
- **Ruta:** `/envios/:id`  
- **Descripción:** Obtener todos los envíos registrados de un usuario.

**Respuesta esperada:**
```json
{
  "envios": [
    {
      "nombre": "Ronaldo Turcios",
      "direccion": "Calle Las Flores 0780",
      "telefono": "123456789",
      "referencia": "Porton Negro",
      "observacion": "Entregar de Lunes a Sabado",
      "descripcion": "Paquete con producto",
      "peso": 2,
      "bultos": 1,
      "fecha_entrega": "2025-05-10T10:00:00Z"
    }
    {
      "costo": 4.5,
      "_id": "68195bc3d6d3d95ea3cfd77f",
      "fecha_envio": "2025-05-06T00:45:55.984Z"
    }
  ]
}
```


# 5. Eliminar un envío y devolver créditos
- **Método:** `DELETE`  
- **Ruta:** `/envio/:userId/:envioId`  
- **Descripción:** Eliminar un envío registrado y reembolsar los créditos correspondientes al usuario.

**Respuesta esperada:**
```json
{
  "mensaje": "El envío fue eliminado y los créditos han sido reembolsados."
}
```

# Tecnologías utilizadas

- Node.js  
- Express.js  
- MongoDB  
- Mongoose  

