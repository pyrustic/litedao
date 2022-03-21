Back to [All Modules](https://github.com/pyrustic/litedao/blob/master/docs/modules/README.md#readme)

# Module Overview

**litedao**
 
No description

> **Classes:** &nbsp; [Error](https://github.com/pyrustic/litedao/blob/master/docs/modules/content/litedao/content/classes/Error.md#class-error) &nbsp;&nbsp; [Litedao](https://github.com/pyrustic/litedao/blob/master/docs/modules/content/litedao/content/classes/Litedao.md#class-litedao)
>
> **Functions:** &nbsp; None
>
> **Constants:** &nbsp; None

# Class Litedao
It's recommended to use Dao by composition. Meaning: don't subclass it.
DAO: Data Access Object (this one is built to work with SQLite).
You give an SQL request with some params or not, it spills out the result nicely !
You can even get the list of tables or columns.

## Base Classes
object

## Class Attributes


## Class Properties
|Property|Type|Description|Inherited from|
|---|---|---|---|
|con|getter|Connection object||
|init_script|getter|None||
|is_new|getter|Returns True if the database has just been created, otherwise returns False||
|path|getter|None||



# All Methods
[\_\_init\_\_](#__init__) &nbsp;&nbsp; [\_stringify\_script](#_stringify_script) &nbsp;&nbsp; [close](#close) &nbsp;&nbsp; [columns](#columns) &nbsp;&nbsp; [edit](#edit) &nbsp;&nbsp; [export](#export) &nbsp;&nbsp; [query](#query) &nbsp;&nbsp; [script](#script) &nbsp;&nbsp; [tables](#tables) &nbsp;&nbsp; [test](#test)

## \_\_init\_\_
- path: absolute path to database file

- init_script: a path to a file, a file-like object or a string of sql code
    Example_a: "CREATE TABLE my_table(id INTEGER NOT NULL PRIMARY KEY);"
    Example_b: "/path/to/script.sql"

- raise_exception: By default, True, so exceptions (sqlite.Error) will be raised

- raise_warning: By default, True, so exceptions (sqlite.Warning) will be raised

- connection_kwargs: connections arguments used while calling the
 method "sqlite.connect()"



**Signature:** (self, path, init\_script=None, raise\_exception=True, raise\_warning=True, connection\_kwargs=None)





**Return Value:** None.

[Back to Top](#module-overview)


## \_stringify\_script
This method will:
- try to read the script: if the script is a file-like object,
    the content (string) will be returned
- try to open the script: if the script is a path to a file,
    the content (string) will be returned
- if the script is already a string, it will be returned as it,
- the script will be returned as it if failed to read/open



**Signature:** (self, script)





**Return Value:** None.

[Back to Top](#module-overview)


## close
Well, it closes the connection



**Signature:** (self)





**Return Value:** None.

[Back to Top](#module-overview)


## columns
Returns the list of columns names of the given table name
A column is like:
    (int_id, str_column_name, str_column_datatype, int_boolean_nullability,
    default_value, int_primary_key)
Example:
    [(0, "id", "INTEGER", 1, None, 1),
    (1, "name", "TEXT", 0, None, 0),
    (2, "age", "INTEGER", 1, None, 0)]

This method can raise sqlite.Error, sqlite.Warning



**Signature:** (self, table)





**Return Value:** None.

[Back to Top](#module-overview)


## edit
Use this method to edit your database.
Formally: Data Definition Language (DDL) and Data Manipulation Language (DML).
It returns True or False or raises sqlite.Error, sqlite.Warning



**Signature:** (self, sql, param=None)





**Return Value:** None.

[Back to Top](#module-overview)


## export
export the database: it returns a string of sql code.
This method can raise sqlite.Error, sqlite.Warning



**Signature:** (self)





**Return Value:** None.

[Back to Top](#module-overview)


## query
Use this method to query your database.
Formally: Data Query Language (DQL)
It returns a tuple: (data, description).
        Data is a list with data from ur query.
        Description is a list with the name of columns related to data
    Example: ( [1, "Jack", 50], ["id", "name", "age"] )
    This method can raise sqlite.Error, sqlite.Warning



**Signature:** (self, sql, param=None)





**Return Value:** None.

[Back to Top](#module-overview)


## script
Executes the script as an sql-script. Meaning: there are multiple lines of sql.
This method returns nothing but could raise sqlite.Error, sqlite.Warning.

script could be a path to a file, a file-like object or just a string.



**Signature:** (self, script)





**Return Value:** None.

[Back to Top](#module-overview)


## tables
Returns the list of tables names.
Example: ["table_1", "table_2"]
This method can raise sqlite.Error, sqlite.Warning



**Signature:** (self)





**Return Value:** None.

[Back to Top](#module-overview)


## test
Returns True if this is a legal database, otherwise returns False



**Signature:** (self)





**Return Value:** None.

[Back to Top](#module-overview)



