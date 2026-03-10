a. Implemente un módulo que genere aleatoriamente información de ventas de un comercio.
Para cada venta generar código de producto, fecha y cantidad de unidades vendidas. Finalizar
con el código de producto 0. Un producto puede estar en más de una venta. Se pide:
i. Generar y retornar un árbol binario de búsqueda de ventas ordenado por código de
producto. Los códigos repetidos van a la derecha.
ii. Generar y retornar otro árbol binario de búsqueda de productos vendidos ordenado por
código de producto. Cada nodo del árbol debe contener el código de producto y la
cantidad total de unidades vendidas.
iii. Generar y retornar otro árbol binario de búsqueda de productos vendidos ordenado por
código de producto. Cada nodo del árbol debe contener el código de producto y la lista de
las ventas realizadas del producto.
Nota: El módulo debe retornar TRES árboles.

````Pascal
program Ejercicio2;

uses
	SysUtils;	

type

	venta = record
		cod:integer;
		fecha:integer;
		cant:integer;
	end;
	
	// primer inciso
	Tarbol1 = ^nodo1;
	
	nodo1 = record
	 dato:venta;
	 hi:Tarbol1;
	 hd:Tarbol1;
	end;
	
	// segundo inciso
	Tarbol2 = ^nodo2;
	
	nodo2 = record
		dato:venta;
		cant:integer;
		hi:Tarbol2;
		hd:Tarbol2;
	end;
	
	// tercer inciso
	Tlist = ^nodoVenta;
	nodoVenta = record
		data:venta;
		sig:Tlist;
	end;
	
	Tarbol3 = ^nodo3;
	
	nodo3 = record
		dato:venta;
		lista_producto:Tlist;
		hi:Tarbol3;
		hd:Tarbol3;
	end;
	
	// inciso 1
	procedure cargar_arbol1 (var a:Tarbol1; v:venta);
	begin
		// caso base (arbol vacio o se encontro la hoja)
		if (a = nil) then begin
			new(a);
			a^.dato := v;
			a^.hi := nil;
			a^.hd := nil;
		end
		else begin
			if (a^.dato.cod > v.cod) then 
				cargar_arbol1(a^.hi,v)
			else
				cargar_arbol1(a^.hd,v);
		end;
	end;
	
	
	procedure imprimir_arbol1 (a:Tarbol1);
	begin
		if (a <> nil) then begin
			imprimir_arbol1(a^.hi);
			writeln('Cod: ', a^.dato.cod, '  | Year: ',a^.dato.fecha, ' | Cant: ', a^.dato.cant);
			imprimir_arbol1(a^.hd);
		end
	end;
	
	
	// inciso 2
	procedure cargar_arbol2 (var a:Tarbol2; v:venta);
	begin
		if (a = nil) then begin
			new(a);
			a^.dato:=v;
			a^.cant:=1;
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
			if (a^.dato.cod = v.cod) then begin
				a^.cant+=1;
			end
			else begin
				if (a^.dato.cod > v.cod) then
					cargar_arbol2(a^.hi,v)
				else
					cargar_arbol2(a^.hd,v);
			end;
		end;
	end;
	
	procedure imprimir_arbol2 (var a:Tarbol2);
	begin
		if (a<>nil) then begin
			imprimir_arbol2(a^.hi);
			writeln('Cod: ', a^.dato.cod, '  | Year: ',a^.dato.fecha, ' | Cant: ', a^.cant);
			imprimir_arbol2(a^.hd);
		end;
	end;
	
	
	// inciso 3
	procedure insertar_adelante(var pri:Tlist; v:venta);
	var
		aux:Tlist;
	begin
		new(aux);
		aux^.data:=v;
		aux^.sig:=pri;
		pri:=aux;
	end;
	
	procedure cargar_arbol3 (var a:Tarbol3; v:venta);
	begin
		if (a=nil) then begin
			new(a);
			a^.dato:=v;
			a^.lista_producto:=nil;
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
			if (a^.dato.cod=v.cod) then 
				insertar_adelante(a^.lista_producto,v)
			else begin
				if	(a^.dato.cod > v.cod) then
					cargar_arbol3(a^.hi,v)
				else
					cargar_arbol3(a^.hd,v);
			end;
		end;
	end;
	
	procedure imprimir_arbol3 (a:Tarbol3);
	begin
		if (a<>nil) then begin
			imprimir_arbol3(a^.hi);
			writeln('Cod: ', a^.dato.cod, '  | Year: ',a^.dato.fecha);
			imprimir_arbol3(a^.hd);
		end;
	end;
	
var 
	a1:Tarbol1;
	a2:Tarbol2;
	a3:Tarbol3;
	v:venta;

BEGIN
	a1:=nil;
	v.cod:=random(101);
	v.fecha:=random(25)+2000;
	v.cant:= random(100) + 1;
	while (v.cod<>0) do begin
		cargar_arbol1(a1,v);
		v.cod:=random(101);
		v.fecha:=random(25)+2000;
		v.cant:= random(100) + 1;
	end;
	imprimir_arbol1(a1);
	writeln('fin arbol 1');
	writeln('------------------------------------------');
	a2:=nil;
	v.cod:=random(101);
	v.fecha:=random(25)+2000;
	v.cant:= random(100) + 1;
	while (v.cod<>0) do begin
		cargar_arbol2(a2,v);
		v.cod:=random(101);
		v.fecha:=random(25)+2000;
		v.cant:= random(100) + 1;
	end;
	imprimir_arbol2(a2);
	writeln('fin arbol 2');
	writeln('------------------------------------------');
	a3:=nil;
	v.cod:=random(101);
	v.fecha:=random(25)+2000;
	v.cant:= random(100) + 1;
	while (v.cod<>0) do begin
		cargar_arbol3(a3,v);
		v.cod:=random(101);
		v.fecha:=random(25)+2000;
		v.cant:= random(100) + 1;
	end;
	imprimir_arbol3(a3);
END.
````

### **Explicacion:** 
   En el primer inciso se busca que realices 1 arbol que acepta repetidos pero los agrega duplicados en el arbol, si entran 4 ventas con el codigo '067' se van a encontrar como nodos o hojas dentro del arbol 4 veces.
   En el segundo inciso se busca solucionar el tema de los duplicados con un contador de cantidad dentro del registro. En este caso si el codigo es igual se incrementa en 1 el contador de apariciones.
   En el tercer inciso se busca manejar de otra forma los duplicados, se maneja una lista dentro del registro la cual se va agregando las apariciones de las ventas en esa lista.  

