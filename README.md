# Installing Kong using Docker
https://docs.konghq.com/gateway/latest/install/docker/
The Kong Docker compose setup is not working!! Install it manually instead.



# Key concepts
https://docs.konghq.com/gateway/latest/key-concepts/services/



# Kong manager
http://localhost:8002/



# Install Deck
https://docs.konghq.com/deck/install/
deck diff
deck sync
deck dump
deck reset -f


# Install Petstore app
https://github.com/swagger-api/swagger-petstore

Comment out below in the jetty-maven-plugin in the pom.xml since there is not such file...
<scanTarget>src/main/resources/openapi-inflector.yaml</scanTarget>

mvn package jetty:run

http://localhost:8080/



# Deck getting started
https://docs.konghq.com/deck/get-started/


# For upstream services use IP Address instead of localhost
Else you get a "Connection refused" error in the kong-gateway Docker container Logs
Use "Ethernet adapter Ethernet 4" IP



# Add hello-cat1 endpoint
deck gateway apply cat1-service.yml
deck gateway apply cat1-route.yml

deck gateway sync cat1.yml

curl http://localhost:8000/hello-cat1
