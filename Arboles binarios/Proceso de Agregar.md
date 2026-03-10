
**. Codigo:**

````Pascal
procedure agregar (var a:arbol; dato:integer) // ejemplo arbol de integers
	if (a = nil) then begin
		new(a);
		a^.dato:= dato;
		a^.HI:= nil;
		a^.HD:= nil;
	end
	else begin 
		if (dato <= a^.dato) then
			agregar (a^.HI, dato)
		else
			agregar (a^.HD,dato);
	end;
end;
````

**¿Como funciona este codigo?**
	. Es un codigo facil de entender ya que utiliza lo que es la recursion, el primer if (if (a = nil)) esta para dos casos:
		. *Caso arbol vacio*: si nunca se le cargo un valor al arbol se lo inicializo en nil al principio del programa, por lo tanto entra en ese if y va a reservar un espacio en memoria y cargar el dato e inicializar sus 2 hijos en nil (por lo tanto este dato recien ingresado pasa a ser una hoja).
		. *Caso finalizo el recorrido del arbol:* Cuando se termino la busqueda recursiva, en la iteracion anterior se consulto a una hoja del arbol y esta paso como parametro a su HI o HD en nil, por lo tanto entra en la condicion del if(a=nil) y se carga el valor del dato, y si inicializan sus HI y HD como nil.
	. La condicion del else realiza lo que es el llamado recursivo y cosulta si es MENOR O IGUAL (el igual es por convencion) al dato que posee el nodo del arbol actual, y caso contrario es MAYOR. Dependiendo que condicion se cumple se envia como arbol el HI o HD del nodo acutal, esto va achicando al arbol hasta que llega a una hoja y esta envia HI o HD con el valor en nil. 