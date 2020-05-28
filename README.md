# microservice-metaparticle-demp


https://metaparticle.io/tutorials/java/ 

Chapter 8 

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
