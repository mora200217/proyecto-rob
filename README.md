# Proyecto Robótica 
Proyecto de automatización de tarea de Pick & place entre espacios de trabajo con IRB140.

## Declaración de problema y solución
Se busca automatizar una rutina de extracción de piezas y alistamiento en un balde originario de una banda transportadora. Aunque la rutina puede ser desarrollada manualmente, la automatización del proceso bajo el diseño de rutinas de movimiento automáticas del manipulador, reducen considerablemente el tiempo del proceso, y aumentan la repitibilidad y confiabilidad de la rutina. 

Se propone establecer en RobotStudio las trayectorias de movimiento para completar el proceso. Para la extracción de las piezas, se hará uso de una ventosa neumática controlada por una electroválvula digital. Se contará con dos espacios de movimiento. Uno de preparación y uno de transporte en banda. 

La secuencia propuesta de movimiento: 
- Alistamiento del balde a la zona de preparación.
- Extracción de piezas de la estantería hacia el balde.
- Posicionamiento del balde desde la zona de preparación a la banda transportadora.

## Diseño de Herramienta 

## Rutina en RAPID

En primer lugar en robostudio se modelo todos los elementos que intervienen en el proceso planteado, lo cual se muestra en la siguiente figura:

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 



Para el desarrollo del RAPID se inicio en crear 3 workobjects, uno que seria referente al gancho_banda, otro que seria de la ventosa_estanteria y otro referente al punto en donde se dejaria la pieza en el balde. De acuerdo a estos 3 workobjects se diseñaron unos Paths, 5 para ser exactos, en donde el primero llamado "Home" es referente a que precisamente todas las articulaciones del robot esten en ceros. Para el Path llamado "Path_agarrar_balde_inicio" describe la traayectoria en donde el robot se acerca al balde, lo agarra con el gancho, y lo deja en el piso. Para el Path llamdado "Path_primeras_tres" representa la trayectoria en donde la ventosa gracias a la valvula hara el proceso de succion y no succion succionando y dejando de succionar para transladar y soltar las piezas en el balde siendo estas 3 primeras posiciones los lugares de arriba, izquierda y derecha y medio a la izquierda. Para el Path  "Path_segundas_tres" describe la misma trayectoria pero para las otras 3 posiciones que son medio a la derecha, abajo izquierda y abajo derecha. Para el Path "Path_dejar_balde_final" se realiza la trayectoria en donde el balde con las piezas con recogidos nuevamente con el gancho por el robot para luego ser llevados otra vez a la banda y ser dejados alli.

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 

<p align="center">
<img margin="auto" src="https://github.com/mora200217/phantom_drawer_ws/blob/master/imgs/rosgraph.png" width="50%"/> 
</p> 



## Proceso de calibración y ejecución

En la realización del proyecto no hubo mayores inconvenientes relacionados a RobotStudio pero a la hora de realizar lo mismo fisicamente se generaron algunos inconvenientes relacionados al la posicion de los puntos, por lo que la calibracion hecha solo fue usar jogging en los puntos problematicos para obtener sus coordenadas y tambien como otra alternativa ir moviendo el workobject de la estanteria.


## Comparación tiempo de alistamiento manual y operación automatizada

Para este apartado se hicieron 2 procedimientos segun los indicados, primero se midio en tiempo cuanto se demoraría un integrante del grupo en ejecutar las mismas trayectorias teniendo este una velocidad constante a la del promedio de velocidades eque existen entre los puntos del robot. Teniendo como resultado que se demoraria XXXX minutos con XXX segundos.

Y seguidamente se midio la velocidad que existia entre la trayectoria completa de tomar las 3 primeras piezas y luego tomar las otras 3, para ver si existe alguna variación en estos tiempos que relativamente debererian ser muy similares, teniendo como resultado que para las primeras 3 piezas se demoro XXX minutos con XXX segundos.


## Demostración de funcionamiento 

Aqui se muestra el funcionamiento completo de la para las rutinas donde en el primera instancia se muestra el robot llegando a las primeras 3 posiciones y luego llegando a las otras 3 posiciones donde en cada posicion se encuentra una figura diferente.

Video

