# Step 3 - Run your image as a container

* [Official Source](https://docs.docker.com/language/java/run-containers/)

<!---->

* [x] Run your "petclinic" docker based on the image created in the previous step.
  * [x] We should access to your application using the http standard port.

```
docker run --publish 8080:8080 java-spring:version1.0.dev
```

Result expected:

{% hint style="info" %}
Linux user, change ^ by ' to execute multi lines commands.
{% endhint %}

```
[INPUT]
curl --request GET ^
--url http://localhost/actuator/health ^
--header 'content-type: application/json'

[OUTPUT]
{"status":"UP"}

//disregard the message curl: (6) Could not resolve host: application
```

* [x] List all Dockers currently running on your local environment. Observe the port forwarding for your "petclinic" docker.

```
[INPUT]
docker ps

[OUTPUT]
CONTAINER ID  IMAGE                        COMMAND                  CREATED         STATUS         PORTS                  NAMES 
6515fbfeda95  java-spring:version1.0.dev   "./mvnw spring-boot:…"   6 minutes ago   Up 6 minutes   0.0.0.0:8080->8080/ tcpmodest_buck


```

* [x] Stop your "petclinic" docker

```
[INPUT]
docker stop 6515fbfeda95 

[OUTPUT]
---
```

* [x] Rename your docker as "petclinic-app"

<!---->

* [Official doc](https://docs.docker.com/engine/reference/commandline/rename/)

```
[INPUT]
 docker rename modest_buck  petclinic-app

[OUTPUT]
6515fbfeda95   java-spring:version1.0.dev   "./mvnw spring-boot:…"   18 minutes ago   Exited (143) 5 minutes ago      petclinic-app
```

* [x] Restart your docker using the new name

```
[INPUT]
docker start petclinic-app

[OUTPUT]
petclinic-app
```

* [x] Display all running dockers with this output format

<!---->

* [Official doc](https://docs.docker.com/config/formatting/)

Result expected:

```
IMAGE                              PORTS.                  NAMES
eclipse-petclinic:version1.0.dev   0.0.0.0:80->8080/tcp.   petclinic-server
```

```
[INPUT]
docker ps --format "table {{.Image}}\t{{.Ports}}\t{{.Names}}"

[OUTPUT]
java-spring:version1.0.dev   0.0.0.0:8080->8080/tcp   petclinic-app
```

