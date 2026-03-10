a. Un módulo que lea información de los finales rendidos por los alumnos de la Facultad de Informática y los almacene en una estructura de datos. La información que se lee es legajo, código de materia, fecha y nota. La lectura de los alumnos finaliza con legajo 0. La estructura generada debe ser eficiente para la búsqueda por número de legajo y para cada alumno deben guardarse los finales que rindió en una lista.

````Pascal
program Ejercicio3a;


type
	
	examen = record
		cod:integer;
		fecha:integer;
		nota:integer;
	end;
	
	Tlist = ^nodoL;
	
	nodoL = record
		dato:examen;
		sig:Tlist;
	end;
	
	alumno = record
		legajo:integer;
		finales:Tlist;
	end;
	
	Tarbol = ^nodo;
	
	nodo = record
		dato:alumno;
		hi:Tarbol;
		hd:Tarbol;
	end;

	procedure leer_examen (var a:alumno; var ex:examen);
	begin
		a.legajo:=random(100);
		ex.cod:=random(10);
		ex.fecha:=random(25)+2000;
		ex.nota:=random(10);
	end;
	
	procedure insertar_adelante (var pri:Tlist; ex:examen);
	var
		aux:Tlist;
	begin
		new(aux);
		aux^.dato:=ex;
		aux^.sig:=pri;
		pri:=aux;
	end;
	
	procedure cargar_alumnos(var a:Tarbol; alum:alumno; ex:examen);
	begin
		if (a = nil) then begin
			new(a);
			a^.dato.legajo:=alum.legajo;
			a^.dato.finales:= nil;
			insertar_adelante(a^.dato.finales, ex);
			a^.hi:=nil;
			a^.hd:=nil;
		end
		else begin
		    if (a^.dato.legajo = alum.legajo) then
				insertar_adelante(a^.dato.finales, ex)
			else begin
				if (a^.dato.legajo > alum.legajo) then 
					cargar_alumnos(a^.hi,alum,ex)
				else
					cargar_alumnos(a^.hd,alum,ex);
			end;
		end;
	end;

var 
	a:Tarbol;
	al:alumno;
	ex:examen;
	
BEGIN
	a:=nil;
	writeln('Leyendo datos de los alumnos...');
	writeln('leyendo...');
	leer_examen(al,ex);
	while (al.legajo<>0) do begin
		cargar_alumnos(a,al,ex);
		leer_examen(al,ex);
	end;
end.
	
````

### **Explicacion:**
### . 🎯 El Objetivo: Buscar por `legajo`

La función recibe el árbol (`a`), los datos del alumno (`alum`, que solo aporta el `legajo`) y el examen (`ex`) que se acaba de leer.

Usa la lógica de un Árbol Binario de Búsqueda (BST) para navegar. Compara el `alum.legajo` que buscas con el legajo del nodo actual (`a^.dato.legajo`).

---

### 2. 🚦 Las Tres Posibilidades Lógicas

El código maneja tres casos que no se superponen:

- **Caso 1: El Alumno NO Existe (`if a = nil`)**
    
    - La búsqueda recursiva llegó a un punto muerto (`nil`), lo que significa que este legajo no está en el árbol.
        
    - **Acción:** Crea un nuevo nodo (`new(a)`) para este alumno, le asigna el `alum.legajo` e inicializa su lista de finales.
        
    - Finalmente, llama a `insertar_adelante` para agregar este primer examen a la lista recién creada del alumno.
        
- **Caso 2: El Alumno SÍ Existe (`else if a^.dato.legajo = alum.legajo`)**
    
    - ¡Éxito! El legajo que buscabas coincide con el legajo del nodo actual.
        
    - **Acción:** No crea un alumno nuevo. Simplemente llama a `insertar_adelante` y agrega el `ex` (examen) a la lista `finales` que **ya existe** en este nodo.
        
- **Caso 3: Seguir Buscando (`else if ...` y `else`)**
    
    - El legajo no coincide con el nodo actual y tampoco es `nil`, por lo que el alumno _podría_ estar más abajo.
        
    - **Acción:** Se llama a sí misma (recursión) para continuar la búsqueda:
        
        - Si el legajo buscado es **menor**, se va por la izquierda (`a^.hi`).
            
        - Si el legajo buscado es **mayor**, se va por la derecha (`a^.hd`).
            

---

En resumen, el módulo **baja por el árbol** buscando el legajo. Si lo **encuentra**, agrega el examen a su lista. Si **llega a un `nil`**, crea al alumno en ese lugar y le agrega el examen.