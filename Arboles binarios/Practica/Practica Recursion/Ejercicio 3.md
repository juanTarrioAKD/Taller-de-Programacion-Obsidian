
3.- Implementar un programa que invoque a los siguientes módulos.
	a. Un módulo recursivo que retorne un vector de 20 números enteros “random” mayores a 300
	y menores a 1550 (incluidos ambos).
	b. Un módulo que reciba el vector generado en a) y lo retorne ordenado. (Utilizar lo realizado
	en la práctica anterior)
	c. Un módulo que realice una búsqueda dicotómica en el vector, utilizando el siguiente
	encabezado:
	Procedure busquedaDicotomica (v: vector; ini,fin: indice; dato:integer; var pos: indice);
	Nota: El parámetro “pos” debe retornar la posición del dato o -1 si el dato no se encuentra
	en el vector.


````Pascal
program Ejercicio3;

const
	dimF=20;

type
	Tvector = array [1..dimF] of integer;
	

	procedure cargarVector (var vec:Tvector; actual:integer);
	begin
		if (actual <= dimF) then begin
			vec[actual]:=random(1251)+300;
			cargarVector(vec,actual+1);
		end;
	end;

	procedure imprimir (vec:Tvector);
	var
		i:integer;
	begin
		for i:= 1 to dimF do begin
			writeln(vec[i]);
		end;
	end;


var
	vec:Tvector;
	actual:integer;
BEGIN
	randomize;
	actual:=1;
	cargarVector(vec,actual);
	imprimir(vec);
END.
````