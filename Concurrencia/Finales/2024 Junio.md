
![[Imagen8.png]]

```ruby
programa ejercicio4
areas
  cancha: AreaPC (1,1,5,5)
  zonaArbitro: AreaP (6,5,6,5)
  zonaEquipo1: AreaPC (6,1,6,2)
  zonaEquipo2: AreaPC (6,3,6,4)
  
robots
  robot Escondedor
  variables
    avAct,caAct,av,ca:numero
    flores:boolean
  comenzar
    avAct:=PosAv
    caAct:=PosCa
    RecibirMensaje(flores,arbitro)
    si flores
      repetir 2
        tomarFlor
    sino 
      repetir 2
        tomarPapel
    repetir 2
      Random(av,1,5)
      Random(ca,1,5)
      si flores
        BloquearEsquina(av,ca)
        Pos(av,ca)
        depositarFlor
      sino
        BloquearEsquina(av,ca)
        Pos(av,ca)
        depositarPapel
      Pos(avAct,caAct)
      LiberarEsquina(av,ca)
    si flores  
      EnviarMensaje(V,buscadorEquipo2)
    sino
      EnviarMensaje(V,buscadorEquipo1)
  fin
  
  robot Buscador
  variables
    avAct,caAct,av,ca,cant:numero
    flores,seguir:boolean
  comenzar
    avAct:=PosAv
    caAct:=PosCa
    RecibirMensaje(flores,arbitro)
    si flores
      RecibirMensaje(seguir,escondedorEquipo2)
    sino
      RecibirMensaje(seguir,escondedorEquipo1)
    mientras (seguir)
      Random(av,1,5)
      Random(ca,1,5) 
      si flores
        BloquearEsquina(av,ca)
        Pos(av,ca)
        si HayPapelEnLaEsquina
          tomarPapel
          cant:=cant+1
      sino
        BloquearEsquina(av,ca)
        Pos(av,ca)
        si HayFlorEnLaEsquina
          tomarFlor
          cant := cant + 1
      Pos(avAct,caAct)
      LiberarEsquina(av,ca)
      si cant = 2
        EnviarMensaje(V,arbitro)
        EnviarMensaje(flores,arbitro)
        seguir:=F
      sino 
        EnviarMensaje(F,arbitro)
        EnviarMensaje(flores,arbitro)
        RecibirMensaje(seguir,arbitro)
  fin
  
  robot Arbitro
  variables
    noTermino,equipoFlores,gano:boolean
    equipo:numero
  comenzar
    EnviarMensaje(V,buscadorEquipo1)
    EnviarMensaje(F,buscadorEquipo2)
    EnviarMensaje(V,escondedorEquipo1)
    EnviarMensaje(F,escondedorEquipo2)
    noTermino:=V
    mientras (noTermino)
      RecibirMensaje(gano,*)
      RecibirMensaje(equipoFlores,*)
      si gano
        si equipoFlores
          EnviarMensaje(F,buscadorEquipo2)
          equipo:=1
          Informar(equipo)
        sino
          EnviarMensaje(F,buscadorEquipo1)
          equipo:=2
          Informar(equipo)
        noTermino:=F
      sino
        si equipoFlores
          EnviarMensaje(V,buscadorEquipo1)
        sino
          EnviarMensaje(V,buscadorEquipo2)
  fin     

variables  
  buscadorEquipo1:Buscador
  buscadorEquipo2:Buscador
  escondedorEquipo1:Escondedor
  escondedorEquipo2:Escondedor
  arbitro:Arbitro
comenzar
  AsignarArea(buscadorEquipo1,cancha)
  AsignarArea(buscadorEquipo2,cancha)
  AsignarArea(escondedorEquipo1,cancha)
  AsignarArea(escondedorEquipo2,cancha)
  AsignarArea(arbitro,zonaArbitro)
  AsignarArea(buscadorEquipo1,zonaEquipo1)
  AsignarArea(escondedorEquipo1,zonaEquipo1)
  AsignarArea(buscadorEquipo2,zonaEquipo2)
  AsignarArea(escondedorEquipo2,zonaEquipo2)
  
  Iniciar(buscadorEquipo1,6,1)
  Iniciar(escondedorEquipo1,6,2)
  Iniciar(buscadorEquipo2,6,3)
  Iniciar(escondedorEquipo2,6,4)
  Iniciar(arbitro,6,5)
fin
```
