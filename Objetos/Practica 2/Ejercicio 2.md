2- Utilizando la clase Persona. Realice un programa que almacene en un vector a lo sumo 15 personas. La información (nombre, DNI, edad) se debe generar aleatoriamente hasta obtener edad 0. Luego de almacenar la información:
- Informe la cantidad de personas mayores de 65 años.
- Muestre la representación de la persona con menor DNI.

````java
public class Ejercicio2 {
    public static void main(String[] args){
        Persona [] personas = new Persona [15];
        int cant=0;
        String nombre;
        int edad;
        int dni;
        int cant_mayores=0;
        int minimo=99;
        int pos_minimo=0;
        nombre=GeneradorAleatorio.generarString(10);
        edad=GeneradorAleatorio.generarInt(100);
        dni=GeneradorAleatorio.generarInt(50000000);
        while ((cant<personas.length)&&(edad!=0)){
            if (edad>64){
                cant_mayores+=1;
            }
            if(minimo>dni){
                minimo=dni;
                pos_minimo=cant;
            }
            personas[cant] = new Persona(nombre,dni,edad);
            nombre=GeneradorAleatorio.generarString(10);
            edad=GeneradorAleatorio.generarInt(100);
            dni=GeneradorAleatorio.generarInt(50000000);
        }
        System.out.println("--- Fin carga ---");
        System.out.println("la cantidad de personas mayores a 65 es:");
        System.out.println(cant_mayores);
        System.out.println("Iniciando busqueda de minimo...");
        System.out.println(personas[pos_minimo].toString());
    }
}
````
