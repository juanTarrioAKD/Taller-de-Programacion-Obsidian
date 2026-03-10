
4- Realice un programa en el que 4 robots mueven de a una todas las flores de la esquina (10,10) a la esquina (11,11). Para ello, cada robot que toma una flor de la esquina (10,10) la deposita en la esquina (11,11) y luego retorna a su esquina inicial. Cada robot que finaliza (o, sea, que detecta que la esquina (10,10) se ha vaciado) deberá avisar al robot coordinador que ha finalizado. Cuando todos los robots finalizaron, el robot coordinador deberá informar qué robot finalizó último y a continuación deberá recolectar todas las flores de la esquina (11,11).
El robot coordinador inicia en la esquina (1,1).
Los robots inician en las esquinas (9,9) (9,10) (9,11) y (9,12).

b- Implemente una variante en la cual los robots luego de tomar cada flor de la esquina (10,10) vuelvan a su esquina inicial, pasen a la esquina (11,11) a depositarla y finalmente vuelvan a la esquina inicial.

c- Analizar:
- ¿Cuál de las 2 soluciones maximiza la concurrencia?
- ¿Se podría resolver este problema sin que los robots deban regresar a su esquina inicial?

```ruby
programa ejercicio4
procesos
  proceso repartirId
  comenzar
    EnviarMensaje(1, r1)
    EnviarMensaje(2, r2)
    EnviarMensaje(3, r3)
    EnviarMensaje(4, r4)
  fin
  
  proceso mover_flor (E ca: numero; E av: numero)
  comenzar
    BloquearEsquina(11,11)
    Pos(11,11)
    depositarFlor
    Pos(av,ca)
    LiberarEsquina(11,11)
  fin

areas
  inicio: AreaC (9,9,9,12)
  inicioCor: AreaP (1,1,1,1)
  zonaDeposito: AreaP (11,11,11,11)
  zonaJuntar: AreaP(10,10,10,10)
  
robots
  robot Coordinador
  variables
    ganador:numero
  comenzar
    repartirId
    repetir 4
      RecibirMensaje(ganador,*)
    Informar('el ganador es: ',ganador)
    Pos(11,11)
    mientras(HayFlorEnLaEsquina)
      tomarFlor
  fin
  
  robot juntador
  variables
    seguir:boolean
    av,ca,id:numero
  comenzar
    ca:=PosCa
    av:=PosAv
    seguir:=true
    RecibirMensaje(id,coordinador)
    mientras seguir
      BloquearEsquina(10,10)
      Pos(10,10)
      si HayFlorEnLaEsquina
        tomarFlor
        si HayFlorEnLaEsquina
          seguir:=true
        sino 
          seguir:=false
      sino
        seguir:=false
      Pos(av,ca)
      LiberarEsquina(10,10)
      si HayFlorEnLaBolsa
        mover_flor(av,ca)
    EnviarMensaje(id,coordinador)
  fin
    
variables  
  r1:juntador
  r2:juntador
  r3:juntador
  r4:juntador
  coordinador:Coordinador
  
comenzar
  AsignarArea(r1, inicio)
  AsignarArea(r2, inicio)
  AsignarArea(r3, inicio)
  AsignarArea(r4, inicio)
  AsignarArea(coordinador, inicioCor)
  AsignarArea(r1, zonaDeposito)
  AsignarArea(r2, zonaDeposito)
  AsignarArea(r3, zonaDeposito)
  AsignarArea(r4, zonaDeposito)
  AsignarArea(coordinador, zonaDeposito)
  AsignarArea(r1, zonaJunta)
  AsignarArea(r2, zonaJunta)
  AsignarArea(r3, zonaJunta)
  AsignarArea(r4, zonaJunta)
  Iniciar(r1,9,9)
  Iniciar(r2,9,10)
  Iniciar(r3,9,11)
  Iniciar(r4,9,12)
  Iniciar(coordinador,1,1)
fin
```
no compila, no se porque.

### c.

La concurrencia la máxima la segunda opción, ya que el proceso de bloquear y moverse a la esquina 11,11 tendría que estar dentro del bloquear esquina de la 10,10
poniendo líneas extra que mantienen bloqueada la esquina impidiendo el paso de otros robots.