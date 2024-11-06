# Defining Datasources

The datasource configuration struct should be defined exactly the same whether you are using an inline, ad-hoc datasource or configuring a datasource in your `boxlang.json` or `Application.bx`. Make sure you have a "driver" key defined OR the driver clearly denoted in the JDBC url:

```js
this.datasources[ "testDB" ] = {
	"driver": "mysql",
	// OR:
	"url" : "jdbc:mysql://localhost:3306/test"
};
```

## Defining Datasources In `boxlang.json`

You can define a datasource at the BoxLang runtime level by placing it in your `boxlang.json`:

{% code title="boxlang.json" %}
```js
  "datasources": {
      "theDerbyDB": {
      	"driver": "derby",
    	"connectionString": "jdbc:derby:memory:testDB;create=true"
      },
      "theMysqlDB": {
      	"driver": "mysql",
        "host": "${env.MYSQL_HOST:localhost}",
        "port": "${env.MYSQL_PORT:3306}",
        "database": "${env.MYSQL_DATABASE:myDB}",
        "username": "${env.MYSQL_USERNAME:root}",
        "password": "${env.MYSQL_PASSWORD}"
      }
  },
```
{% endcode %}

Note the use of BoxLang's environment variable replacement syntax for the datasource properties: `${env.MYSQL_HOST:localhost}`. See [Environment Variable Substitution](../getting-started/configuration.md#environment-variable-substitution) for more info.

## Defining Datasources In `Application.bx`

For web runtimes, you can also define the datasources in the `Application.bx`, which is sometimes our preferred approach as the connections are versioned controlled and more visible than in the admin. You will do this by defining a struct called `this.datasources`. Each **key** will be the name of the datasource to register and the **value** of each key a struct of configuration information for the datasource. However, we recommend that you setup environment variables in order to NOT store your passwords in plain-text in your source code.

{% code title="Application.bx" %}
```java
class{
    this.datasources = {
        // Driver Approach
        mysql = {
            database : "mysql",
            host : "localhost",
            port : "3306",
            driver : "MySQL",
            username : "root",
            password : "mysql",
            options : value
        },
        // URL approach
        mysql2 = {
            driver : "mysql",
            url : "jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=UTF-8&useLegacyDatetimeCode=true",
            username : "",
            password : ""
        },
        // Shorthand Approach
        myDSN = {
            class : "com.mysql.jdbc.Driver",
            connectionString : "jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=UTF-8&useLegacyDatetimeCode=true",
            username : "",
            password : ""
        },
        // Long Approach
        myDSN = {
            type : "mysql",
            database : "mysql",
            host : "localhost",
            port : "3306",
            username : "",
            password : ""
        }
    };
}
```
{% endcode %}

{% hint style="success" %}
For the inline approach, you will use the struct definition, as you see in the `Application.bx` above and pass it into the `bx:query` or `queryexecute` call.
{% endhint %}

## Defining Inline Datasources

Finally, for smaller or simpler applications with few queries, you may find it useful to define your datasource at query time. So instead of giving the name of the `datasource`, it can be a `struct` definition of the datasource you want to connect to:

```js
queryExecute(
  "SELECT * FROM Employees WHERE empid = ? AND country = ?", // sql
  [ 1, "USA" ], // params
  { // options
    datasource : {
      "driver": "mysql",
      "host": "${env.MYSQL_HOST:localhost}",
      "port": "${env.MYSQL_PORT:3306}",
      "database": "${env.MYSQL_DATABASE:myDB}",
      "username": "${env.MYSQL_USERNAME:root}",
      "password": "${env.MYSQL_PASSWORD}"
    }
  }
)
```

## Default Datasource

You can also define a default datasource to allow you to omit the `datasource` completely from query calls.

To do this, you'll need to define a default datasource in one of two locations:

1. In your BoxLang runtime's `boxlang.json` config file via the `defaultDatasource` key
2. or, for web server runtimes, in a `this.datasource` variable in your `Application.bx` file

### Defining a default datasource via boxlang.json

{% code title="boxlang.json" %}
```json
   "defaultDatasource: {
      "driver": "mysql",
       "host": "${env.MYSQL_HOST:localhost}",
       "port": "${env.MYSQL_PORT:3306}",
       "database": "${env.MYSQL_DATABASE:myDB}",
       "username": "${env.MYSQL_USERNAME:root}",
       "password": "${env.MYSQL_PASSWORD}"
    },
   "datasources": {
      // You can still define additional datasources here! You're not limited to the default datasource
   },
```
{% endcode %}

### Defining a default datasource via Application.bx

{% code title="Application.bx" %}
```java
class{
    this.name = "myApp";

    // Default Datasource Name
    this.datasource = "pantry";

}
```
{% endcode %}

## Portable Datasources

You can also make your data sources portable from application to application or BoxLang engine to engine by using our [CFConfig](https://cfconfig.ortusbooks.com/) project. CFConfig allows you to manage almost every setting that shows up in the web administrator, but instead of logging into a web interface, you can manage it from the command line by hand or as part of a scripted server setup. You can seamlessly transfer config for all the following:

* CF Mappings
* Data sources
* Mail servers
* Request, session, or application timeouts
* Licensing information
* Passwords
* Template caching settings
* Basically any settings in the web based administrator

You can easily place a `.cfconfig.json` in the web root of your project, and if you start up a CommandBox server on any BoxLang engine, CFConfig will transfer the configuration to the engine's innards:

{% code title=".cfconfig.json" %}
```java
{
    "requestTimeoutEnabled":true,
    "whitespaceManagement":"white-space-pref",
    "requestTimeout":"0,0,5,0",
    "cacheDefaultObject":"coldbox",
    "caches":{
        "coldbox":{
            "storage":"true",
            "type":"RAM",
            "custom":{
                "timeToIdleSeconds":"1800",
                "timeToLiveSeconds":"3600"
            },
            "readOnly":"false"
        }
    },
    "datasources" : {
         "coldbox":{
             "host":"${DB_HOST}",
             "dbdriver":"${DB_DRIVER}",
             "database":"${DB_DATABASE}",
             "dsn":"jdbc:mysql://{host}:{port}/{database}",
             "custom":"useUnicode=true&characterEncoding=UTF-8&useLegacyDatetimeCode=true&autoReconnect=true",
             "port":"${DB_PORT}",
             "class":"${DB_CLASS}",
             "username":"${DB_USER}",
             "password":"${DB_PASSWORD}",
             "connectionLimit":"100",
             "connectionTimeout":"1"
         }
    }
}
```
{% endcode %}

{% embed url="https://cfconfig.ortusbooks.com/using-the-cli/command-overview" %}