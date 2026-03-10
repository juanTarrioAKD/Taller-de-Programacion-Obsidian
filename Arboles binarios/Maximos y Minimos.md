
### **. Codigo Minimo:**

````Pascal
function buscarNodoMinimo (a:arbol);
	if (a^.HI = nil) then
		buscarNodoMinimo:= a^.dato
	else 
		buscarNodoMinimo:= buscarNodoMinimo(a^.HI);
end;
````

**¿Como funciona esto?:**
	. Basicamente es un llamado recursivo hasta encontrar el nodo minimo "mas izquierda del arbol" ya que en ese nodo se encuentra el valor minimo. 
	. *Caso raiz sin hijo izquierdo:* 
		. Si no posee hijo izquierdo va a retornar directamente el valor que esta en la raiz por la condicion del if (a^.HI = nil) "true", retorna el resutado.
	.*Caso raiz con hijos:* 
		. En caso de poseer HI va a entrar al else, pasando como arbol su HI, hasta encontrar el nodo minimo sin HI. Cuando si cumple el if (a^.HI = nil) "true", va a retornar el resultado que va a ir subiendo a travez de los nodos el resultado que retorno el nodo minimo hasta llegar a la raiz que hace el ultimo retorno.
	.*Obs:* No se consulta si el arbol es nil, ya que se checkea en un proceso previo, de todas formas se podria consultar agregando un if (a=nil) "true" retorna un valor invalido como -9999 o 9999.

### **. Codigo Maximo:**

````Pascal
function buscarNodoMinimo (a:arbol);
	if (a^.HD = nil) then
		buscarNodoMinimo:= a^.dato
	else 
		buscarNodoMinimo:= buscarNodoMinimo(a^.HD);
end;
````

*Misma explicacion y codigo que el minimo pero en vez de HI consulta por HD*
