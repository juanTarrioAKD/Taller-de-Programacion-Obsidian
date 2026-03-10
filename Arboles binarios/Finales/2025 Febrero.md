

![](../Imagenes/Imagen6.png)


```Pascal
program 2025_febrero;

type
	facultad=1..17;

	estudiante=record
		nom:string;
		legajo:integer;
		id:facultad;
		promedio:double;
	end;

	nodoArbol=record
		dato:estudiante;
		hi:Arbol;
		hd:Arbol;
	end;
	
	Tarbol=^nodoArbol;
	
	Tarray=array[17]of Tarbol;
	
	procedure leerAlum(var a:estudiante);
	begin
		readln(a.nom);
		readln(a.legajo);
		readln(a.id);
		readln(a.promedio);
	end;
	
	procedure cargar_arbolLegajo (var a:Tarbol, e:estudiante);
	var
	begin
		if(a==nil) then begin
			new(a);
			a^.dato:=e;
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
			if (a^.dato.legajo>e.legajo) then cargar_arbol(a^.hi,e)
			else cargar_arbol(a^.hd,e);
		end;
	end;
	
	procedure cargar_arbolPromedio (var a:Tarbol, e:estudiante);
	var
	begin
		if(a==nil) then begin
			new(a);
			a^.dato:=e;
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
			if (a^.dato.legajo>e.promedio) then cargar_arbol(a^.hi,e)
			else cargar_arbol(a^.hd,e);
		end;
	end;
	
	procedure cargar_facultades (var facultades:Tarray, a:Tarbol);
	var
	begin
		if(a<>nil) then begin
			cargar_facultades(facultades,a^.hi);
			cargar_facultades(facultades,a^.hd);
			cargar_arbolPromedio(facultad[a^.dato.id],a^.dato);
		end;
	end;
		
	function buscar_alumno (facultades:Tarray,facultad);
	begin
		if(a==nil) then return -1
		else begin
			while (seguir) do begin
				if(facultades[facultad]^.hd<>nil) then facultades[facultad]:=facultades[facultad]^.hd
				else begin
					writeln(facultades[facultad]^.dato.nombre);
					writeln(facultades[facultad]^.dato.legajo);
					seguir:=false;
				end;
			end;
		end;
	end;
	
```
