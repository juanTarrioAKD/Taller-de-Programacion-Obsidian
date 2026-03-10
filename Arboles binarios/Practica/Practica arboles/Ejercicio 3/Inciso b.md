b. Un módulo que reciba la estructura generada en a. y retorne la cantidad de alumnos con legajo impar.

````Pascal
function soy_impar (num:integer):boolean;
	begin
		if (((num mod 10)div 2) <> 0) then 
			soy_impar:=true
		else
			soy_impar:=false;
	end;

function buscar_impares (a:Tarbol):integer;
	var
		cant:integer;
	begin
		if (a<> nil) then begin
			cant:=buscar_impares(a^.hi);
			cant:=cant+buscar_impares(a^.hd);
			if (soy_impar(a^.dato.legajo)) then
				cant:=cant+1;
			buscar_impares:=cant;
		end
		else
			buscar_impares:=0;
	end;
````

### **Explicacion:**

- **Caso 1: El Caso Base (`if a = nil`)**
    
    - La recursión llega a una rama vacía (`nil`), es decir, un "hijo" que no existe.
        
    - **Acción:** No hay alumnos que contar aquí. La función **retorna 0**. Este es el punto de parada fundamental de la recursión.
        
- **Caso 2: El Nodo SÍ Existe (`else begin ... end`)**
    
    - El nodo actual (`a`) tiene un alumno, por lo que debe contarlo a él y a todos sus descendientes. Para hacer esto, sigue una lógica **Post-Orden** (Izquierda, Derecha, _luego_ Raíz):
        
    - **Paso A (Izquierda):** `cant := buscar_impares(a^.hi);`
        
        - Primero, "baja" por toda la rama izquierda y pregunta: "¿Cuántos impares hay en todo este subárbol?". El resultado (ej: 5) lo guarda en `cant`.
            
    - **Paso B (Derecha):** `cant := cant + buscar_impares(a^.hd);`
        
        - Luego, "baja" por toda la rama derecha y pregunta: "¿Cuántos impares hay _aquí_?". El resultado (ej: 3) **lo suma** al valor que ya tenía `cant` (ahora $cant = 5 + 3 = 8$).
            
    - **Paso C (Raíz/Actual):** `if (soy_impar(a^.dato.legajo)) then ...`
        
        - Una vez que tiene el total de sus dos hijos, se procesa a sí mismo. Llama a `soy_impar` (la función que revisa si el legajo es impar).
            
        - Si es impar, se suma 1 al contador (ahora $cant = 8 + 1 = 9$).
            
    - **Paso D (Retorno):** `buscar_impares := cant;`
        
        - Finalmente, la función **retorna el total acumulado** (9) a la llamada superior que estaba esperando su resultado.