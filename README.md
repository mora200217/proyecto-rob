# Proyecto Robótica 
Proyecto de automatización de tarea de Pick & place entre espacios de trabajo con IRB140.

**Integrantes**: 
* Nelson David Ramírez Marín
* Andrés Zuleta 
* Andrés Morales Martínez 

## Declaración de problema y solución
Se busca automatizar una rutina de extracción de piezas y alistamiento en un balde originario de una banda transportadora. Aunque la rutina puede ser desarrollada manualmente, la automatización del proceso bajo el diseño de rutinas de movimiento automáticas del manipulador, reducen considerablemente el tiempo del proceso, y aumentan la repitibilidad y confiabilidad de la rutina. 

Se propone establecer en RobotStudio las trayectorias de movimiento para completar el proceso. Para la extracción de las piezas, se hará uso de una ventosa neumática controlada por una electroválvula digital. Se contará con dos espacios de movimiento. Uno de preparación y uno de transporte en banda. 

La secuencia propuesta de movimiento: 
- Alistamiento del balde a la zona de preparación.
- Extracción de piezas de la estantería hacia el balde.
- Posicionamiento del balde desde la zona de preparación a la banda transportadora.

A continuacion se muestran todo el conjunto de objetos usados para el desarrollo del proyecto:

- Estanteria A  

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Estanteria%20A%20real.jpeg" width="50%"/> 
</p> 

- Banda Transportadora
  
<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Banda%20transportadora.jpeg" width="50%"/> 
</p> 

- Balde usado
  
<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Balde%20real.jpeg" width="50%"/> 
</p> 

- Herramienta usada y acoplada al brazo_1

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Herramienta%20utilizada%20real%20y%20acoplada_1.jpeg" width="50%"/> 
</p> 

- Herramienta usada y acoplada al brazo_2

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Herramienta%20utilizada%20real%20y%20acoplada_2.jpeg" width="50%"/> 
</p> 

- Piezas utilizadas (6)

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Piezas%20utilizadas.jpeg" width="50%"/> 
</p> 


## Diseño de Herramienta 

En este apartado se muestra la descripción, planos y fotografías del gripper diseñado y sus piezas para el proceso de alistamiento asi como de la herramienta porta ventosas creada para la tarea de alistamiento como se muestran en las siguientes figuras de esta seccion:

- Planos de la herramienta_1

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Plano%20herramienta_1.PNG" width="50%"/> 
</p>   

-Planos de la herramienta_2

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Plano%20herramienta_2.PNG" width="50%"/> 
</p> 

- Modelado herramienta completa sin gancho ni ventosa
  
<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Modelado%20herramienta%20semicompleta.jpeg" width="50%"/> 
</p> 


- Modelado herramienta completa con gancho y ventosa


<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Modelado%20herramienta%20completa%20simulacion.jpeg" width="50%"/> 
</p> 

La herramienta fue diseñada de forma que sea fácil de montar en el manipulador, la ventosa y el gancho sean acoplados y  removidos fácilmente y las orientaciones y posiciones de los TCP sean ubicados fácilmente a la hora de crear la herramienta en Robot Studio, el agujero de la ventosa se modeló siguiendo la forma de la misma, teniendo las secciones circulares y la sección hexagonal a medida para que la misma no tenga deslizamiento o juego en ninguna dirección y quede fija, el gancho se ubicó en la parte superior de la herramienta como se ve en la figura, para que la herramienta pudiera entrar en la estantería fácilmente y sin chocar con la misma. La herramienta se dividió en dos partes con corte en el diámetro de la sección de la ventosa, con un par de tornillos M3 se asegura la segunda pieza y a los laterales se cuenta con dos orificios para insertar tuercas de forma que el tornillo quede fijo y no deslice. 

## Rutina en RAPID

En primer lugar en RoboStudio se muestra el modelo de todos los elementos que intervienen en el proceso planteado, lo cual se muestra en la siguiente figura:

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Objetos_intervienen_worksapce.PNG" width="50%"/> 
</p> 



