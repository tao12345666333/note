+++
title = "MongoDB Security"
draft = true
date = "2017-02-20T23:13:31+08:00"

+++


# 认证

* SCRAM-SHA-1 (default password authorization mechanism)

    `mongod --auth`

    ```yaml
    security:
      authorization: 'enabled'
    ```

* X.509
* LDAP
* Kerberos

# 授权
