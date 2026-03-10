
![[Imagen5.png]]

```pascal
program 2025_junio;

var
	Paquete=record
		cod:integer;
		dni_emisor:integer;
		dni_receptor:integer;
		cant:integer;
		peso:double;
	end;
	
	Reg_arbol=record
		dni:integer;
		cant_paquetes:integer;
		peso_total:double;
	end;
	
	nodo=record
		dato:Reg_arbol;
		hi:Arbol;
		hd:Arbol;
	end;
	
	Arbol=^nodo
	
	nodoList=record
		dni:int;
		sig:Tlist;
	end;
	
	Tlist=^nodoList;
	
	procedure leer_paquete(var p:Paquete);
	begin
		readln(p.cod);
		readln(p.dni_emisor);
		readnl(p.dni_receptor);
		readln(p.cant);
		readln(p.peso);
	end;
	
	procedure cargar_arbol (var a:Arbol,p:Paquete);
	var
	begin
		if (a==nil) then begin
			new(a);
			a^.dato.dni:=p.dni_emisor;
			a^.dato.cant_paquetes:=1;
			a^.dato.peso_total:=p.peso;
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
			if (a^.dato.dni<p.dni_emisor) then cargar_arbol(a^.hd,p)
			else begin
				if (a^.dato.dni>p.dni_emisor) then cargar_arbol(a^.hi,p)
				else begin
					a^.dato.cant_paquetes++;
					a^.dato.peso_total+=p.peso;
				end;
			end;
		end;
	end;

	procedure insertar_atras (var ult:Tlist,var pri:Tlist, dato:integer);
	var
		aux:Tlist;
	begin
		if(pri=nil) then begin
			new(aux);
			aux^.dato:=dato;
			aux^.sig:=nil;
			pri:=aux;
			ult:=aux;
		end
		else begin
			new(aux);
			aux^.dato:=num;
			aux^.sig:=nil;
			ult^.sig:=aux;
			ult:=aux;
		end;
	end;

	procedure buscar_paquetes(var a:Arbol,num:integer,var ult:Tlist, var pri:Tlist);
	var
	begin
		if (a<>nil) then begin
			buscar_paquetes(a^.hi,num);
			if (a^.dato.cant_paquetes<num) then insertar_atras(ult,pri,a^.dato.dni);
			buscar_paquetes(a^.hd,num);
		end;
	end;	

	procedure buscar_dni (var a:Arbol,num:integer,var result:Reg_arbol);
	begin
		if(a==nil) then begin
			result.dni:=-1;
		else begin
			if (a^.dato.dni>num) then buscar_dni(a^.hi,num);
			else begin
				if (a^.dato.dni<num) then buscar_dni(a^.hd,num);
				else result:=a^.dato;
			end;
		end;
	end;

var
	p:Paquete;
	a:Arbol;
	num:integer;
	pri:Tlist;
	ult:Tlist;
	
BEGIN
	a:=nil;
	pri:=nil;
	ult:=nil;
	leer_paquete(p);
	while (p.cod<>0) do
		cargar_arbol(a,p);
		leer_paquete(p);
	end;
	readl(num);
	buscar_paquetes(a,num,ult,pri);
	buscar_dni(a,num,r);
END.
```