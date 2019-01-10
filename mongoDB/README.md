```
docker run -d -p 27017:27017 -v /media/db:/data/db -p 28017:28017 --name mongodb tgwin/mongodb mongod --rest --httpinterface --auth
```
### create admin user
```
use admin
db.createUser(
   {
       user: "tgwin", 
       pwd: "password", 
       roles:["root"]
   })

```
### Create Base User
```
user inventory
db.createUser(
   {
     user: "inventory",
     pwd: "password",
     roles: [ "readWrite", "dbAdmin" ]
   }
);
```