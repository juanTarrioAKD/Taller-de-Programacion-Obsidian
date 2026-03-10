
### Descripcion del algoritmo:

. Dado un arreglo con una dimension logico (dimL), el algoritmo consiste en buscar el elemento minimo e intercambiarlo por el primero no ordenado.

**. Algoritmo:**

````Pascal
procedure Seleccion (var V:tVector; dimL:int);
	int i;
	int j;
	int pos;
	int aux;
	for i := 1 to dimL-1 do begin
		pos:=i;
		for j := i+1 to dimL-1 do begin
			if (vec[J] > vec[pos]) then
				pos:=j;
			end;
		aux:= vec[i];
		vec[i]:=vec[pos];
		vec[pos]:= aux;

````
***

**Explicacion del algoritmo:**
	. Porque un doble for?: Este algoritmo se basa en recorrer todo el algortimo(el primer for) y en cada iteracion volver a recorrerlo para encontrar el minimo y luego hacer el intercambio(el segundo for).
	. Porque se utiliza aux?: Se utiliza la variable aux ya que sin una variable auxiliar es imposible hacer el intercambio sin perder algun dato en el proceso 
	Ejemplo sin aux:
````Pascal
		vec[i]:= vec[pos];   // se perdio el valor del vec[i]
		vec[pos]:= vec[i];   // el valor de vec[i] es igual al de vec[pos]
````
***
	. Que pasa si en ninguna iteracion del for se cumple la condicion del if?: 
	Si en ninguna iteracion del segundo for se cumple la condicion del if indica que el elemento en la poscicion "i" ya esta ordenado, pero este algoritmo no sabe identificar eso por lo tanto lo que pasa en esa ocasion es:
	. No va a modificar el valor de pos, en pos va a quedar el valor inicial que se le dio antes del segundo for (pos=i), el segundo for va a terminar de ejecutarse y nunca va a cumplirse la condicion del if, al salir del for lo que va a ser la zona de intercambio es:
````Pascal
// EJEMPLO EN QUE VEC[i] = 5, pos = 1, i = 1
	aux:=vec[i];       // aux=5
	vec[i]:=vec[pos];  // vec[1]=5
	vec[pos]:=aux;     // vec[1]=5
// como se ve se le asigna a la misma posicion el mismo valor, por lo tanto funciona para los elementos que estan ordenados pero es incesesaria este intercambio ya que esta ordenado. (solucion algoritmo de incersion)
````

**. Orden N^2:**
	El algoritmo de selección tiene orden cuadrático ya que, por cada iteración del primer bucle (`for` externo), se ejecuta el segundo bucle (`for` interno).  
	En la primera iteración (i = 1), el segundo bucle realiza **dimL - 1** comparaciones.  
	En la segunda iteración (i = 2), realiza **dimL - 2**, y así sucesivamente, hasta que queda una sola comparación.  
	Por lo tanto, el orden de complejidad del algoritmo es **O(n²)**.

**. Iteraciones:**
	Itera dimL-1 veces el primer for, ya que va desde 1 hasta dimL-1 ya que en la ultima iteracion el vector ya esta ordenado. Por lo tanto no es necesario realizar esa iteracion.