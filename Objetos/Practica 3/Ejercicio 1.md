
1-A- Definir una clase para representar triángulos. Un triángulo se caracteriza por el
tamaño de sus 3 lados (double), el color de relleno (String) y el color de línea (String).
Provea un constructor que reciba todos los datos necesarios para iniciar el objeto.
Provea métodos para:
- Devolver/modificar el valor de cada uno de sus atributos (métodos get y set)
- Calcular el perímetro y devolverlo (método calcularPerimetro)
- Calcular el área y devolverla (método calcularArea)
B- Realizar un programa que instancie un triángulo, le cargue información leída desde teclado e informe en consola el perímetro y el área.
NOTA: Calcular el área con la fórmula Área = s(s − a)(s − b)(s − c) , donde a, b y c
son los lados y s = . La función raíz cuadrada es Math.sqrt(#) a+b+c.

### main.
 
```java
public class Ejercicio1 {
    public static void main(String[] args){
        Triangulo triangulo;
        double lado1;double lado2;double lado3;
        String colorRelleno; String colorLinea;
        System.out.println("--- Ingrese los datos del triangulo ---");
        System.out.println("Ingrese los 3 lados: ");
        lado1=Lector.leerDouble();
        lado2=Lector.leerDouble();
        lado3=Lector.leerDouble();
        System.out.println("ingrese el color de la linea del triangulo: ");
        colorRelleno=Lector.leerString();
        System.out.println("ingrese el color del relleno: ");
        colorLinea=Lector.leerString();
        triangulo=new Triangulo(lado1,lado2,lado3,colorLinea,colorRelleno);
        System.out.println("El perimetro del triangulo es: ");
        System.out.println(triangulo.getPerimetro());
        System.out.println("El area del triangulo es: ");
        System.out.println(triangulo.getArea());
        System.out.println(triangulo.toString());
    }
}
```

---
### class triangulo

```java
public class Triangulo {
    private double lado1;
    private double lado2;
    private double lado3;
    private String colorLinea;
    private String colorRelleno;
    
    public Triangulo(){
        
    }
    
    public Triangulo (double Alado1,double Alado2,double Alado3,String AcolorLinea,String AcolorRelleno){
        this.lado1=Alado1;
        this.lado2=Alado2;
        this.lado3=Alado3;
        this.colorLinea=AcolorLinea;
    }
    
    private double calcular_perimietro (){
        return this.lado1+this.lado2+this.lado3;
    }
    
    private double calcular_area (){
        return Math.sqrt((((this.lado1+this.lado2+this.lado3)/2)*(((this.lado1+this.lado2+this.lado3)/2)-this.lado1))*(((this.lado1+this.lado2+this.lado3)/2)-this.lado2))*(((this.lado1+this.lado2+this.lado3)/2)-this.lado3);
    }
    
    public double getPerimetro (){
        return this.calcular_perimietro();
    }
    
    public double getArea(){
        return this.calcular_area();
    }
    
    public String toString(){
        return "lado 1: "+this.lado1+", lado 2: "+this.lado2+", lado 3: "+this.lado3+ ", color de linea: "+this.colorLinea+", color de relleno: "+this.colorRelleno;
    }
}

```