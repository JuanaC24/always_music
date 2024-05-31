# Always Music - Desafío

Este proyecto es parte del desafío de Always Music, donde se requiere desarrollar una aplicación en Node.js para gestionar estudiantes en una escuela de música, utilizando PostgreSQL para la base de datos.

## Tabla de Contenidos

1. [Descripción](#descripción)
2. [Instalación](#instalación)
3. [Uso](#uso)
4. [Configuración](#configuración)


## Descripción

La escuela de música Always Music es reconocida en la ciudad por graduar a grandes músicos de reconocimiento mundial. Sin embargo, han decidido cambiar su antigua base de datos en Excel por una solución personalizada en Node.js y PostgreSQL.

Esta aplicación permite:
- Agregar un nuevo estudiante.
- Consultar los estudiantes registrados.
- Consultar un estudiante por RUT.
- Actualizar la información de un estudiante.
- Eliminar el registro de un estudiante.

## Instalación

Sigue estos pasos para instalar y configurar el proyecto localmente:

1. Clona el repositorio:

    ```bash
    git clone https://github.com/JuanaC24/always_music.git
    cd always_music
    ```

2. Instala las dependencias:

    ```bash
    npm install
    ```

3. Crea un archivo `.env` en la raíz del proyecto y agrega tus variables de entorno:

    ```env
    DB_USER=postgres
    DB_HOST=localhost
    DB_DATABASE=always_music
    DB_PASSWORD=tu_contraseña
    DB_PORT=5432
    ```

4. Crea la base de datos y la tabla en PostgreSQL:

    ```sql
    CREATE DATABASE always_music;
    \c always_music

    CREATE TABLE estudiantes (
      id SERIAL PRIMARY KEY,
      nombre VARCHAR(100),
      rut VARCHAR(10) UNIQUE,
      curso VARCHAR(50),
      nivel VARCHAR(50)
    );
    ```

## Uso

Para interactuar con la aplicación, puedes utilizar los siguientes comandos:

1. **Agregar un nuevo estudiante**:

    ```bash
    node app.js add -n "Juan Pérez" -r "12345678-9" -c "Guitarra" -l "Intermedio"
    ```

2. **Obtener todos los estudiantes**:

    ```bash
    node app.js getAll
    ```

3. **Obtener un estudiante por RUT**:

    ```bash
    node app.js get -r "12345678-9"
    ```

4. **Actualizar un estudiante**:

    ```bash
    node app.js update -r "12345678-9" -n "Juan Pérez" -c "Piano" -l "Avanzado"
    ```

5. **Eliminar un estudiante**:

    ```bash
    node app.js delete -r "12345678-9"
    ```

## Configuración

Asegúrate de configurar correctamente las variables de entorno en el archivo `.env`. Aquí un ejemplo:

```env
DB_USER=postgres
DB_HOST=localhost
DB_DATABASE=always_music
DB_PASSWORD=tu_contraseña
DB_PORT=5432
