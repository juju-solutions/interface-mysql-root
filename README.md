# Overview

This interface layer handles communication with MySQL via the `mysql-root`
interface protocol.


# Usage

Most users should only need to use the [mysql][] interface. The `mysql-root`
interface is meant to grant elevated privileges for a MySQL user.

```bash
$ juju deploy ubuntu-devenv
$ juju deploy mysql
$ juju relate mysql:db ubuntu-devenv
```

By default, the user will not have GRANT privileges:
```
mysql> select user, grant_priv from user;
+------------------+------------+
| user             | grant_priv |
+------------------+------------+
| Eepiengah1choe1  | N          |
```

Add the MySQL `db-admin` relation:
```
$ juju relate mysql:db-admin ubuntu-devenv
```

Our user now has GRANT:
```
mysql> select user, grant_priv from user;
+------------------+------------+
| user             | grant_priv |
+------------------+------------+
| Eepiengah1choe1  | Y          |
```


[mysql]: https://github.com/johnsca/juju-relation-mysql
