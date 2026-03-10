
. La declaracion de los arboles binarios es sencilla ya que no presenta manejo de vectores ni de listas para los hijos, simplemente tiene 2 punteros (1 para cada hijo).

**. Codigo:**

````Pascal
Type 
	Arbol = ^nodo
	
	nodo = record
		dato = ...;
		HI = Arbol;
		HD = Arbol;
	end;
  
var 
	a:Arbol;
````

. Su declaracion es muy parecida a una lista pero en vez de tener 1 solo siguiente, tiene 2 (HI y HD).

