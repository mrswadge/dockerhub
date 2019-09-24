# Artifactory with OpenJDK
## Prerequisites
Dependent images *mrswadge/debian-base* and *mrswadge/debian-openjdk* must be created first.

## Steps
1. Spin up image with: *docker run -p 8081:8081 mrswadge/debian-artifactory-openjdk:latest*
2. Find the docker machine ip address with: *docker-machine ip*
3. Artifactory can be accessed with *http://\<docker-machine ip\>:8081*
4. Artifactory login: *admin* / *password*
