
u have to patch catalina.jar, as this is version number the WTP adapter looks at. It's a quite useless check, and the adapter should allow you to start the server anyway, but nobody has though of that yet.

For years and with every version of Tomcat this is always a problem.

To patch you can do the following:

cd [tomcat or tomee home]/lib
mkdir catalina
cd catalina/
unzip ../catalina.jar
vim org/apache/catalina/util/ServerInfo.properties
Make sure it looks like the following (the version numbers all need to start with 8.0):

server.info=Apache Tomcat/8.0.0
server.number=8.0.0
server.built=May 11 2016 21:49:07 UTC
Then:

jar uf ../catalina.jar org/apache/catalina/util/ServerInfo.properties
cd ..
rm -rf catalina

http://stackoverflow.com/questions/37024876/how-to-use-tomcat-8-5-x-and-tomee-7-x-with-eclipse
