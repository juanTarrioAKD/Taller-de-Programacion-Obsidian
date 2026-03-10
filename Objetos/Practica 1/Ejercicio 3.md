
3- Escriba un programa que defina una matriz de enteros de tamaño 5x5. Inicialice
la matriz con números aleatorios entre 0 y 30.
Luego realice las siguientes operaciones:
- Mostrar el contenido de la matriz en consola.
- Calcular e informar la suma de los elementos de la fila 1
- Generar un vector de 5 posiciones donde cada posición j contiene la suma
de los elementos de la columna j de la matriz. Luego, imprima el vector.
- Leer un valor entero e indicar si se encuentra o no en la matriz. En caso de
encontrarse indique su ubicación (fila y columna) en caso contrario
imprima “No se encontró el elemento”.

````Java
public class Ejercicio3 {
    public static void main(String[] args) {
        // TODO code application logic here
        int [][] matriz = new int [5][5];
        int total_fila1 = 0;
        int [] vector = new int [5];
        for (int i=0; i<5; i++){
            System.out.println("fila: "+i);
            for (int j=0; j<5; j++){
                matriz[i][j]=GeneradorAleatorio.generarInt(30);
                System.out.println(matriz[i][j]);
                if (i==1){
                    total_fila1+=matriz[i][j];
                }
                vector[j]+=matriz[i][j];
            }
        }
        System.out.println("--- Fin carga del matriz ---");
        System.out.println("Comenzando calculo del total de la fila 1..");
        System.out.println("El total de la fila 1 es: "+total_fila1);
        System.out.println("--- Fin total de fila 1 ---");
        System.out.println("Comenzando modulo de impresion del vector...");
        for (int i=0; i<5; i++){
            System.out.println(vector[i]);
        }
        System.out.println("--- Fin impresion del vector ---");
        System.out.println("Ingrese numero a buscar en la matriz: ");
        int num_buscar = Lector.leerInt();
        boolean encontro=false;
        for (int i=0; i<5; i++){
            for (int j=0; j<5; j++){
                if (matriz[i][j]==num_buscar){
                    System.out.println("Se ha encontrado el valor en la matriz");
                    System.out.println("Fila: " + i + "Columna" + j);
                    encontro=true;
                }
            }
        }
        if (!encontro){
            System.out.println("No se ha encontrado el valor en la matriz");
        }
    } 
}
````