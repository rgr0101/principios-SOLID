# principios-SOLID
<img src="https://logowik.com/content/uploads/images/731_java.jpg" alt="image" width="200" height="100">

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

### L => Liskov Substitution Principle (LSP) 

### I => Interface Segretation Principle (ISP) 

### D => Dependency Inversion Principle (DIP) 
