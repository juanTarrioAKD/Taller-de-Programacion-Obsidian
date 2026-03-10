
1- Realice un programa con 2 robots recolectores de flores (floreros) y 2 robots recolectores de papeles (papeleros).
Los floreros comparten área y tienen 5 intentos cada uno para juntar las flores de una esquina, dentro de dicha área, elegida al azar en cada intento. Del mismo modo, los papeleros comparten área y tienen 3 intentos cada uno para juntar los papeles. En cada intento cada robot va a la esquina al azar, junta todos los elementos (flores o papeles según le corresponda) y vuelve a su esquina original. Al finalizar sus intentos cada robot debe acceder a la esquina (10, 10) y depositar los elementos recogidos de a uno.
- Área de floreros: (1,1) a (5, 10)
- Área de papeleros: (6, 1) a (10, 9)
- Esquinas de inicio de floreros: (6,10) y (7,10)
- Esquinas de inicio de papeleros: (8,10) y (9,10)

```ruby
programa Ejercicio1
procesos
  proceso juntarPapeles(ES papeles:numero)
  comenzar
    mientras(HayPapelEnLaEsquina)
      tomarPapel
      papeles:= papeles+1
  fin
  proceso juntarFlores(ES flores:numero)
  comenzar 
    mientras(HayFlorEnLaEsquina)
      tomarFlor
      flores:=flores+1
  fin
areas
  zonaFlores: AreaPC (1,1,5,10)
  zonaPapeles: AreaPC (6,1,10,9)
  zonaDeposito: AreaP (10,10,10,10)
  zonaInicioFlores: AreaPC(6,10,7,10)
  zonaInicioPapeles: AreaPC(8,10,9,10)
  
robots
  robot tipoFlor
  variables
    flores,avenida,calle,inicioAv,inicioCa:numero
  comenzar
    inicioAv:=PosAv
    inicioCa:=PosCa
    flores:=0
    repetir 5
      Random(avenida,1,5)
      Random(calle,1,10)
      BloquearEsquina(avenida,calle)
      Pos(avenida,calle)
      juntarFlores(flores)
      Pos(inicioAv,inicioCa)
    mientras(HayFlorEnLaBolsa)
      BloquearEsquina(10,10)
      Pos(10,10)
      depositarFlor
      Pos(inicioAv,inicioCa)
      LiberarEsquina(10,10)
  fin
  robot tipoPapel
  variables
    papeles,avenida,calle,inicioAv,inicioCa:numero
  comenzar
    inicioAv:=PosAv
    inicioCa:=PosCa
    papeles:=0
    repetir 5
      Random(avenida,6,10)
      Random(calle,1,9)
      BloquearEsquina(avenida,calle)
      Pos(avenida,calle)
      juntarPapeles(papeles)
      Pos(inicioAv,inicioCa)
    mientras(HayPapelEnLaBolsa)
      BloquearEsquina(10,10)
      Pos(10,10)
      depositarPapel
      Pos(inicioAv,inicioCa)
      LiberarEsquina(10,10)
  fin
variables  
  r1:tipoFlor
  r2:tipoFlor
  r3:tipoPapel
  r4:tipoPapel
comenzar
  AsignarArea(r1, zonaFlores)
  AsignarArea(r2, zonaFlores)
  AsignarArea(r3, zonaPapeles)
  AsignarArea(r4, zonaPapeles)
  AsignarArea(r1, zonaDeposito)
  AsignarArea(r2, zonaDeposito)
  AsignarArea(r3, zonaDeposito)
  AsignarArea(r4, zonaDeposito)
  AsignarArea(r1, zonaInicioFlores)
  AsignarArea(r2, zonaInicioFlores)
  AsignarArea(r3, zonaInicioPapeles)
  AsignarArea(r4, zonaInicioPapeles)
  
  Iniciar(r1,6,10)
  Iniciar(r2,7,10)
  Iniciar(r3,8,10)
  Iniciar(r4,9,10)
fin
```