Para el desarrollo del RAPID se inicio en crear 3 workobjects, uno que seria referente al gancho_banda, otro que seria de la ventosa_estanteria y otro referente al punto en donde se dejaria la pieza en el balde para 2 configuraciones diferente dependiendo la rutina ejecutada anteriormente. De acuerdo a estos 4 workobjects se diseñaron unos Paths, 5 para ser exactos, en donde el primero llamado "Home" es referente a que precisamente todas las articulaciones del robot esten en ceros. Para el Path llamado "Path_agarrar_balde_inicio" describe la traayectoria en donde el robot se acerca al balde, lo agarra con el gancho, y lo deja en el piso. Para el Path llamdado "Path_primeras_tres" representa la trayectoria en donde la ventosa gracias a la valvula hara el proceso de succion y no succion succionando y dejando de succionar para transladar y soltar las piezas en el balde siendo estas 3 primeras posiciones los lugares de arriba, izquierda y derecha y medio a la izquierda. Para el Path  "Path_segundas_tres" describe la misma trayectoria pero para las otras 3 posiciones que son medio a la derecha, abajo izquierda y abajo derecha. Para el Path "Path_dejar_balde_final" se realiza la trayectoria en donde el balde con las piezas con recogidos nuevamente con el gancho por el robot para luego ser llevados otra vez a la banda y ser dejados alli.

"Path_agarrar_balde_inicio":

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Path_agarrar_balde_inicio.PNG" width="50%"/> 
</p> 

"Path_primeras_tres":

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Path_primeras_tres.PNG" width="50%"/> 
</p> 

 "Path_segundas_tres":

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Path_segundas_tres.PNG" width="50%"/> 
</p> 

"Path_dejar_balde_final"

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Path_dejar_balde_final.PNG" width="50%"/> 
</p> 

Estando aqui el codigo RAPID comentado sobre las caracteristicas de los Paths anteriormente mencionados en el main

<p align="center">
<img margin="auto" src="https://github.com/mora200217/proyecto-rob/blob/master/Imagenes%20proyecto%20robotica/Rapid_main.PNG" width="50%"/> 
</p> 


## Proceso de calibración y ejecución

En la realización del proyecto no hubo mayores inconvenientes relacionados a RobotStudio pero a la hora de realizar lo mismo fisicamente se generaron algunos inconvenientes relacionados al la posicion de los puntos, por lo que la calibracion hecha solo fue usar jogging en los puntos problematicos para obtener sus coordenadas y tambien como otra alternativa ir moviendo el workobject de la estanteria como los workobjects de dejar la pieza en el blade dependiendo si era para las 3 primeras primeras posiciones, o para las otras 3.


## Comparación tiempo de alistamiento manual y operación automatizada

Para este apartado se hicieron 2 procedimientos segun los indicados, primero se midio en tiempo cuanto se demoraría un integrante del grupo en ejecutar las mismas trayectorias teniendo este una velocidad constante a la del promedio de velocidades eque existen entre los puntos del robot y ademas siguiendo de cierta forma los puntos de las rutinas que hacia el robot. Teniendo como resultado que se demoraria, como se ve en el video alistamiento manual Path_primeras_tres, 37 segundos para las primeras 3 posiciones y de acuerdo al video alistamiento manual Path_segundas_tres, 28 segundos para las otras 3 posiciones 

 - Video alistamiento manual Path_primeras_tres

   * https://youtu.be/I_ztmLPLh1E

 - Video alistamiento manual Path_segundas_tres

   * https://youtu.be/c2UgFJ2A1XM

Y seguidamente se midio la velocidad que existia entre la trayectoria completa de tomar las 3 primeras piezas y luego tomar las otras 3, para ver si existe alguna variación en estos tiempos que relativamente debererian ser muy similares, teniendo como resultado que para las primeras 3 piezas se demoro 55 segundos minutos y para las otras 3 piezas se demoro 56 segundos segun lo recopilado en el video de demostracion completo de forma fisica, lo que resulta en que las rutinas de coger y dejar las piezas en el balde, en los 2 casos son muy similares a como se esperaba para el proceso.


## Demostración de funcionamiento 

Aqui se muestra el funcionamiento completo de la para las rutinas donde en el primera instancia se muestra el robot llegando a las primeras 3 posiciones y luego llegando a las otras 3 posiciones donde en cada posicion se encuentra una figura diferente, donde primero se muestra la simulación en RobotStudio de los 2 paths y luego el proceso fisico de los mismos

 - Video completo

   *

Aqui se muestra el funcionamiento completo de la para las rutinas donde en el primera instancia se muestra el robot llegando a las primeras 3 posiciones y luego llegando a las otras 3 posiciones donde en cada posicion se encuentra una figura diferente, todo en simulacion en RobotStudio

 - Simulación 3 primeras posiciones

   * https://youtu.be/wz9IZnBNGRQ

 - Simulacion 3 segundas posiciones

   * https://youtu.be/LEoH4QJWPf4
