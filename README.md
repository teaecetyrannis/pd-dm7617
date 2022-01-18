# dm7617
[read in english](https://github.com/teaecetyrannis/pd-dm7617/blob/main/README_EN.md)
<br><br>
sintetizador FM inspirado en el chip YM2612, desarrollado en [pure data](https://github.com/pure-data/pure-data)


## instalación
descargar el archivo dm7617.zip de la [última release](https://github.com/teaecetyrannis/pd-dm7617/releases), extraer y agregar la carpeta contenedora al path de pure data, luego se puede iniciar desde cualquier parche creando el objeto `[dm7617~]`
<br><br>también depende de la abstracción [adsr](https://github.com/teaecetyrannis/pd-adsr) y el objeto `[selector~]` de la librería [cyclone](https://github.com/porres/pd-cyclone), por lo que necesariamente deberán instalarse también


## funcionamiento
el sintetizador cuenta con:

 1. cuatro operadores, cada uno con control de:
	 - ganancia (0-100%)
	 - ataque (*ms*), decay (*ms*), sustain (*0-100%*) y release (*ms*)
	 - multiplicador de la frecuencia fundamental
	 - afinación (*cents*)
	 - cantidad de la lfo que se le es ruteada (*0-100%*)

	a su vez el operador 1 puede "automodular" con una copia idéntica de sí mismo (op1_self), que cuenta con su propio control de ganancia y cantidad de lfo
	
 2. una lfo con control de ganancia y frecuencia (*hz*)
 3. ocho algoritmos idénticos a los del YM2612
 4. controles para cambiar entre monofónico y polifónico, **legato**, voice-**stealing** y comportamiento del pitch **bend** (*global* aplica el bend a todas las voces de la polifonía y *last* aplica el bend sólo a la última voz activada)
 
CUIDADO:
- en modo monofónico **bend** debe estar en *global*, de lo contrario puede que el pitch bend no haga efecto
- en modo polifónico **legato** debe estar apagado, de lo contrario puede que algunas voces no suenen


## documentación, cambiar los parámetros dinámicamente y guardar el estado actual del sintetizador
en el subparche `[pd help]` dentro de dm7617~.pd se encuentra (en inglés) toda esta misma información y además se detallan sus inlets y outlets y cómo setear todos los parámetros desde fuera mediante mensajes, permitiendo un control completamente dinámico del sintetizador sin hacer uso de la interfaz
<br>gracias a esto también es posible recordar enteramente el estado del sintetizador: sólo es necesario un muy extenso mensaje que incluya todos los valores actuales para cada parámetro... por suerte esta función ya está incorporada y basta con conectar un mensaje (no es necesario que esté vacío, ya que su contenido será reemplazado) a la tercera outlet y luego enviar un mensaje `[state(` a la segunda inlet, esto escribirá en el mensaje todos los parámetros y rutas de archivos
	

## créditos
[pure data](https://github.com/pure-data/pure-data) por miller puckette y muchxs más
