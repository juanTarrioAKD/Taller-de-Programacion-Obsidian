
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