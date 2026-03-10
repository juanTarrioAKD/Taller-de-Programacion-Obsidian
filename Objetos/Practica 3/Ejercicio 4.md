
4-A- Un hotel posee N habitaciones. De cada habitación conoce costo por noche, si está ocupada y, en caso de estarlo, guarda el cliente que la reservó (nombre, DNI y edad).
(i) Genere las clases necesarias. Para cada una provea métodos getters/setters adecuados.
(ii) Implemente los constructores necesarios para iniciar: los clientes a partir de nombre, DNI, edad; el hotel para N habitaciones, cada una desocupada y con costo aleatorio e/ 2000 y 8000.
(iii) Implemente en las clases que corresponda todos los métodos necesarios para:
- Ingresar un cliente C en la habitación número X. Asuma que X es válido (es decir, está en el rango 1..N) y que la habitación está libre.
- Aumentar el precio de todas las habitaciones en un monto recibido.
- Obtener la representación String del hotel, siguiendo el formato:
{Habitación 1: costo, libre u ocupada, información del cliente si está ocupada}
...
{Habitación N: costo, libre u ocupada, información del cliente si está ocupada}
B- Realice un programa que instancie un hotel, ingrese clientes en distintas habitaciones, muestre el hotel, aumente el precio de las habitaciones y vuelva a mostrar el hotel.
NOTAS: Reúse la clase Persona. Para cada método solicitado piense a qué clase debe delegar la responsabilidad de la operación.

```java
public class Ejercicio4 {
    public static void main(String[] args){
        Habitacion [] hotel = new Habitacion [30];
        int num=0; String nombre; int dni; int edad; Persona cliente;
        boolean seguir=true;
        for (int i=0; i<30; i++){
            hotel[i]=new Habitacion();
        }
        while (seguir){
          System.out.println("Ingrese la habitacion a la cual deseea acceder: ");
          num=Lector.leerInt()-1;   
          if((num<0)||(num>29)) System.out.println("Habitacion invalida (ingrese del 1 al 30)");
          else 
            if (hotel[num].getOcupada()) System.out.println("Habitacion ocupada, seleccione otra: ");
            else seguir=false;
        }
        System.out.println("Ingrese su nombre: ");
        nombre=Lector.leerString();
        System.out.println("Ingrese su dni: ");
        dni=Lector.leerInt();
        System.out.println("Ingrese su edad: ");
        edad=Lector.leerInt();
        cliente= new Persona(nombre,dni,edad);
        hotel[num].dar_alojamiento(cliente);
        System.out.println(hotel[num].toString());
    }
}
```


### class Hotal

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