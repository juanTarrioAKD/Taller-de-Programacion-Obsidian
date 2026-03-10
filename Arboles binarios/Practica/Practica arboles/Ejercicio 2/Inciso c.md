
c. Implemente un módulo que reciba el árbol generado en ii. y retorne el código de producto con mayor cantidad total de unidades vendidas.

````Pascal
procedure cantidad_maxima (a:Tarbol2; var cod_max:integer; var cant_max:integer);
	begin
		if (a<>nil) then begin
			cantidad_maxima(a^.hi,cod_max,cant_max);
			cantidad_maxima(a^.hd,cod_max,cant_max);
			if (cant_max < a^.cant) then begin
				cod_max:=a^.dato.cod;
				cant_max:=a^.cant;
			end;
		end;
	end;	
````

### **Explicacion:**
1. **Parámetros `var`:** La clave de todo son los parámetros `var cod_max` y `var cant_max`. Estos actúan como una "memoria global". Cuando una llamada recursiva (incluso una muy profunda) modifica `cant_max`, todas las demás llamadas ven ese cambio.
    
2. **Caso Base (`if a <> nil`):**  se aseguran de que todo el código solo se ejecute si el nodo actual (`a`) no es `nil`. Si es `nil` (una rama vacía), la función simplemente termina y no hace nada.
    
3. **La "Bajada" (Recursión):**
    
    - `cantidad_maxima(a^.hi, ...)`: Primero, la función se llama a sí misma y "baja" por toda la rama izquierda hasta llegar al fondo.
        
    - `cantidad_maxima(a^.hd, ...)`: Luego, hace lo mismo por toda la rama derecha.
        
4. **La "Subida" (La Acción):**
    
    - `if (cant_max < a^.cant) ...`: Esta es la parte más importante. Se ejecuta **después** de haber revisado a los dos hijos (en el "viaje de vuelta").
        
    - Compara la cantidad del nodo actual (`a^.cant`) con el máximo que se ha encontrado hasta ahora en todo el árbol (`cant_max`).
        
    - Si la cantidad del nodo actual es mayor, actualiza las variables `var` (`cant_max` y `cod_max`) para que guarden este nuevo máximo.
        

En resumen: El procedimiento "baja" hasta el fondo del árbol y, mientras "sube" de vuelta a la raíz, va comparando cada nodo con el máximo encontrado hasta ese momento, actualizándolo si es necesario.

---

c. Implemente un módulo que reciba el árbol generado en iii. y retorne el código de producto con mayor cantidad de ventas.


````Pascal
function contar_nodos (pri:Tlist):integer;
	var
		cont:integer;
	begin
		cont:=0;
		while(pri<>nil) do begin
			cont:=cont+1;
			pri:=pri^.sig;
		end;
		contar_nodos:=cont;
	end;
	
	procedure cantidad_maxima2 (a:Tarbol3; var cant_max:integer; var cod_max:integer);
	var
		cant:integer;
	begin
		if(a<>nil) then begin
			cantidad_maxima2(a^.hi,cant_max,cod_max);
			cantidad_maxima2(a^.hd,cant_max,cod_max);
			cant:=contar_nodos(a^.lista_producto);
			if(cant>cant_max) then begin
				cant_max:=cant;
				cod_max:=a^.dato.cod;
			end;
		end;
	end;
````

*Obs:* igual al C anterior pero con un contador de nodos de las listas.