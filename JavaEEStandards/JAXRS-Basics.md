# Basic JAX-RS
* web.xml
```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">
         
</web-app>
```
* Application
```java
import javax.ws.rs.ApplicationPath;
import javax.ws.rs.core.Application;

@ApplicationPath("/root/path")
public class MyApplication extends Application {

}
```
* REST Handler
```java
import javax.ws.rs.GET;
import javax.ws.rs.Path;

@Path(value = "/myapi")
public class MyAPI {

	@GET
	public String getDemoString() {
		return "test";
	}
}
```

#### Sub Resource
```java
@Path("/item")
public class ItemResource {
    @Context UriInfo uriInfo;
 
    @Path("content")
    public ItemContentResource getItemContentResource() {
        return new ItemContentResource();
    }
 
    @GET
    @Produces("application/xml")
        public Item get() { ... }
    }
}
 
public class ItemContentResource {
 
    @GET
    public Response get() { ... }
 
    @PUT
    @Path("{version}")
    public void put(@PathParam("version") int version,
                    @Context HttpHeaders headers,
                    byte[] in) {
        ...
    }
}

```

##### Resources
- [Jersey Docs](https://jersey.java.net/documentation/latest/jaxrs-resources.html)
