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
Use "Ethernet adapter Ethernet 4" IP Address or "Wireless LAN adapter Wi-Fi"

# Set environment variable
https://docs.konghq.com/deck/gateway/sensitive-data/
set DECK_PET_STORE_HOST=192.168.68.119




# Add hello-cat1 endpoint
deck gateway apply cat1-service.yml
deck gateway apply cat1-route.yml

deck gateway sync cat1.yml

curl http://localhost:8000/hello-cat1



# Use url instead of protocol, host, port, and path individually
When defining a service, the administrator provides a name and the upstream application connection information. 
The connection details can be provided in the url field as a single string, or by providing individual values for protocol, host, port, and path individually.




# Kong Service Resource URI Validation Error
https://github.com/Kong/kong/issues/6125
Include ${route.id} in upstream URL you can use template variables in the service's url field

Indeed "$" is part of reserved as part of sub-delims, but the path rule includes segment and segment-nz, which include pchar, which includes sub-delims explicitly.

Long story short, all characters from the sub-delims list above need to be added as valid to our path validator!



https://pskim.medium.com/url-rewriting-in-kong-b887d65ca072

https://docs.konghq.com/hub/kong-inc/request-transformer
https://docs.konghq.com/hub/kong-inc/request-transformer-advanced/




# Intellij Exploring the HTTP request syntax
https://www.jetbrains.com/help/idea/exploring-http-syntax.html



# Kong Gateway debug requests
https://docs.konghq.com/gateway/latest/production/debug-request/