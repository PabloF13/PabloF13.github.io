---
layout: post
title:  Base de datos PostgreSQL desplegada en Heroku"
author: ana
categories: [ PostgreSQL, Heroku ]
image: assets/images/2021-10-27-nomads-postgresql-heroku.png
---



Tras la pandemia y la generalización del teletrabajo han emergido los nómadas digitales, las personas que trabajan desde cualquier parte del mundo. Un poco de envidia sí que dan, ¿verdad?. Con este target en mente, antigüos estudiantes de The Bridge estamos desarrollando la app *Digital&Nomads*.

Una parte importante de la aplicación son los datos propios de cada una de las ciudades españolas como destinos ideales para nómadas digitales. Datos como el coste de vida de la ciudad, información del tiempo y temperatura media los almacenamos en una base de datos. El equipo de Data y de Full Stack nos decidimos por montarla en `PostgreSQL` y alojarla en un servidor gratuito para la prueba de concepto, como es `Heroku`.

A continuación explico los pasos para crear una base de datos PostgreSQL en Heroku y como hacer la subida de algunos registros con `Python` y `SQLAlchemy`.

## Creación aplicación en Heroku con base de datos PostgreSQL
Lo primero es crear una [cuenta gratuita en Heroku](https://signup.heroku.com/login). Después debemos crear una app en Heroku en el botón `New` que está arriba a la derecha.

![Nueva app en Heroku](/assets/images/nomads/heroku-newApp.png)

Ahora tenemos que añadir la base de datos. Para ello entramos en nuestra app y seleccionamos la pestaña Resources. Como queremos añadir la base de datos como un *add-on*, tenemos que buscar *Heroku Postgres* en el campo de texto del buscador.

![Búsqueda add-on Postgres en Heroku](/assets/images/nomads/heroku-postgresql-search.png)

Tras la búsqueda nos aparecerá un *pop-up* en el que tenemos que dejar seleccionada la opción `Hobby Dev - Free` y clickar en el botón `Submit Order Form` y ya nos aparecerá el *add-on Heroku Postgres* creado.

![Creación de add-on Postgres en Heroku](/assets/images/nomads/heroku-postgresql-submit.png)

![Creación de add-on Postgres en Heroku](/assets/images/nomads/heroku-postgresql-submit.png)

Si accedemos al *add-on Heroku Postgres* veremos toda la información de la base de datos como el tamaño y número de registros. Las credenciales para conectarnos a la base de datos las podemos ver en la pestaña Settings si pulsamos el botón `View credentials...`.

## Conexión a la base de datos PostgreSQL con Python

Ahora que tenemos la base de datos deplegada podemos crear la tabla y escribir los datos en ella. Lo primero que debemos hacer es crear un archivo exclusivo para las credenciales: `config_produccion.py`. Después creamos el archivo `postgres_conn.py` para establecer la conexión con la base de datos mediante el uso de la librería `SQLAlchemy`. Podemos ver el código de ambos archivos a continuacion:

### `config_produccion.py`

```python
host = 'ec2-43-203-100-53.eu-west-1.compute.amazonaws.com'
port = 5432
database = '9ct28tgiw9r7qi'
user = '6cnfak2u5746br'
password = 'h4tgwj4frkzrkbuwi2wk3v3bybha39g4ehvjkkkua9ff75nq85px9a8p5z4dzjvp'
```

### `postgres_conn.py`

```python
import pandas as pd
from sqlalchemy import create_engine
from config_produccion import host, port, database, user, password

# Cargar datos provenientes de csv
df = pd.read_csv('variables_ciudades.csv')
df.index.names = ['id']

# crear engine
engine = create_engine(f'postgresql://{user}:{password}@{host}:{port}/{database}')

# borrar tabla si existe
sql = f'DROP TABLE IF EXISTS {table};'
result = engine.execute(sql)
print(result)

# crear tabla con tipos definidos
sql = """
CREATE TABLE cities (
    id SERIAL,
    name VARCHAR(128) UNIQUE,
    population INTEGER,
    coverage_broadband SMALLINT,
    coverage_4g SMALLINT,
    latitude DECIMAL(16, 14),
    longitude DECIMAL(16, 14),
    cost_living_index NUMERIC,
    rent_index NUMERIC,
    cost_living_rent_index NUMERIC,
    groceries_index NUMERIC,
    restaurant_index NUMERIC,
    humidity SMALLINT,
    sun_hours NUMERIC,
    sunny_days NUMERIC,
    spring_temp_min SMALLINT,
    spring_temp_max SMALLINT,
    summer_temp_min SMALLINT,
    summer_temp_max SMALLINT,
    autumn_temp_min SMALLINT,
    autumn_temp_max SMALLINT,
    winter_temp_min SMALLINT,
    winter_temp_max SMALLINT,
    description TEXT,
    PRIMARY KEY(id)
);
"""
result = engine.execute(sql)
print(result)

# Insertar registros
table = 'cities'
df.to_sql(table, engine, if_exists='append')

# Cerrar conexión
engine.dispose()
```
