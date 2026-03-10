
4- Sobre un nuevo programa, modifique el ejercicio anterior para considerar que:
a) Durante el proceso de inscripción se pida a cada persona sus datos (nombre, DNI, edad) y el día en que se quiere presentar al casting. La persona debe ser inscripta en ese día, en el siguiente turno disponible. En caso de no existir un turno en ese día, informe la situación. La inscripción finaliza al llegar una persona con nombre “ZZZ” o al cubrirse los 40 cupos de casting.
Una vez finalizada la inscripción:
b) Informar para cada día: la cantidad de inscriptos al casting ese día y el nombre de la persona a entrevistar en cada turno asignado.


```java
public class Ejercicio4 {
    public static void main(String[] args){
        Persona [][] casting = new Persona [5][8];
        int cupos=40;
        boolean seguir_participantes=true; boolean seguir_turno; boolean seguir;
        Persona participante;
        String nombre; int edad; int dni;
        int dia=-1; int turno=-1;
        System.out.println("--- Comienza Carga de Participantes ---");
        System.out.println("...");
        while (cupos>0&&(seguir_participantes)){
            System.out.println("Ingrese su nombre:");
            nombre=Lector.leerString();
            if (nombre.equals("ZZZ")) seguir_participantes=false;
            else{
                System.out.println("Ingrese su dni:");
                dni=Lector.leerInt();
                System.out.println("Ingrese su edad:");
                edad=Lector.leerInt();
                System.out.println("Ingrese el dia que quiere asistir:");
                seguir_turno=true;
                while(seguir_turno){
                    dia=Lector.leerInt();
                    if ((dia>4)||(dia<1)) System.out.println("Ingrese un dia valido (dias del 1 al 5)");
                    else seguir_turno=false;
                }
                System.out.println("Ingrese el turno al que quiere asistir:");
                seguir_turno=true;
                while(seguir_turno){
                    turno=Lector.leerInt();
                    if ((turno>8)||(turno<1)) System.out.println("Ingrese un turno valido (turnos del 1 al 8)");
                    else seguir_turno=false;
                }
                participante=new Persona(nombre,dni,edad);
                seguir=true;
                while (seguir){
                    if (casting[dia-1][turno-1]==null){
                        casting[dia-1][turno-1]=participante;
                        seguir=false;
                        System.out.println("Ha sido registrado en el dia: "+dia+" en el turno: "+turno);
                    }
                    else{
                        if (turno<8) turno++;
                        else {
                            if (dia<5) dia++;
                            else System.out.println("No hay turnos disponibles, lo sentimos.");
                        }
                    }
                }
                if (seguir) {
                    casting[dia-1][turno-1]=participante;  
                    System.out.println("Ha sido registrado en el dia: "+dia+" en el turno: "+turno);
                }
            }
        }
        System.out.println("--- Fin Carga de Participantes ---");
        for (int i=0; i<5; i++){
            for (int j=0; j<8; j++){
                if(casting[i][j]!=null) System.out.println(casting[i][j].toString());
            }
        }
    }
}

```