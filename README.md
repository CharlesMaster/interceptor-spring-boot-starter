# interceptor-spring-boot-starter

## Introduce
interceptor-spring-boot-starter is a demo starter to interceptor method by exlude


## How to use

- maven dependency 

```xml
        <dependency>
            <groupId>com.bad.evil</groupId>
            <artifactId>interceptor-spring-boot-starter</artifactId>
            <version>1.0.1-SNAPSHOT</version>
        </dependency>
```

- application.properties
```properties
evillog.exclude=A,B
```

- controller

```
@RestController
public class TestController {

    @Autowired
    private TakeoffService takeoffService;

    @GetMapping("/input")
    public String input(String word){
        return takeoffService.wrap(word);
    }

    @GetMapping("/A")
    @Log
    public String A(){
        return takeoffService.wrap("A");
    }

    @GetMapping("/B")
    @Log
    public String B(){
        return takeoffService.wrap("B");
    }

    @GetMapping("/C")
    @Log
    public String C(){
        return takeoffService.wrap("C");
    }

}
```
so when you curl http://localhost:8080/C
we will get log,A&B invocation will direct proceed