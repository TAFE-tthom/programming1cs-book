# Persistent Data Storage and ADO.NET

Usually when using ASP.NET we want to pair it with a database connect. This is usually in the form of using an ORM like **EntityFramework** but we will use the raw-connector api called **ADO.NET**.


## Using a database and SQL

You can use the following sequelize module to interact with an sql database. Without needing to know much about SQL, you can create a sql database through javascript by constructing the tables and entries through javascript.

It requires the following stages to be performed.

1. Initialise a connection to the database
2. Construct types with fields specified and the relevant types
3. Synchronise the model created with the database

## Adding a database connector

Within this example we will use MySQL/MariaDB database as an example case. You can use MS-SQL, Sqlite and PostgreSQL if you prefer but you will need to use a separate conenctor library.

With `dotnet`, you will need to add the package `MySqlConnector` using `dotnet add package MySqlConnect`. This library will then be added to your project that you then use within your ASP.NET project.


### Connecting to a database

Inside your application you will maintain a way to connect and handle connections to a database. You will need to factor in appropriate credentials and roles for the application accessing this. However for this section, we will assume that we have already done this.

Let's look at the following snippet.

```cs
const string constring =
    "SERVER=localhost; DATABASE=Northwind;" +
    "UID=ahto; PWD=somepassword";


var dbcon = new MySqlConnection(constring);
dbcon.Open();
string query = "SELECT * FROM Customers;";
var cmd = new MySqlCommand(query, dbcon);

var dataReader = cmd.ExecuteReader();

while (dataReader.Read())
{
    var idn = dataReader[0].ToString();
    var name = dataReader[1].ToString();

    Console.WriteLine($"{idn} - {name}");
}

dbcon.Close();
```

There is quite a bit to breakdown but we will start with the first two 5 lines of code. In the snippet below we have the connection string and the object that will form the database connection.

```cs
const string constring =
    "SERVER=localhost; DATABASE=Northwind;" +
    "UID=user; PWD=somepassword";


var dbcon = new MySqlConnection(constring);
dbcon.Open()
```

Once a connection is established, we can then manage it and terminate the connection using `.Close()`. Note that `constring` has a format where it is the address/hostname, database to be used, the username/id and the password to be used.

Once passed to the connection constructor, it will attempt to connect. Afterwards, if successful, we can then execute commands and receive results from this connection.

```cs
string query = "SELECT * FROM Customers;";
var cmd = new MySqlCommand(query, dbcon);

var dataReader = cmd.ExecuteReader();  
```

The above snippet is the query we want to send to the server. We will keep it simple and send trivial select query to the server. The command must have the query string and the database connection. Afterwards, we are able to retrieve a `Reader` from the command, with the results.

```cs
while (dataReader.Read())
{
    var idn = dataReader[0].ToString();
    var name = dataReader[1].ToString();

    Console.WriteLine($"{idn} - {name}");
}
```

Once the reader has been retrieved, we can now process the results and assign it. In this example, we are just taking the first and second fields of the object we are reading and printing them out. However we are to construct objects or use the data however we like.

```
dbcon.Close()
```

Once the session has been finished, we should close the database connection. Use `.Close()` or more appropriately, use the connector within a `using` statement in which the resources will be released when needed.


## Writing Data

Takign the query snippet from above, we can insert data instead of reading. However we need ensure that do it in an appropriate way.

```cs
string query = "INSERT INTO Categories(CategoryID, CategoryName, Description) " +
  "VALUES(@cid, @cname, @cdesc);";

var cmd = new MySqlCommand(query, dbcon);
cmd.Parameters.AddWithValue("cid", "55");
cmd.Parameters.AddWithValue("cname", "Electronics");
cmd.Parameters.AddWithValue("cdesc", "All of the electronics!");

cmd.ExecuteNonQuery();  
```

By accessing the `Parameters`, we are able to call `AddWithValue` which will associate the data matching the sql format we have constructed. Each `@` component, will be its own variable that is then replaced with the value given.


Refer to the documentation for futher [information and guidance](https://mysqlconnector.net/tutorials/basic-api/).
