# dm7617
sintetizador FM inspirado en el chip YM2612, desarrollado en [pure data](https://github.com/pure-data/pure-data) y [camomile](https://github.com/pierreguillot/Camomile)

## instrucciones de instalación
descargar el archivo dm7617.zip de la [última release](https://github.com/teaecetyrannis/dm7617/releases/tag/v1.0) y extraerlo en la carpeta donde se encuentren los plugins vst3 (para correrlo en pd basta con ejecutar el parche dm7617.pd)

## funcionamiento
el sintetizador cuenta con:

 1. cuatro operadores, cada uno con control de:
	  - ganancia (0-100%)
	 - ataque (ms), decay (ms), sustain (0-100%) y release (ms)
	 - multiplicador de la frecuencia fundamental
	 - afinación (cents)
	 - cantidad de la lfo que se le es ruteada (0-100%)

	a su vez el operador 1 puede "automodular" con una copia idéntica de sí mismo (op1_self), que cuenta con su propio control de ganancia y cantidad de lfo
	
 2. una lfo con control de ganancia y frecuencia (hz)
 3. ocho algoritmos idénticos a los del YM2612
 4. controles para cambiar entre monofónico y polifónico, legato, voice-stealing y comportamiento del pitch bend (*global* aplica el bend a todas las voces de la polifonía y *last* aplica el bend sólo a la última voz activada)
 
	 CUIDADO: en modo monofónico *bend* debe estar en *global* y en modo polifónico *legato* debe estar apagado, de lo contrario pueden surgir comportamientos inesperados (errores conocidos que aún no supe arreglar)

## créditos
[pure data](https://github.com/pure-data/pure-data) por miller puckette y muchxs más
[camomile](https://github.com/pierreguillot/Camomile) por pierre guillot
