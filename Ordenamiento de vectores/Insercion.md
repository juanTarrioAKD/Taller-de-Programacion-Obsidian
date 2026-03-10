### Descripcion del algoritmo:

. Este algoritmo se basa en recorrer el vector como como si tuviera 2 elementos y en cada iteracion ir agrandando en 1 la cantidad de elementos. En cada iteracion desde la posicion 1 hasta la posicion i-1 va a estar ordenado, el nuevo elemento que es el que esta en la posicion i es el nuevo elemento que hay que insertar en el subconjunto del vector que ya esta ordenado.
Como se inserta? se va recorriendo de atras para adelante moviendo 1 posicion para atras los elementos hasta encontrar la posicion en la que va el elemento a insertar.

**. Algoritmo:**

````Pascal
procedure Insercion (var V:tVector; dimL:integer);
	int i;
	int j;
	int actual;
	for i:= 2 to dimL do begin
		actual=vec[i];
		j:=i-1;
		while (j > 0) and (v[j] > actual) do begin
			vec[j+1]:=vec[j];
			j:=j-1;
		end;
		vec[j+1]:=actual;
	end;
````

**Explicacion del algoritmo:**
	. Porque arranca desde 2?: Ya que se maneja como subconjuntos del vector y si un subconjunto solo tiene 1 solo elemento se asume que ya esta ordenado, por lo tanto no es necesaria esa iteracion. Por lo tanto se comienza desde un subconjunto con 2 elementos. Se va agrandando el vector en cada iteracion del for. Ejemplo:
	*Primera iteracion:*
		subconjunto: [5]  [1]
		luego del while: [5]  [5]  ***el while salio por la condicion j>0***
		luego de asignacion: [1]  [5] 
	*Segunda iteracion:*
		subconjunto: [1]  [5]  [3]
		luego del while: [1]  [5]  [5] ***el while sale por la condicion v[j]>actual***  
		luego de asignacion: [1]  [3]  [5]
	Asi hasta completar todas las iteraciones del for.
	. Es una mejora con respecto al ordenamiento de seleccion ya que en este algoritmo al encontrar la posicion del elemento a insertar no itera mas (se ahorra esas iteraciones inecesarias del metodo de seleccion).

**. Orden N^2:**
	El algoritmo **va tomando cada elemento** del vector y lo **inserta en su lugar correcto** dentro de la parte que ya está ordenada.  
	Para encontrar ese lugar, **compara hacia atrás** y **va moviendo** los elementos que son más grandes.
	Lo importante: cuántas veces compara y mueve
	Cada vez que el algoritmo toma un nuevo elemento:
	. Puede tener suerte y colocarlo enseguida (si ya está en orden).
	. O puede tener que compararlo con muchos elementos anteriores y moverlos (si el vector está desordenado).    
	Entonces, **la cantidad de comparaciones y movimientos depende del orden del vector**.
	En el peor caso el vector esta al reves por lo tanto por va a tener la misma cantidad de iteraciones que el metodo de ordenamiento de seleccion, teniendo un orden cuadratico.
	En el mejor caso el vector ya esta ordenado y va iterar unicamente las iteraciones del for ya que el while no se va a cumplir por la condicion de 
	vec[j] > actual, en caso de estar ordenado esta condicion va a ser falsa y no va a entrar al while, teniendo un orden lineal.
	En estos casos se asume que el orden de ejecucion es el orden del peor caso, por lo tanto se asume que el orden de ejecucion es el orden cuadratico.

|Algoritmo|Mejor caso|Peor caso|Explicación|
|---|---|---|---|
|**Selección**|🔸 **O(n²)**|🔸 **O(n²)**|Siempre recorre todo el vector con los dos bucles (el externo y el interno). Aunque esté ordenado, sigue comparando igual.|
|**Inserción**|🟢 **O(n)**|🔴 **O(n²)**|Si el vector está ordenado, el `while` nunca se ejecuta → solo pasa una vez por el `for`. Pero si está al revés, el `while` hace muchas comparaciones, igualando el número total de iteraciones del método de selección.|