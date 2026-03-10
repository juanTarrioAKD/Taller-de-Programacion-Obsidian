
4- Un edificio de oficinas está conformado por 8 pisos (1..8) y 4 oficinas por piso
(1..4). Realice un programa que permita informar la cantidad de personas que
concurrieron a cada oficina de cada piso. Para esto, simule la llegada de personas al edificio de la siguiente manera: a cada persona se le pide el nro. de piso y nro. de
oficina a la cual quiere concurrir. La llegada de personas finaliza al indicar un nro.
de piso 9. Al finalizar la llegada de personas, informe lo pedido.

````Java
public class Ejercicio4 {
    public static void main(String[] args) {
        int [][] edificio = new int [8][4];
        int piso = 0;
        int oficina;
        while (piso!=8){
            do{
                System.out.println("Ingrese el numero de piso al cual desea acceder:");
                piso = Lector.leerInt()-1;
                System.out.println("ingrese el numero de oficina al cual desea acceder:");
                oficina = Lector.leerInt()-1;
                if (piso > 8 || piso < 0){
                    System.out.println("El numero de piso es invalido, debe ser mayor a 0 y menor a 10");
                }
                if (oficina > 3 || oficina < 0){
                    System.out.println("El numero de piso es invalido, debe ser mayor a 0 y menor a 5");
                }
            }
            while ((piso > 8 || piso < 0)||(oficina > 3 || oficina < 0));
            System.out.println("el piso seleccionado es: "+piso);
            System.out.println("La oficina seleccionada es: "+oficina);
            if (piso!=8){
                edificio[piso][oficina]+=1;
            }
        }
        System.out.println("--- Fin acceso de personas al edificio ---");
        System.out.println("Imprimiendo cantidad de personas por oficina...");
        for (int i=0; i<8; i++){
            System.out.println("fila: "+i);
            for (int j=0; j<4; j++){
                System.out.println(edificio[i][j]);
            }
        }
    }
}
````