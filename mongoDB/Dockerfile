
FROM ubuntu:latest

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
RUN echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.2.list

RUN apt-get update

RUN apt-get update
RUN apt-get install -y mongodb-org


RUN mkdir -p /data/db

EXPOSE 27017
CMD ["usr/bin/mongod", "--smallfiles"]







#docker run -d -p 27017:27017 -v /media/db:/data/db -p 28017:28017 --name mongodb tgwin/mongodb mongod --rest --httpinterface --auth

#db.createUser(
#   {
#       user: "tgwin", 
#       pwd: "Tmg0415!", 
#       roles:["root"]
#   })


#   use test
#db.createUser(
#   {
#     user: "inventory",
#     pwd: "ram3teMeye",
#     roles: [ "readWrite", "dbAdmin" ]
#   }
#);