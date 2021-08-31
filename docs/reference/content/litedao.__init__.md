
Back to [Reference Overview](https://github.com/pyrustic/litedao/blob/master/docs/reference/README.md)

# litedao.\_\_init\_\_



<br>


```python

class Error:
    """
    Common base class for all non-exit exceptions.
    """

    def __init__(self, *args, **kwargs):
        """
        Initialize self.  See help(type(self)) for accurate signature.
        """

```

<br>

```python

class Litedao:
    """
    It's recommended to use Dao by composition. Meaning: don't subclass it.
    DAO: Data Access Object (this one is built to work with SQLite).
    You give an SQL request with some params or not, it spills out the result nicely !
    You can even get the list of tables or columns.
    """

    def __init__(self, path, init_script=None, raise_exception=True, raise_warning=True, connection_kwargs=None):
        """
        - path: absolute path to database file
        
        - init_script: a path to a file, a file-like object or a string of sql code
            Example_a: "CREATE TABLE my_table(id INTEGER NOT NULL PRIMARY KEY);"
            Example_b: "/path/to/script.sql"
        
        - raise_exception: By default, True, so exceptions (sqlite.Error) will be raised
        
        - raise_warning: By default, True, so exceptions (sqlite.Warning) will be raised
        
        - connection_kwargs: connections arguments used while calling the
         method "sqlite.connect()"
        """

    @property
    def con(self):
        """
        Connection object
        """

    @property
    def init_script(self):
        """
        
        """

    @property
    def is_new(self):
        """
        Returns True if the database has just been created, otherwise returns False
        """

    @property
    def path(self):
        """
        
        """

    def close(self):
        """
        Well, it closes the connection
        """

    def columns(self, table):
        """
        Returns the list of columns names of the given table name
        A column is like:
            (int_id, str_column_name, str_column_datatype, int_boolean_nullability,
            default_value, int_primary_key)
        Example:
            [(0, "id", "INTEGER", 1, None, 1),
            (1, "name", "TEXT", 0, None, 0),
            (2, "age", "INTEGER", 1, None, 0)]
        
        This method can raise sqlite.Error, sqlite.Warning
        """

    def edit(self, sql, param=None):
        """
        Use this method to edit your database.
        Formally: Data Definition Language (DDL) and Data Manipulation Language (DML).
        It returns True or False or raises sqlite.Error, sqlite.Warning
        """

    def export(self):
        """
        export the database: it returns a string of sql code.
        This method can raise sqlite.Error, sqlite.Warning
        """

    def query(self, sql, param=None):
        """
        Use this method to query your database.
        Formally: Data Query Language (DQL)
        It returns a tuple: (data, description).
                Data is a list with data from ur query.
                Description is a list with the name of columns related to data
            Example: ( [1, "Jack", 50], ["id", "name", "age"] )
            This method can raise sqlite.Error, sqlite.Warning
        """

    def script(self, script):
        """
        Executes the script as an sql-script. Meaning: there are multiple lines of sql.
        This method returns nothing but could raise sqlite.Error, sqlite.Warning.
        
        script could be a path to a file, a file-like object or just a string.
        """

    def tables(self):
        """
        Returns the list of tables names.
        Example: ["table_1", "table_2"]
        This method can raise sqlite.Error, sqlite.Warning
        """

    def test(self):
        """
        Returns True if this is a legal database, otherwise returns False
        """

```

