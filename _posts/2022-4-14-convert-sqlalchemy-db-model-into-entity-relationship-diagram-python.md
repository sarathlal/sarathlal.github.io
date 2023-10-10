---
title: Convert SQLAlchemy DB Model into entity relationship diagram using Python
layout: post
tags:
  - Python
  - SQLAlchemy
  - Database Design
---

Here is my `requirements.txt` for the project.

    greenlet==1.1.2
    psycopg2-binary==2.9.3
    pydot==1.4.2
    pyparsing==3.0.7
    SQLAlchemy==1.4.31
    sqlalchemy-schemadisplay==1.3

If the `graphviz` package was not installed, we have to install it globally. Installing the `graphviz` package as a project package does not work for me.

    sudo apt install graphviz

Here is the Python script to generate diagrams.

    from sqlalchemy_schemadisplay import create_schema_graph
    from sqlalchemy import MetaData

    graph = create_schema_graph(metadata=MetaData('postgresql://db_user_name:db_user_password@db_host_name/db_name'))
    graph.write_png('image_name.png')
