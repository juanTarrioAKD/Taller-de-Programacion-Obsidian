b. Implemente un módulo que reciba el árbol generado en i. y una fecha y retorne la cantidad total de productos vendidos en la fecha recibida.

````Pascal
function contar_productos (a:Tarbol1;year:integer): integer;
	var
		total:integer;
	begin
		total:=0;
		if (a=nil) then
			contar_productos:=0
		else begin
			total:=total+contar_productos(a^.hi,year);
			total:=total+contar_productos(a^.hd,year);
			if (a^.dato.fecha = year) then 
				contar_productos:=total+1
			else	
				contar_productos:=total;
		end;
	end;
````

### **Explicacion:**

1. **Caso Base (`if a = nil`):** Si el nodo es `nil` (un subárbol vacío), retorna `0`. Esto es perfecto, es el punto de parada de la recursión.
    
2. **Llamada Izquierda (`contar_productos(a^.hi)`):** "Baja" por completo a la izquierda y pregunta: "¿Cuántos productos que coinciden hay en todo mi subárbol izquierdo?". El resultado se guarda en `total`.
    
3. **Llamada Derecha (`contar_productos(a^.hd)`):** "Baja" por completo a la derecha y pregunta: "¿Cuántos productos que coinciden hay en todo mi subárbol derecho?". El resultado se _suma_ al `total` que ya tenías.
    
4. **Procesar el Nodo Actual:** En este punto, `total` contiene la suma de todos los hallazgos en _ambos_ hijos. Ahora solo falta revisar el nodo actual:
    
    - Si `(a^.dato.fecha = year)`, el nodo actual coincide. Retornas `total + 1`.
        
    - Si no coincide, simplemente retornas el `total` (la suma de los hijos).
        

El resultado "sube" por la recursión y te da la suma total.