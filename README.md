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

A continuacion se muestran las piezas utilizadas

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 
<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 
<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 
<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 
<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 
<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 


## Diseño de Herramienta 

En este apartado se muestra la descripción, planos y fotografías del gripper diseñado y sus piezas para el proceso de alistamiento asi como de la herramienta porta ventosas creada para la tarea de alistamiento como se muestran en las siguientes figuras:


<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 





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

Para este apartado se hicieron 2 procedimientos segun los indicados, primero se midio en tiempo cuanto se demoraría un integrante del grupo en ejecutar las mismas trayectorias teniendo este una velocidad constante a la del promedio de velocidades eque existen entre los puntos del robot. Teniendo como resultado que se demoraria XXXX minutos con XXX segundos.

 - Video

Y seguidamente se midio la velocidad que existia entre la trayectoria completa de tomar las 3 primeras piezas y luego tomar las otras 3, para ver si existe alguna variación en estos tiempos que relativamente debererian ser muy similares, teniendo como resultado que para las primeras 3 piezas se demoro XXX minutos con XXX segundos y para las otras 3 piezas se demoro XXX minutos con XXX segundos

 - Video

## Demostración de funcionamiento 

Aqui se muestra el funcionamiento completo de la para las rutinas donde en el primera instancia se muestra el robot llegando a las primeras 3 posiciones y luego llegando a las otras 3 posiciones donde en cada posicion se encuentra una figura diferente, todo fisicamente

 - Video

Aqui se muestra el funcionamiento completo de la para las rutinas donde en el primera instancia se muestra el robot llegando a las primeras 3 posiciones y luego llegando a las otras 3 posiciones donde en cada posicion se encuentra una figura diferente, todo en simulacion en RobotStudio

 - Video

