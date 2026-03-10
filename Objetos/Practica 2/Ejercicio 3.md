
3- Se realizará un casting para un programa de TV. El casting durará a lo sumo 5 días y en cada día se entrevistarán a 8 personas en distinto turno.
a) Simular el proceso de inscripción de personas al casting. A cada persona se le pide nombre, DNI y edad y se la debe asignar en un día y turno de la siguiente manera: las personas primero completan el primer día en turnos sucesivos, luego el segundo día y así siguiendo. La inscripción finaliza al llegar una persona con nombre “ZZZ” o al cubrirse los 40 cupos de casting.
Una vez finalizada la inscripción:
b) Informar para cada día y turno asignado, el nombre de la persona a entrevistar.
NOTA: utilizar la clase Persona. Pensar en la estructura de datos a utilizar. Para comparar Strings use el método equals.


````java
public class Ejercicio3 {
    public static void main(String[] args){
        Persona [][] casting = new Persona [5][8];
        int i=0; int j;
        boolean seguir=true;
        Persona participante;
        String nombre; int edad; int dni;
        System.out.println("--- Comienza Carga de Participantes ---");
        System.out.println("...");
        while ((i<5)&&(seguir)){
            j=0;
            while ((j<8)&&(seguir)){
                nombre=GeneradorAleatorio.generarString(3);
                if (nombre.equals("ZZZ")) seguir=false;
                else{
                    dni=GeneradorAleatorio.generarInt(50000000);
                    edad=GeneradorAleatorio.generarInt(50);
                    participante=new Persona(nombre,dni,edad);
                    casting[i][j]=participante;
                    System.out.println(participante.toString());
                    j++;
                }
            }
            i++;
        }
        System.out.println("--- Fin Carga de Participantes ---");
    }
}
````