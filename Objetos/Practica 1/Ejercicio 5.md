
5- El dueño de un restaurante entrevista a cinco clientes y les pide que califiquen
(con puntaje de 1 a 10) los siguientes aspectos: (0) Atención al cliente (1) Calidad
de la comida (2) Precio (3) Ambiente.
Escriba un programa que lea desde teclado las calificaciones de los cinco clientes
para cada uno de los aspectos y almacene la información en una estructura. Luego
imprima la calificación promedio obtenida por cada aspecto.

````Java
public class Ejercicio5 {
    public static void main(String[] args){
        double [][] calificaciones = new double [5][4];
        double [] promedios = new double [5];
        for (int i=0; i<5; i++){
            System.out.println("Ingrese las notas de: "+ i);
            for (int j=0; j<4; j++){
                calificaciones[i][j]=Lector.leerDouble();
                promedios[i]+=calificaciones[i][j];
            }
        }
        System.out.println("--- Fin carga de notas ---");
        System.out.println("comenzando calculo de promedios...");
        for (int i=0; i<4; i++){
            promedios[i]=promedios[i]/promedios.length;
            System.out.println(promedios[i]);
        }
    }
}
````

