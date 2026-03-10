
```java
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
```