4.- Realizar un programa que lea números y que utilice un módulo recursivo que escriba el equivalente en binario de un número decimal. El programa termina cuando el usuario ingresa el número 0 (cero).
Ayuda: Analizando las posibilidades encontramos que: Binario (N) es N si el valor es menor a 2.
¿Cómo obtenemos los dígitos que componen al número? ¿Cómo achicamos el número para la
próxima llamada recursiva? Ejemplo: si se ingresa 23, el programa debe mostrar: 10111.

````Pascal
program Ejercicio4;
	procedure EscribirBinario(num: integer);
	begin
		// Caso Base: Si el número es 0 o 1, se imprime
		if (num < 2) then begin
			write(num);
		end
		else
		// Caso Recursivo:
		begin
		// 1. Primero "bajo" con el número achicado (N DIV 2)
		EscribirBinario(num DIV 2);
		// 2. "A la vuelta", imprimo el dígito (N MOD 2)
		write(num MOD 2); 
  end;
end;

var
	num:integer;

BEGIN
	writeln('ingrese numero:');
	readln(num);
	while (num<>999) do begin
		EscribirBinario(num);
		writeln();
		writeln('ingrese numero:');
		readln(num);
	end;
	
END.

````

El sistema binario no se basa en potencias de 10 (1, 10, 100, ...), se basa en potencias de **2** (1, 2, 4, 8, 16, ...).

Para "desarmar" un número en binario, no divides por 10, **divides por 2**.

- El **resto** (`MOD 2`) te dice si hay un **1** o **0** en la última posición (la columna del '1').
    
- El **cociente** (`DIV 2`) es "el resto del número", corrido una posición.
    

### Ejemplo: Convertir 23 (el de tu ejercicio)

Vamos a hacer exactamente lo mismo que hicimos con 123, pero dividiendo por 2.

|**División**|**Cociente (DIV 2)**|**Resto (MOD 2)**|**Dígito Binario (Posición)**|
|---|---|---|---|
|**23 / 2**|11|**1**|(Este `1` va en la columna de $2^0$, o sea, la del **1**)|
|**11 / 2**|5|**1**|(Este `1` va en la columna de $2^1$, o sea, la del **2**)|
|**5 / 2**|2|**1**|(Este `1` va en la columna de $2^2$, o sea, la del **4**)|
|**2 / 2**|1|**0**|(Este `0` va en la columna de $2^3$, o sea, la del **8**)|
|**1 / 2**|0|**1**|(Este `1` va en la columna de $2^4$, o sea, la del **16**)|

El cociente llegó a **0**, así que terminamos.

Ahora, lee los **restos** de **abajo hacia arriba**: **10111**.

- $10111 = (1 \times 16) + (0 \times 8) + (1 \times 4) + (1 \times 2) + (1 \times 1) = 16 + 4 + 2 + 1 = 23$
    

**En resumen:** `MOD 2` "arranca" el último dígito binario, y `DIV 2` te da el resto del número para seguir procesando. Por eso la recursión "postorden" funciona tan bien:

1. **"Baja"** (`DIV 2`) hasta que el número es 0.
    
2. **"A la vuelta"** (`MOD 2`), va imprimiendo los restos, desde el último que calculó (que es el primer dígito) hasta el primero que calculó (que es el último dígito).