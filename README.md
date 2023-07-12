# principios-SOLID
<img src="https://brandslogos.com/wp-content/uploads/images/large/java-logo-1.png" alt="image" width="250" height="250">

#### Los cinco principios SOLID en Spring Boot: 

### S => Single Responsability Principle (SRP) 
Principio de Responsabilidad Unica: Establece que una clase debe tener una única responsabilidad y solo debe haber una razón para que cambie. podemos ejemplificar este principio dividiendo nuestras clases en módulos y asegurándonos de que cada uno tenga una responsabilidad específica.
````
public class ServicioUsuario
{
    public void crearUsuario(Usuario usuario)
    {
        // crear un usuario
    }

    public void eliminarUsuario(Usuario usuario)
    {
        // eliminar un usuario
    }
}

public class ControladorUsuario {
    private ServicioUsuario servicioUsuario;
    // inyección dependencia

    public void crearUsuario(Usuario usuario)
    {
        servicioUsuario.crearUsuario(usuario);
    }

    public void eliminarUsuario(Usuario usuario)
    {
        servicioUsuario.eliminarUsuario(usuario);
    }
}

````

### O => Open/Closed Principle (OCP) 
Principio Abierto / Cerrado: Establece que las entidades del software deben estar abiertas para la extensión pero cerradas para la modificación. Podemos aplicar este principio utilizando interfaces y la inyección de dependencias para permitir la extensión de funcionalidades sin modificar el código existente.
````
public interface ProveedorPago 
{
    void procesarPago(Orden orden);
}

public class ProveedorPagoTarjetaCredito implements ProveedorPago 
{
    public void procesarPago(Orden orden) 
    {
        // procesar el pago con tarjeta
    }
}

public class ProveedorPagoPayPal implements ProveedorPago 
{
    public void procesarPago(Orden orden) 
    {
        // procesar pago con PayPal
    }
}
````

### L => Liskov Substitution Principle (LSP) 
Principio de Sustitución de Liskov: Establece que los objetos de un programa deben ser reemplazables por instancias de sus subtipos sin alterar la corrección del programa. Esto nos lleva a que las clases derivadas deben poder usarse en lugar de las clases base sin cambiar el comportamiento esperado.
````
public interface Figura
{
    double calcularArea();
}

public class Rectangulo implements Figura
{
    private double ancho;
    private double altura;
    // calcularArea()
}

public class Cuadrado implements Figura
{
    private double lado;
    // calcularArea()
}
````

### I => Interface Segretation Principle (ISP) 
Principio de Segregación de Interfaces: Establece que ninguna clase debe depender de interfaces que no utiliza por completo. Se puede aplicar este principio creando interfaces específicas para cada cliente y evitando interfaces genéricas que puedan obligar a implementar métodos innecesarios.
````
public interface RepositorioUsuario
{
    void guardar(Usuario usuario);
    void eliminar(Usuario usuario);
    Usuario buscarPorId(Long id);
}

public interface RepositorioBusquedaUsuario
{
    List<Usuario> buscar(String palabraClave);
}
````

### D => Dependency Inversion Principle (DIP) 
Principio de Inversión de Dependencias: Establece que los módulos de alto nivel no deben depender de módulos de bajo nivel, ambos deben depender de abstracciones. Se puede ejemplificar utilizando la inyección de dependencias y programando contra interfaces en lugar de implementaciones concretas.
````
public interface ServicioNotificacion
{
    void enviarNotificacion(String mensaje);
}

public class ServicioNotificacionEmail implements ServicioNotificacion
{
    public void enviarNotificacion(String mensaje)
    {
        // enviar una notificación por correo electrónico
    }
}

public class ServicioNotificacionSMS implements ServicioNotificacion
{
    public void enviarNotificacion(String mensaje)
    {
        // enviar una notificación de SMS
    }
}

public class ClienteNotificacion
{
    private ServicioNotificacion servicioNotificacion;

    // inyección de dependencia ServicioNotificacion

    public void notificarUsuario(String mensaje)
    {
        servicioNotificacion.enviarNotificacion(mensaje);
    }
}
````
