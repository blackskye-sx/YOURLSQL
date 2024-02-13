
## Background

This is a fork of the original [YOURLS](https://github.com/YOURLS/YOURLS).
The goal of this fork is to rewrite the database code to make it more compatible with other databases. The defaults will be mySQL, PostgreSQL, and sqlite. But people will be able to create "extensions" that will plug into other databases like SQL Server and Oracle. 

In addition, the goal is to maintain compatibility with the existing plugins. 

Right now it's called YOURLSQL to identify the rewrite.

## DO NOT USE 

This fork is currently in alpha and it will be unuseable for the time being. 

## License

YOURLSQL will be released under the [MIT license](LICENSE).


### TO DO 


- create a file that will hold all SQL statements. The first version will be the mysql statements only. It will be expanded later to include postgresql and sqlite
- work on separating out mysql
- create "drivers" for postgres and sqlite
- ...
- ...
- ...


- rename everything from "mysql" to "ydbsql"
-- includes\class-mysql.php
-- 'mysql_version'      => yourls_get_db()->mysql_version(),
-- return yourls_sanitize_version(yourls_get_db()->mysql_version());
-- 

    public function include_db_files() {
        // Attempt to open drop-in replacement for the DB engine else default to core engine
        $file = YOURLS_USERDIR . '/db.php';
        $attempt = false;
        if(file_exists($file)) {
            $attempt = yourls_include_file_sandbox( $file );
            // Check if we have an error to display
            if ( is_string( $attempt ) ) {
                yourls_add_notice( $attempt );
            }
        }

        // Fallback to core DB engine
        if ( $attempt !== true ) {
            require_once YOURLS_INC . '/class-mysql.php';
            yourls_db_connect();
        }
    }

    public function mysql_version() {
        $version = $this->pdo->getAttribute(PDO::ATTR_SERVER_VERSION);
        return $version;
    }
