
5-A- Definir una clase para representar círculos. Los círculos se caracterizan por su radio (double), el color de relleno (String) y el color de línea (String).
Provea un constructor que reciba todos los datos necesarios para iniciar el objeto.
Provea métodos para:
- Devolver/modificar el valor de cada uno de sus atributos (métodos get y set)
- Calcular el perímetro y devolverlo (método calcularPerimetro)
- Calcular el área y devolverla (método calcularArea)
B- Realizar un programa que instancie un círculo, le cargue información leída de teclado e informe en consola el perímetro y el área.
NOTA: la constante PI es Math.PI

```java
public class Ejercicio5 {
    public static void main(String[] args){
        Circulo circulo;
        String colorL; String colorR; double radio;
        System.out.println("Ingrese los colores del circulo: ");
        colorL=Lector.leerString();
        colorR=Lector.leerString();
        System.out.println("Ingrese el radio del circulo: ");
        radio=Lector.leerDouble();
        circulo=new Circulo(radio,colorL,colorR);
        System.out.println(circulo.calcularPerimetro());
        System.out.println(circulo.toString());
    }
}
```

---
### circulo class

```java
public class Circulo extends Figura {
    private double Radio;
    
    public Circulo (double Aradio, String aColorLinea, String aColorRelleno){
        super(aColorRelleno,aColorRelleno);
        this.Radio=Aradio;
    }
    
    public double calcularPerimetro (){
        return (Math.PI*this.Radio);
    }
    
    public double getRadio (){
        return this.Radio;
    }
    
    public void getRadio (double nuevoRadio){
        this.Radio=nuevoRadio;
    }
    
    @Override
    public String toString(){
        return super.toString()+", radio: "+this.Radio;
    }
}
```

---
### Figura Abstract Class

```java
public abstract class Figura {
    private String colorRelleno;
    private String colorLinea;
    
    public Figura (String AcolorRelleno, String AcolorLinea){
        this.colorRelleno=AcolorRelleno;
        this.colorLinea=AcolorLinea;
    }
    
    abstract double calcularPerimetro();
    
    public String getColorRelleno (){
        return this.colorRelleno;
    }
    
    public String getColorLinea (){
        return this.colorLinea;
    }
    
    public void setColorRelleno (String nuevoColor){
        this.colorRelleno=nuevoColor;
    }
    
    public void setColorLinea (String nuevoColor){
        this.colorLinea=nuevoColor;
    }
    
    @Override
    public String toString(){
        return "color linea: "+this.colorLinea+", color relleno: "+this.colorRelleno;
    }
}
```