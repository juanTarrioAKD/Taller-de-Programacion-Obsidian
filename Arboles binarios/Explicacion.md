
**. Arboles binarios de busqueda:**
	Se le llama arbol binario de busqueda se deben cumplir 2 condiciones:
		. Debe tener un metodo de ordenamiento, ya sea por la edad, notas, etc.
		en caso de no estar oredenado va a ser una arbol binario, pero no un arbol binario de busqueda.
	Ejemplo arbol binario de busqueda:

![[Pasted image 20251026130937.png]]

. Como se ve en la imagen todos los hijos izquierdos de la raiz (15) son menores a la misma y los derechos son mayores. Esto tambien depende de como se van leyendo los datos a la hora de la carga del arbol, dependiendo el orden puede quedar de 1 forma o otra. En este caso la raiz (el primer valor que se leyo) fue 15 por lo tanto quedo equilibrado al venir 3 valores menores y 3 valores mayores.

**. Caracteristicas:**

. Es una estructura de datos jerarquica (no lineal), homogenea y dinamica
### 🌳 Estructura Jerárquica (No Lineal)

Esto se refiere a cómo se organizan y conectan los datos.

- **No Lineal:** Es lo opuesto a una estructura lineal como un **array (vector)** o una **lista enlazada**. En una estructura lineal, cada elemento tiene un "siguiente" y (a veces) un "anterior". Los datos están en fila, uno después del otro.
    
- **Jerárquica:** En un árbol, los datos no están en fila, sino organizados por **niveles**. Hay un nodo principal (la **raíz**) y de él "cuelgan" sus "hijos" (child nodes). A su vez, esos hijos pueden tener sus propios hijos, creando una relación de "padre-hijo". Es una estructura que representa niveles de dependencia, como un organigrama de una empresa o un árbol genealógico.
    

> En resumen: **No lineal** significa que un nodo puede estar conectado a varios nodos (dos, en un árbol binario), no solo al "siguiente". **Jerárquico** significa que estas conexiones crean niveles y una relación de dependencia desde la raíz hacia las hojas.

---
### 2. 🧬 Homogénea

Esto se refiere al **tipo** de datos que almacena la estructura.

- **Homogéneo** significa que **todos los elementos** (en este caso, todos los nodos) que componen el árbol son del **mismo tipo**.
    
- Por ejemplo, si estás programando un árbol en un lenguaje como Java, C++ o Python, defines una **clase** o **struct** llamada `Nodo`. Todos los nodos del árbol serán una instancia de esa misma clase `Nodo`. Cada nodo tendrá la misma estructura interna (por ejemplo: un campo para el `valor`, un puntero al `hijoIzquierdo` y un puntero al `hijoDerecho`).
    
- Lo opuesto sería una estructura **heterogénea** (como una lista en Python) donde en una posición puedes guardar un número, en otra un texto y en otra un objeto diferente. En un árbol (generalmente), todos los nodos son del mismo tipo.
    

> En resumen: **Homogénea** significa que todos los nodos del árbol obedecen a la misma "plantilla" o tipo de dato.

---
### 3. 💧 Dinámica

Esto se refiere a cómo la estructura maneja la **memoria**.

- **Dinámica** significa que el tamaño de la estructura (la cantidad de nodos) **puede crecer o reducirse durante la ejecución** del programa.
    
- Cuando quieres agregar un nuevo elemento (un nuevo nodo), el programa pide (asigna) un nuevo bloque de memoria para ese nodo. Cuando quieres eliminar un nodo, el programa libera ese bloque de memoria.
    
- Lo opuesto es una estructura **estática**, como un array simple. Cuando declaras un array (ej. `int miArray[100]`), reservas sus 100 espacios en memoria desde el principio, y no puedes agregar el elemento 101 sin crear un array completamente nuevo.
    

> En resumen: **Dinámica** significa que el árbol usa la memoria "a demanda", pidiendo solo la que necesita y liberando la que ya no usa, sin un tamaño máximo fijo predefinido (más allá de la memoria total del sistema).

