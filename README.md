# Metaparticle demo

Metaparticle/Package simplifies the task of building and deploying container images. Metaparticle/Package is a collection of libraries that enable programmers to build and deploy containers using code that feels familiar to them.

For more detail, check [this](https://metaparticle.io/tutorials/java/).


### Sample code
```
import static io.metaparticle.Metaparticle.Containerize;
@SpringBootApplication
public class BootDemoApplication {
    @Runtime(ports = {8080},
            replicas = 4,
            executor = "metaparticle")
    @Package(repository = "your-docker-user-goes-here",
            jarFile = "target/boot-demo-0.0.1-SNAPSHOT.jar",
            publish = true,
            verbose = true)
    public static void main(String[] args) {
        Containerize(() ->  SpringApplication.run(BootDemoApplication.
        class, args));
} }
@RestController
class HelloController {
    @GetMapping("/")
    public String hello(HttpServletRequest request) {
        System.out.printf("[%s]%n", request.getRequestURL());
        return String.format("Hello containers [%s] from %s",
                request.getRequestURL(), System.getenv("HOSTNAME"));
} }
```

Happy Reading !!!
