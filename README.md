# principios-SOLID
<img src="https://brandslogos.com/wp-content/uploads/images/large/java-logo-1.png" alt="image" width="250" height="250">

#### Los cinco principios SOLID: 
### S => Single Responsability Principle (SRP) 
Principio de Responsabilidad Unica: Establece que una clase debe tener una única responsabilidad y solo debe haber una razón para que cambie. podemos ejemplificar este principio dividiendo nuestras clases en módulos y asegurándonos de que cada uno tenga una responsabilidad específica.

public class UserService 
{
    public void createUser(User user) 
    {
        // codigo crear usuario
    }
    public void deleteUser(User user) 
    {
        // codigo eliminar usuario
    }
}

public class UserController 
{
    private UserService userService;
    // inyección dependencia
    public void createUser(User user)
    {
        userService.createUser(user);
    }
    public void deleteUser(User user) 
    {
        userService.deleteUser(user);
    }
}

### O => Open/Closed Principle (OCP) 
Principio Abierto / Cerrado: Establece que las entidades del software deben estar abiertas para la extensión pero cerradas para la modificación. Podemos aplicar este principio utilizando interfaces y la inyección de dependencias para permitir la extensión de funcionalidades sin modificar el código existente.

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

### L => Liskov Substitution Principle (LSP) 

### I => Interface Segretation Principle (ISP) 

### D => Dependency Inversion Principle (DIP) 
