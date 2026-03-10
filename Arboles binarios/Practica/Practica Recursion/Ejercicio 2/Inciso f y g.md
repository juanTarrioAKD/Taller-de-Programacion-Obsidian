
f. Un módulo recursivo que reciba la lista generada en e) e imprima los valores de la lista en el mismo orden que están almacenados.

````Pascal
procedure imprimirListaConRecursionPreOrder (pri:Tlist);
	begin
		if (pri<>nil) then begin
			writeln(pri^.dato);
			imprimirListaConRecursionPreOrder(pri^.sig);
		end;
	end;
	
procedure imprimirListaConRecursionPostOrder (pri:Tlist);
	begin
		if (pri<>nil) then begin
			imprimirListaConRecursionPostOrder(pri^.sig);
			writeln(pri^.dato);
		end;
	end;
````

*Obs:* es el mismo caso que el inciso c, la diferencia es como se van a leer los caracteres, si procesa y despues hace el llamado recursivo o si primero hace el llamado y despues procesa.