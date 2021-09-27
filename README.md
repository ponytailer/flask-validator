flask-dantic-schema
============

#### Generate for quart-schema

[![Build Status](https://app.travis-ci.com/huangxiaohen2738/flask-dantic-schema.svg?branch=main)](https://app.travis-ci.com/huangxiaohen2738/flask-dantic-schema)



### Install

 - `pip install schema-validator`

### How to use

```
    from dataclasses import dataclass
    from datetime import datetime
    from typing import Optional
    from pydantic import BaseModel

    from flask import Flask
    from schema_validator import FlaskSchema, validate

    app = Flask(__name__)
    
    FlaskSchema(app)
    
    OR
    
    schema = FlaskSchema()
    schema.init_app(app)

    @dataclass
    class Todo:
        task: str
        due: Optional[datetime]

    class TodoResponse(BaseModel):
        id: int
        name: str

    @app.post("/")
    @validate(body=Todo, responses={200: TodoResponse})
    def create_todo():
        ... # Do something with data, e.g. save to the DB
        return data
       
    app.cli.add_command(generate_schema_command)
    
    virtualenv:  flask schema swagger.json -> generate json swagger
```
