
```java
public class Habitacion {
    private double precio;
    private boolean ocupada;
    private Persona cliente;
    
    public Habitacion (){
        this.precio=GeneradorAleatorio.generarDouble(6000)+2000;
        this.ocupada=false;
    }
    
    public String dar_alojamiento (Persona Apersona){
        if (!ocupada){
            this.cliente=Apersona;
            this.ocupada=true;
            return "Se ha agregado correctamente a la persona";
        }
        else return "La habiatacion ya se encuentra ocupada";
    }
    
    public void liberar_habitacion(){
        this.cliente=null;
        this.ocupada=false;
    }
    
    public void aumentar_precio (double aumento){
        this.precio=this.precio+aumento;
    }
    
    public String getCliente (){
        return cliente.toString();
    }
    
    public boolean getOcupada(){
        return this.ocupada;
    }
    
    public double getPrecio(){
        return this.precio;
    }
    
    @Override
    public String toString(){
        if(this.ocupada){
            return "cliente: "+this.cliente.toString()+", el precio es: "+this.precio;
        }
        else
            return "el precio es: "+this.precio;
    }
}

```