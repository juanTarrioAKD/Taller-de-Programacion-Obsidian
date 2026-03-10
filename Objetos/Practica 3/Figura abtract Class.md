
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