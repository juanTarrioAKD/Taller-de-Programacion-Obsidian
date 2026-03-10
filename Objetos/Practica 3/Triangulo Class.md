
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