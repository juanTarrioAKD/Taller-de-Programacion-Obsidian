c. Un módulo que reciba la estructura generada en a. e informe, para cada alumno, su legajo y su cantidad de finales aprobados (nota mayor o igual a 4).

````Pascal

````


---

c. Un módulo que reciba la estructura generada en a. y un valor real. Este módulo deberetornar los legajos y promedios de los alumnos cuyo promedio supera el valor ingresado.

````Pascal
procedure insertar_adelante (var pri:Tlistab; legajo:integer; prom:real);
	var
		aux:Tlistab;
	begin
		new(aux);
		aux^.dato.legajo:=legajo;
		aux^.dato.promedio:=prom;
		aux^.sig:=pri;
		pri:=aux;
	end;
	
	function consultar_promedio(pri:Tlist):real;
	var
		cant:integer;
		total:integer;
	begin
		cant:=0;
		total:=0;
		while (pri <> nil) do begin
			total:=total+pri^.dato.nota;
			cant:=cant+1;
			pri:=pri^.sig;
		end;
		consultar_promedio:=total div cant;
	end;
	
	procedure cargar_lista (var pri:Tlistab; a:Tarbol; promedio:integer);
	var
		prom:real;
	begin
		if (a <> nil) then begin
			cargar_lista(pri,a^.hi,promedio);
			cargar_lista(pri,a^.hd,promedio);
			prom:=consultar_promedio(a^.dato.finales);
		    if (prom >= promedio) then 
				insertar_adelante(pri,a^.dato.legajo,prom);
		end;
	end;
````