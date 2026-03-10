1- Se dispone de la clase Persona (en la carpeta tema2). Un objeto persona puede crearse
sin valores iniciales o enviando en el mensaje de creación el nombre, DNI y edad (en ese
orden). Un objeto persona responde a los siguientes mensajes:
getNombre() retorna el nombre (String) de la persona
getDNI() retorna el dni (int) de la persona
getEdad() retorna la edad (int) de la persona
setNombre(X) modifica el nombre de la persona al “String” pasado por parámetro (X)
setDNI(X) modifica el DNI de la persona al “int” pasado por parámetro (X)
setEdad(X) modifica la edad de la persona al “int” pasado por parámetro (X)
toString() retorna un String que representa al objeto. Ej: “Mi nombre es Mauro, mi

DNI es 11203737 y tengo 70 años”

Realice un programa que cree un objeto persona con datos leídos desde teclado. Luego
muestre en consola la representación de ese objeto en formato String.

### Main: 

````Java
public class Ejercicio1 {
    public static void main(String[] args){
        Persona humano = new Persona("Juan Tarrio",46193318,21);
        System.out.println(humano.toString());
    }
}
````

---
### Persona:

````Java
public class Persona {
    private String _nombre;
    private long _dni;
    private int _edad;
    
    // Constructores
    public Persona (){
        
    } 
    
    public Persona (String Anombre, long Adni, int Aedad){
        this._nombre=Anombre;
        this._dni=Adni;
        this._edad=Aedad;
    }
    
    // Getters and Setters
    public String getNombre(){
        return this._nombre;
    }
    
    public long getDni(){
        return this._dni;
    }
    
    public int getEdad(){
        return this._edad;
    }
    
    public void setNombre (String Anombre){
        this._nombre=Anombre;
    }
    
    public void setDni (long Adni){
        this._dni=Adni;
    }
    
    public void setEdad (int Aedad){
        this._edad=Aedad;
    }
    
    // Metodo ToString
    public String toString (){
        return("Mi nombre es "+this.getNombre()+", mi DNI es "+this.getDni()+" y tengo "+this.getEdad()+" años.");
    }
}
````

