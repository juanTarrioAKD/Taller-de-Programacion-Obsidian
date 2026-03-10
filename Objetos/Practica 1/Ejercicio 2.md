2- Escriba un programa que lea las alturas de los 15 jugadores de un equipo de
básquet y las almacene en un vector. Luego informe:
- la altura promedio
- la cantidad de jugadores con altura por encima del promedio
NOTA: Dispone de un esqueleto para este programa en Ej02Jugadores.java

````Java
package practica.objetos;
import PaqueteLectura.Lector;
import PaqueteLectura.GeneradorAleatorio;
/**
 *
 * @author juant
 */
public class PracticaObjetos {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        double [] jugadores = new double [15];
        double total = 0;
        for (int i=0; i<15; i++){
            jugadores[i]=GeneradorAleatorio.generarDouble(3);
            System.out.println(jugadores[i]);
            total+=jugadores[i];
        }
        System.out.println("--- Fin carga del vector ---");
        System.out.println("Comenzando calculo de promedio...");
        System.out.println("El vector tiene una dimension fisica de: " + jugadores.length);
        System.out.println("El total es de: " + total);
        System.out.println(total/jugadores.length);
    } 
}
````