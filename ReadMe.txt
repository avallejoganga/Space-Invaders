El juego en sí no está hecho realmente para jugarlo, sé que está mal diseñado,
pero es solo para mostrar algo que haya programado yo desde 0.

El mayor reto del juego es imitar las limitaciones técnicas de la época, la que más
problemas me ha dado ha sido sin duda la de hacer que las líneas se muevan independientemente
unas de las otras, pero que se muevan por turnos de intervalos iguales.

Mi planteamiento para hacerlo ha sido tener una clase que sea el propio alienigena, tener una clase
que sean las Líneas, que contienen un array de aliens, y que el Game Manager tenga una array de
lineas. Los aliens tienen un método para moverse ellos mismos una cantidad de espacio determinada, las
lineas tienen un método que llaman a ese método a la vez para todos los aliens, y el Game Manager tiene 
un método que acepta un integro que empieza en 0 al principio del programa. 
El Game Manager al iniciarsecomienza ese método con el integro 0, lo que hace que llame a la array de lineas,
el index 0, y esta hacesu método de mover todos los aliens, al integro se le suma 1, y el método se llama a 
sí mismo con un espaciode tiempo determinado, esta vez llamando a la siguiente y así hasta llegar al final. 
Cuando (integro > numeroDeLineas -1) vuelve a pasar a 0, y así se repite el proceso sucesivamente

Otro problema que tuve es hacer que todos los aliens bajaran a la vez cuando solo uno de ellos llegara al borde.
Lo primero fue darle un método al propio alien para que baje y a la vez cambie de dirección.  
Para ello lo que hice fue poner un booleano a la clase Alien que comprobaba si habia llegadoa uno de los bordes, 
cuando era true, cambia un booleano en la linea, que cambia un booleano en la invasión, que cambia un booleano
en todas las líneas. 
Entonces la invasión hace un ciclo de MoveLines, y las lineas comprueban si está este booleano
activado, si está activado, en lugar de decirle a los Aliens que se muevan, les dice que caigan hacía abajo

Y por último necesitaba hacer que los Alien dispararan. Esto lo hacen con dos métodos elegidos aleatoriamente. Uno
hace que dispare el alien más cercano al jugador, y el otro hace que dispare un alien random. Ambos métodos siguen la
misma lógica, solo que a la hora de elegir quien dispara en uno está marcado el Alien y en el otro es aleatorio.

Obviamente empezamos poniendole un método al propio alien para que dispare. Para elegir quien dispara hay que organizar
a los aliens por columnas en lugar de por lineas, ya que siempre atacan los aliens que estén en la linea más baja, es decir,
el primero de cada columna. Eso quiere decir que hay que coger al primer alien de cada fila, y entonces tenemos una columna
después el segundo alien de cada fila y así sucesivamente. Para esto basta con hacer un for dentro de un for, el primer for
coge el index del puesto del alien, y el segundo for itera en cada fila.

Entonces cogemos la columna que vaya a disparar, comprobamos el index más bajo de esa columna, es decir, el alien de la fila
más baja, y disparamos. Para que las arrays nunca se salgan de index o estén nulas, lo que hacemos es al matar un alien, lo
desactivamos, pero no lo eliminamos por completo. Y la columna al disparar detecta si esta activo o no, si está inactivo entoces
pasa al siguiente alien de esa misma columna.

El resto del proceso fue mucho más directo de hacer, por eso no explicaré todo, ya que fue programación mucho más básica que no
necesitó ser planeada de antemano


 