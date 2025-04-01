# Análisis de Datos para Propuesta de Valor en Lectura en Línea

[![Licencia MIT](https://img.shields.io/badge/Licencia-MIT-blue.svg)](LICENSE)
[![Python Version](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)

## Descripción del Proyecto
En el contexto del crecimiento de la lectura en línea tras la pandemia, han surgido múltiples aplicaciones para optimizar este servicio. Este proyecto tiene como objetivo analizar la información de la base de datos de uno de los principales competidores en el mercado de lectura digital. Se estudian datos relacionados con libros, editoriales, autores, calificaciones de clientes y reseñas para desarrollar una propuesta de valor innovadora para un nuevo producto.

El análisis se centra en responder preguntas clave, tales como:
- ¿Cuántos libros se han publicado en fechas recientes?
- ¿Cuáles son los libros mejor valorados y con mayor número de reseñas?
- ¿Qué editorial es la más prolífica en el mercado?
- ¿Qué autores destacan por la alta calificación de sus obras?
- ¿Cuáles son las características de los usuarios más comprometidos?

## Contenido
- [Descripción del Proyecto](#descripción-del-proyecto)
- [Inicialización y Conexión a la Base de Datos](#inicialización-y-conexión-a-la-base-de-datos)
- [Exploración y Validación de Tablas](#exploración-y-validación-de-tablas)
- [Extracción de Información Clave](#extracción-de-información-clave)
  - [Cantidad de Libros Publicados Después del 2000](#cantidad-de-libros-publicados-después-del-2000)
  - [Reseñas y Calificaciones de Libros](#reseñas-y-calificaciones-de-libros)
  - [Editorial con Mayor Número de Publicaciones](#editorial-con-mayor-número-de-publicaciones)
  - [Autor Destacado por Calificación](#autor-destacado-por-calificación)
  - [Compromiso de Usuarios](#compromiso-de-usuarios)
- [Conclusiones](#conclusiones)
- [Aplicaciones en Negocios y Desarrollo de Producto](#aplicaciones-en-negocios-y-desarrollo-de-producto)
- [Instalación y Uso](#instalación-y-uso)
- [Contribución](#contribución)
- [Licencia](#licencia)
- [Contacto](#contacto)

## Inicialización y Conexión a la Base de Datos
El proyecto utiliza Python y SQLAlchemy para conectarse a una base de datos PostgreSQL. Se configuran las credenciales de conexión y se crea un motor de conexión que permite ejecutar consultas SQL para extraer información relevante.

Ejemplo de configuración:
```python
import pandas as pd
from sqlalchemy import create_engine, text

db_config = {
    'user': 'practicum_student',
    'pwd': 's65BlTKV3faNIGhmvJVzOqhs',
    'host': 'rc1b-wcoijxj3yxfsf3fs.mdb.yandexcloud.net',
    'port': 6432,
    'db': 'data-analyst-final-project-db'
}

connection_string = 'postgresql://{}:{}@{}:{}/{}'.format(
    db_config['user'], db_config['pwd'], db_config['host'],
    db_config['port'], db_config['db']
)

engine = create_engine(connection_string, connect_args={'sslmode': 'require'})
