
b. Un módulo que reciba el vector generado en a) e imprima el contenido del vector.

````Pascal
program Ejercicio1c;

const
	dimF = 10;

type
	Tvector = array [1..dimF] of char;
	
	Tlist = ^nodo;
	
	nodo = record
		dato : char;
		sig : Tlist;
	end;
	
	//solucion leyendo caracteres desde consola.
	procedure cargarCaracteresV2 (var caracteres:Tvector; actual:integer; var dimL:integer);
	var
		c:char;
	begin
		writeln('ingrese un caracter:');
		readln(c);
		if ( c <> '.') and (actual < dimF) then begin
			cargarCaracteresV2(caracteres,actual+1,dimL);
			caracteres[actual] := c;
			dimL:=dimL+1
		end;
	end;			
	
	procedure imprimirRecursivoPostorder (caracteres:Tvector; actual:integer; dimL:integer);
	begin
		if (actual <= dimL) then begin
			imprimirRecursivoPostorder(caracteres,actual+1,dimL);
			writeln(caracteres[actual]);
		end;
	end;
	
	procedure imprimirRecursivoPreorder (caracteres:Tvector; actual:integer; dimL:integer);
	begin
		if (actual <= dimL) then begin
			writeln(caracteres[actual]);
			imprimirRecursivoPreorder(caracteres,actual+1,dimL);
		end;
	end;

var 
	caracteres:Tvector;
	actual:integer;
	dimL:integer;

BEGIN
	dimL:=0;
	actual:=1;
	cargarCaracteresV2(caracteres,actual,dimL);
	actual:=1;
	imprimirRecursivoPreorder(caracteres,actual,dimL);
	actual:=1;
	imprimirRecursivoPostOrder(caracteres,actual,dimL);
END.

````

La unica diferencia es como van a imprimir los valores.

- **Preorden:** Primero **procesás** el elemento actual y _después_ **bajás** a la siguiente llamada recursiva. (Acción "a la ida").
    
- **Postorden:** Primero **bajás** a la siguiente llamada recursiva y _después_ (cuando esa llamada termina, "a la vuelta") **procesás** el elemento actual. (Acción "a la vuelta").