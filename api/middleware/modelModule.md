---
title: Model module
permalink: /api/middleware/model-module/
---

## Overview

This module handles data validation and CRUD. A model instance will try to connect to the database using `config.database.{model name}` from the config.json file. If that does not exist in config, it will use the default database config, i.e. `config.database.host`, `config.database.port`, etc... You can also optionally pass in an existing connection object.

## Arguments

Model(name, fields, [connection], settings) -

* `name` a String that will be unique among models
* `fields` an Object that describes this model's fields, as per the spec
* `connection` Optionally, a connection instance that is already initialized. If not passed in, the model will try to connect with data from config
* `settings` an Object that describes the default behaviour of this model

## Settings

* `cache` true
* `cacheTTL` 300
* `authenticate` true
* `callback` null
* `defaultFilters` null
* `fieldLimiters` null
* `allowExtension` false
* `count` 40
* `sort` "fieldName"
* `sortOrder` 1
<!-- * `storeRevisions` true
* `revisionCollection` "testSchemaHistory"
* `index` -->


## Example Usage

    var model = require(__dirname + '/model');

    // load the schema...
    var mod = model('my_model_name', schema.fields, null, schema.settings);

Also look through the `test/acceptance/workspace/` directories for examples of schemas.
