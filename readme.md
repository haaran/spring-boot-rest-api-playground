# Todo and Hello World Rest APIs Connecting to H2 In memory database running on port 5000

Run com.in28minutes.rest.webservices.restfulwebservices.RestfulWebServicesApplication as a Java Application.


## Hello World URLS

- http://localhost:5000/hello-world

```txt
Hello World
```

- http://localhost:5000/hello-world-bean

```json
{"message":"Hello World - Changed"}
```

- http://localhost:5000/hello-world/path-variable/in28minutes

```json
{"message":"Hello World, in28minutes"}
```


## Hardcoded Service URLs

- GET - http://localhost:5000/users/in28minutes/todos

```
[
  {
    id: 1,
    username: "in28minutes",
    description: "Learn to Dance 2",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
  {
    id: 2,
    username: "in28minutes",
    description: "Learn about Microservices 2",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
  {
    id: 3,
    username: "in28minutes",
    description: "Learn about React",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
]
```

#### Retrieve a specific todo

- GET - http://localhost:5000/users/in28minutes/todos/1

```
{
  id: 1,
  username: "in28minutes",
  description: "Learn to Dance 2",
  targetDate: "2018-11-09T12:05:18.647+0000",
 : false,
}
```

#### Creating a new todo

- POST to http://localhost:5000/users/in28minutes/todos with BODY of Request given below

```
{
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2030-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Updating a new todo

- http://localhost:5000/users/in28minutes/todos/1 with BODY of Request given below

```
{
  "id": 1,
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2045-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Delete todo

- DELETE to http://localhost:5000/users/in28minutes/todos/1


## JPA Service URLs

- GET - http://localhost:5000/jpa/users/in28minutes/todos

```
[
  {
    "id": 10001,
    "username": "in28minutes",
    "description": "Learn JPA",
    "targetDate": "2019-06-27T06:30:30.696+0000",
    "done": false
  },
  {
    "id": 10002,
    "username": "in28minutes",
    "description": "Learn Data JPA",
    "targetDate": "2019-06-27T06:30:30.700+0000",
    "done": false
  },
  {
    "id": 10003,
    "username": "in28minutes",
    "description": "Learn Microservices",
    "targetDate": "2019-06-27T06:30:30.701+0000",
    "done": false
  }
]
```

#### Retrieve a specific todo

- GET - http://localhost:5000/jpa/users/in28minutes/todos/10001

```
{
  "id": 10001,
  "username": "in28minutes",
  "description": "Learn JPA",
  "targetDate": "2019-06-27T06:30:30.696+0000",
  "done": false
}
```

#### Creating a new todo

- POST to http://localhost:5000/jpa/users/in28minutes/todos with BODY of Request given below

```
{
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2030-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Updating a new todo

- http://localhost:5000/jpa/users/in28minutes/todos/10001 with BODY of Request given below

```
{
  "id": 10001,
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2045-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Delete todo

- DELETE to http://localhost:5000/jpa/users/in28minutes/todos/10001


## H2 Console

- http://localhost:5000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL


## Deploy to Heroku
- Get HEROKU_API_KEY from https://dashboard.heroku.com/account
- To eliminate Heroku CLI installation, the Maven plugin can be executed as given below:
```
 HEROKU_API_KEY=9d2ec761-5288-4161-8d43-e0d54e5ed728 mvn heroku:deploy
```
-Configure pom.xml file with following

```
<properties>
   <full-artifact-name>target/${project.artifactId}-${project.version}.jar</full-artifact-name>
</properties>
<build>
 <plugins>
  <plugin>
      <groupId>com.heroku.sdk</groupId>
      <artifactId>heroku-maven-plugin</artifactId>
      <version>1.1.1</version>
      <configuration>
          <appName>spring-boot-rest-apis</appName>
          <includeTarget>false</includeTarget>
          <includes>
              <include>${basedir}/${full-artifact-name}</include>
          </includes>
          <jdkVersion>1.8</jdkVersion>
          <processTypes>
              <web>java $JAVA_OPTS -jar ${full-artifact-name}</web>
          </processTypes>
      </configuration>
  </plugin>
 </plugins>
</build>
```
