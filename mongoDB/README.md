docker run -d -p 27017:27017 -v /media/db:/data/db -p 28017:28017 --name mongodb tgwin/mongodb mongod --rest --httpinterface --auth

db.createUser(
   {
       user: "tgwin", 
       pwd: "Tmg0415!", 
       roles:["root"]
   })


   use test
db.createUser(
   {
     user: "inventory",
     pwd: "ram3teMeye",
     roles: [ "readWrite", "dbAdmin" ]
   }
);