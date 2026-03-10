d. Un módulo recursivo que permita leer una secuencia de caracteres terminada en punto y retorne la cantidad de caracteres leídos. El programa debe informar el valor retornado.


````Pascal
program Ejercicio1d;

type

function contarCaracteres (): integer;
	var
		c:char;
	begin
		writeln('ingrese caracter');
		readln(c);
		if (c <> '.') then begin
			contarCaracteres := contarCaracteres()+1;
		end
		else
			contarCaracteres := 0;
	end;
	
BEGIN
	writeln(contarCaracteres);
END.
````
