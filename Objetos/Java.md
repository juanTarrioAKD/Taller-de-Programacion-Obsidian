
### **Puntos importantes de java:**

Las aplicaciones en Java, no necesitan compilarse varias veces dependendiendo ni del sistema operativo ni de la arquitectura.
En java se genera un codigo.java
ejemplo:

````Java
public class HolaMundoApp {
	public static void main (string[] args){
		system.out.printl("hola mundo!");
	}
}
````

Este archivo es un .java, ya que no se compilo.
Luego de compilarlo con el comipador javac (java compilator) se va generar un archivo bytecode como .class. Esta extencion .class se puede correr en cualquier lugar tanto en linux como en windows.

**Plataforma Java:**
- *Plataforma de desarrolo:* (JDK: java development kit) incluye compilador, depurador, generador de documentacion, etc.
- *Plataforma de ejecucion:* (JRE: java runtime enviroment) incluye componentes requeridas para ejecutar aplicaciones Java, entre ellas la JVM (java vitrual machine). Esta JVM funciona como un entorno virtual, el cual hace que no importa en donde se este ejecutando el codigo ya que va a traducir las instrucciones entre el codigo java y el sistema operativo.
