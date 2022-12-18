##BUILD Image
docker build . -t keycloak

##Run Image
docker run --name keycloak -p 3000:8443 \
-e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
keycloak \
start --optimized --hostname-port=5000

##Run local image development
docker run --name keycloakLocal -p 8080:8080 \
-e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
keycloak-local \
start-dev

##Run remote image development 
docker run --name keycloakLocal -p 8080:8080 \
-e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
quay.io/keycloak/keycloak \
start-dev

##Run local image development with db credential
docker run --name keycloakLocal -p 8080:8080 \
-e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
keycloak-local \
start-dev \
--db=postgres --features=token-exchange \
--db-url=jdbc:postgresql://localhost:5432/keycloak


##Run docker-compose

docker-compose up
