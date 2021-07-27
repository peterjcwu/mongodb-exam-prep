# Enable Auth and Create  the First User

## Enable Auth

For enabling mongodb authentication, append the <code>--auth</code> option behind the mongod.

``` bash
mongod --auth
```

Any DB operation will fail due to the non-authorized on amdin error 

## Create the First User

At the admin database with localhost, you could create the first user, thanks to localhost exception. 

```javascript
> db.createUser({
    user: '<username>',
    pwd: '<password>',
    roles: {role: 'userAdminAnyDatabase'},
    db: 'admin'
})
```

But if ther is already any user existed in the admin db, the localhost exception will not apply.

## Authenticate the User

You could authenticate the user in the console

```bash
$ mongo admin -u <username> -p <password>
$ mongo -u <useranme> -p <password> --authticationDatabase=admin
```

Remember to assign the admin database while trying to logging, because the default db is the **test** db and will causing to authentication fail.

You could also authenticate the user in the MongoDB shell

```javascript
> db.auth(<username>, <password>)
>
> db.system.users.find()
```

For a shared server. The user infroamtions are stored in the **configuration servers**.

If you would like to disable the localhost excption, you need to<code>  --setParameter enableLocalHostAuthBypass=false</code> in the mongod option.