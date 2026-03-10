a. Un módulo recursivo que permita leer una secuencia de caracteres terminada en punto, los almacene en un vector con dimensión física igual a 10 y retorne el vector.

````Pascal
program Ejercicio1a;

const
	dimF = 10;

type
	Tvector = array [1..dimF] of char;
	
	Tlist = ^nodo;
	
	nodo = record
		dato : char;
		sig : Tlist;
	end;
	
	//solucion asumiendo que tengo una lista de caracters.
	procedure cargarcaracteresV1 (var caracteres: Tvector; pri: Tlist; actual: integer) ;
	begin
		if (pri^.dato <> '.') and (actual < dimF) then begin
			cargarCaracteresV1(caracteres,pri^.sig,actual+1);
			caracteres[actual] := pri^.dato;
		end;
	end;		
	
	//solucion leyendo caracteres desde consola.
	procedure cargarCaracteresV2 (var caracteres:Tvector; actual:integer);
	var
		c:char;
	begin
		writeln('ingrese un caracter:');
		readln(c);
		if ( c <> '.') and (actual < dimF) then begin
			cargarCaracteresV2(caracteres,actual+1);
			caracteres[actual] := c;
		end;
	end;			
	
	procedure imprimir (caracteres:Tvector);
	var
		i:integer;
	begin
		for i:= 1 to dimF do begin
			writeln(caracteres[i]);
		end;
	end;

var 
	caracteres:Tvector;
	actual:integer;

BEGIN
	actual:=1;
	cargarCaracteresV2(caracteres,actual);
	imprimir(caracteres);
END.

````
