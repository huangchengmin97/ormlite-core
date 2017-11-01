ORMLite Core
============

This package provides the core functionality for the JDBC and Android packages.  Users that are connecting to SQL
databases via JDBC will need to download the [ormlite-jdbc](https://github.com/j256/ormlite-jdbc) package as well. Android
users should download the [ormlite-android](https://github.com/j256/ormlite-android) package as well as this core package.

* For more information, visit the [ORMLite home page](http://ormlite.com/).	
* Online documentation can be found off the home page.  Here's the [getting started docs](http://ormlite.com/docs/getting-started).  Here are the [code Javadocs](http://ormlite.com/javadoc/ormlite-core/).
* Browse the code on the [git repository](https://github.com/j256/ormlite-core).  [![CircleCI](https://circleci.com/gh/j256/ormlite-core.svg?style=svg)](https://circleci.com/gh/j256/ormlite-core) [![CodeCov](https://img.shields.io/codecov/c/github/j256/ormlite-core.svg)](https://codecov.io/github/j256/ormlite-core/)
* Maven packages are published via [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.j256.ormlite/ormlite-core/badge.svg?style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.j256.ormlite/ormlite-core/)
* I've published a [number of example programs](http://ormlite.com/docs/examples).

ORMLite is easy to use and provides the following features:

* Setup your classes by simply adding Java annotations.
* Powerful abstract Database Access Object (DAO) classes.
* Flexible QueryBuilder to easily construct simple and complex queries.
* Supports MySQL, Postgres, Microsoft SQL Server, H2, Derby, HSQLDB, and Sqlite and can be extended to additional databases relatively easily.
* Provisional support for DB2, Oracle, ODBC, and Netezza. Contact the author if your database type is not supported.
* Handles "compiled" SQL statements for repetitive query tasks.
* Supports "foreign" objects with the class field being the object but an id stored in the database table.
* Basic support for database transactions.
* Auto generates SQL to create and drop database tables.
* Spring configuration support for DOAs and class configurations.
* Support for configuring of tables and fields without annotations.
* Supports native calls to Android SQLite database APIs

Enjoy, Gray Watson

## Code Example

The following is a quick code example to give you a taste on how to use the library.

    // this uses h2 but you can change it to match your database
    String databaseUrl = "jdbc:h2:mem:account";
    // create a connection source to our database
    ConnectionSource connectionSource = new JdbcConnectionSource(databaseUrl);
    
    // instantiate the DAO to handle Account with String id
    Dao<Account,String> accountDao = DaoManager.createDao(connectionSource, Account.class);
    
    // if you need to create the 'accounts' table make this call
    TableUtils.createTable(connectionSource, Account.class);
    
    // create an instance of Account
    String name = "Jim Smith";
    Account account = new Account(name, "_secret");
    
    // persist the account object to the database
    accountDao.create(account);
    
    // retrieve the account
    Account account2 = accountDao.queryForId(name);
    // show its password
    System.out.println("Account: " + account2.getPassword());
    
    // close the connection source
    connectionSource.close();

# ChangeLog Release Notes

See the [ChangeLog.txt file](src/main/javadoc/doc-files/changelog.txt).
