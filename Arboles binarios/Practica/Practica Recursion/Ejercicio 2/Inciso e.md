
e. Un módulo recursivo que permita leer una secuencia de caracteres terminada en punto y retorne una lista con los caracteres leídos.

````Pascal
program Ejercicio1e;

type
	Tlist = ^nodo;
	
	nodo = record
		dato : char;
		sig : Tlist;
	end;
	
procedure leerConLista (var pri:Tlist);
	var
		aux:Tlist;
		c:char;
	begin
		writeln('ingrese un caracter:');
		readln(c);
		if (c<>'.') then begin
			new(aux);
			aux^.dato:=c;
			aux^.sig:=nil;
			pri:=aux;
			leerConLista(pri^.sig);
		end;
	end;

procedure imprimirLista (pri:Tlist);
	begin
		while (pri <> nil) do begin
			writeln(pri^.dato);
			pri:=pri^.sig;
		end;
	end;
	
var 
	pri:Tlist;

BEGIN
	leerConLista(pri);
	imprimirLista(pri);
END.
````