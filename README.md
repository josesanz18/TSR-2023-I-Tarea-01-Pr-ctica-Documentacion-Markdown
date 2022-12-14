# TSR-2023-I-Tarea-01-Practica-Documentacion-Markdown

## Contenido
- [Introducción](#introducción)
- [Desarrollo](#desarrollo)
- [Conclusiones](#conclusiones)
- [Autor](#autor)
- [Referencias](#referencias)

## Introducción

Esta tarea práctica es realizada con el objetivo de familiarizarnos con Markdown y podamos realizar documentación apropiada, usando encabezados, tablas, imágenes y demás recursos según sea necesario.
Para practicar la documentación se elaboró un documento introductorio a ROS.

## Desarrollo

### Clasificación de los robots móviles por configuración
En los robots móviles con ruedas se consideran las siguientes configuraciones: ackerman, triciclo clásico, tracción diferencial, skid steer, síncrona y tracción omnidireccional, las cuales dotan al robot de características y propiedades distintas respecto a la eficiencia energética, dimensiones, cargas y maniobrabilidad[^1].

### Restricciones cinemáticas
Coordenadas dependientes: Coordenadas adicionales que se utilizan para definir el sistema de manera unívoca.
Están relacionadas con las coordenadas independientes mediante las ecuaciones de **restricción cinemáticas**.
Estas restricciones son por lo general no lineales y su número es igual al número de coordenadas dependientes[^2].

### Conceptos de localización, ruta, odometría y planeación de ruta.

#### ·Localización
La localización de robots móviles autónomos consiste en determinar la posición del robot en relación a un mapa dado del entorno. El problema de la localización de un robot móvil reside en que su posición no puede ser medida directamente y debe ser inferida de datos sensoriales[^3].

#### ·Ruta
La palabra ruta proviene del francés route, que a su vez deriva del latín rupta. Se trata de un camino, carretera o vía que permite transitar desde un lugar hacia otro. En el mismo sentido, una ruta es la dirección que se toma para un propósito[^4].

#### ·Odometría
Es el estudio de la estimación de la posición de vehículos con ruedas durante la navegación.
Para realizar esta estimación se usa información sobre la rotación de las ruedas para estimar cambios en la posición a lo largo del tiempo.
Este término también se usa a veces para referirse a la distancia que ha recorrido uno de estos vehículos[^5].

#### ·Planeación de ruta
La planificación de trayectorias, por su parte, es la encargada de encontrar una ruta transitable entre una posición de origen y una posición objetivo. La planificación exige, entre otras cosas, una representación del robot y su entorno. La representación explícita de entornos amplios hace que el coste computacional y de memoria de la planificación sea alto, hasta el punto de llegar a ser intratable en un espacio de tiempo razonable. Debido a ello, se han desarrollado metodologías y algoritmos que buscan una solución de compromiso entre la optimidad de la solución y el coste computacional[^3].

### Diferencias entre sistemas holonómicos y no-honolomicos.
Una de las posibles formas de clasificar los robots es distinguiendo si son holonómicos o no. Es una distinción que está relacionada con su movilidad. Simplificando, podemos decir que robots o sistemas holonómicos son aquellos capaces de modificar su dirección instantáneamente (en esta consideración se considera masa nula), y sin necesidad de rotar previamente. Un vehículo con un sistema de dirección como el de un coche, por ejemplo, no lo es, porque para poder desplazarse en el sentido lateral tiene que realizar varias maniobras previas. Del mismo modo, un robot con 2 ruedas es no-holonómico ya que no puede moverse hacia la izquierda o la derecha. Siempre lo hace hacia delante en la dirección definida por la velocidad de sus ruedas[^6].

### Caracterización de la plataforma móvil TurtleBot3:
#### Modelo cinemático

![tb3_D](/imagenes/turtlebot3_dimension1.png)
#### Sensores y actuadores que lo integran.

![tb3](/imagenes/turtlebot3_burger_components.png)[^7]
#### Nodos y Tópicos de ROS utilizados por la plataforma Turtlebot3 y sus sensores

El nodo **/amcl** permite leer la posición inicial del robot, las coordenadas y el continuo escaneo
en la variación de su posición para ser publicada en el tópico **/particlecloud** el cual permite analizar
la variación de sus coordenadas desde la posición (0, 0, 0) y comunicarse con el computador
remotamente.

El nodo **/move_base** es necesario para el funcionamiento del robot, 
se encarga de mover el robot hacia una meta o punto final. En este nodo se asocian “topicos” o
tares que permite realizar el funcionamiento total del robot.

Este nodo recibe los datos tomados del sensor LDS unido con los datos de posicionamiento
del robot para construir la trayectoria y variar la velocidad lineal o angular del robot “turltebot 3”
mediante el uso del topic **/cmd_vel.**

El nodo **/turtlebot3_slam_gmapping** permite hacer el mapeo del robot alrededor de su
trayectoria. Este nodo recibe los valores de posicionamiento del robot permitiendo tener una
referencia del robot dentro del mapa.

El nodo **/explore_server** es el encargado de recibir el valor del punto final de la trayectoria y
convertir este valor es un valor binario. Este valor binario va ser recibido por el nodo **/move_base** 
para realizar la trayectoria desde el punto posicionado del robot hasta el punto final definido por el
usuario.

El nodo **turtlebot3_core** es el encargado de recibir los valores del tópico **/cmd_vel** y guiar el
robot a través de la trayectoria creada por el nodo move_base controlando el valor de posición,
orientación y covarianza del robot. 

Algunos Tópicos empleados son:
/tf
/initialpose
/tf_static
/scan
/explore_server/action_topics
/move_base/action_topics
/particlecloud
/odom
/map
/move_base_simple/goal
/move_base/NavfnROS/plan
/move_base/local_constmap/constmap_updates
/move_base/DWAPlannerROS/global_plan
/move_base/local_constmap/constmap
/move_base/global_constmap/constmap
/move_base/local_constmap/footprint
/move_base/action_topics
/join_states
/tf
/sensor_state
/imu[^8]

## Conclusiones

Se lograron identificar las diferentes configuraciones de los robpots móviles, como el triciclo y el ackerman. A su vez, se definieron las ecuaciones de restricción en la robótica. 
También se recavó infirmación reelevante para los robots móviles, como la localización, la ruta, la odometría y la planeación de ruta, como también la diferencia entre sistemas holonómicos y no holonómicos.
Por último, se recaudó información relevante relacionada a la plataforma de desarrollo, TurtleBot3, identificando su configuración, los nodos y tópicos más importantes que emplea, sin olvidar los sensores y actuadores que lo conforman.

## Autor

**Autor** José Manuel Sánchez Espinosa [GitHub profile](https://github.com/josesanz18)

## Referencias

[^1]: A.e: Gil. (2022, Julio 06). Robótica móvil: Qué es y sus aplicaciones.[Online]. Available: https://openwebinars.net/blog/robotica-movil-que-es-y-sus-aplicaciones/#:~:text=En%20los%20robots%20m%C3%B3viles%20con,eficiencia%20energ%C3%A9tica%2C%20dimensiones%2C%20cargas%20y 

[^2]: A. Fernández. (N.A.). Maquinas y Mecanismos.[Online]. Available: https://ocw.unican.es/pluginfile.php/2949/course/section/2799/Tema%207%20-%20Ana%CC%81lisis%20Cinema%CC%81tico%20III.pdf

[^3]: Tekniker. (N.A.). LOCALIZACIÓN Y PLANIFICACIÓN DE TRAYECTORIAS.[Online]. Available: https://www.tekniker.es/es/localizacion-y-planificacion-de-trayectorias#:~:text=La%20localizaci%C3%B3n%20de%20robots%20m%C3%B3viles,ser%20inferida%20de%20datos%20sensoriales.

[^4]: J. Delgado. (2013, Enero 13). Significado de Ruta (Definición, Concepto, Qué es).[Online]. Available: https://edukavital.blogspot.com/2013/01/definicion-de-ruta-compendio-de.html

[^5]: K. Ramírez. (N.A.). Odometría. [Odometría]. Available: http://www.kramirez.net/Robotica/Material/Presentaciones/Odometria.pdf

[^6]: electric Bricks. (2010, Septiembre 16). Sistemas holonómicos.[Online]. Available: http://blog.electricbricks.com/2010/07/sistemas-holonomicos/

[^7]: Robotis. (N.A.). TurtleBot3 2.Feature. [Online]. Available:https://emanual.robotis.com/docs/en/platform/turtlebot3/features/#specifications

[^8]: D.L. Martínez. (2019) Trabajo de grado para optar al título de Ingeniero Electrónico. [Online]. Available: https://repository.usta.edu.co/bitstream/handle/11634/18667/2019davidmartinez.pdf?sequence=1
