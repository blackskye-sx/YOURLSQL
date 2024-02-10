
## Background

This is a fork of the original [YOURLS](https://github.com/YOURLS/YOURLS).
The goal of this fork is to rewrite the database code to make it more capatible with other databases. The defaults will be mySQL, PostgreSQL, and sqlite. But people will be able to create "extensions" that will plug into other databases like SQL Server and Oracle. 

Right now it's called YOURLSQL to identify the rewrite.

## DO NOT USE 

This fork is currently in alpha and it will be unuseable for the time being. 

## License

YOURLSQL will be released under the [MIT license](LICENSE).


### TO DO 

- rename everything from "mysql" to "ydbsql"
- create a file that will hold all SQL statements. The first version will be the mysql statements only. It will be expanded later to include postgresql and sqlite
- ...
