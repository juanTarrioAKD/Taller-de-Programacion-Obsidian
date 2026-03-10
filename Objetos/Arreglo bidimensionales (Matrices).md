### **Conceptos:**

- Coleccion oredenada e indexada de elementos.
- Esta estructura de datos compuesta permite acceder a cada componente utilizando dos indices (fila y columna) que permite ubicar un elemento dentro de la estructura.
- Sus elementos pueden int, double, char, bool, u otros objetos.
   
![[Imagen3.png]]

### **Caracteristicas:**

- Homogenea
- Estatica
- Indexada 
- Lineal 

### Ejemplos tipicos:
- Sala de teatro (30 filas, 20 butacas por fila).
- Clima en argentina en 1 año (23 provincias, 12 meses).
- Cartel de bingo (5 filas, 5 columnas).

### **Declaracion:**

	TipoElemento [][] nombreVariable;
	

````Java
int [][] tabla = new int[3][4];
int i,j;
for (i=0; i<=3; i++){
	for (j=0; j<=4; j++){
		tabla[i][j]=GeneradorAleatorio.generarInt(10);
		System.out.println(tabla[i][j]);
	}
}
````
