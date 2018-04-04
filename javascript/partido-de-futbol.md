# Ejercicio propuesto - partido de fútbol

volver a [ejemplos y ejercicios Arrays / Strings / Object Literals](./javascript-arrays-strings-object-literals-ejemplos.md)

volver a [JavaScript](./javascript-intro.md)

<br/>

El objetivo es armar una página que muestre información sobre un partido de fútbol, y algunas estadísticas del mismo. 

Se parte de la siguiente información.
```
			const equipoLocal = {
				nombre: "España", 
				titulares: [
							{nuemro: 1, nombre: "David De Gea", posicion: "arquero", puntaje: 6.9}, 
							{nuemro: 2, nombre: "Daniel Caravajal", posicion: "defensa", puntaje: 6.0}, 
							{nuemro: 3, nombre: "Gerard Pique", posicion: "defensa", puntaje: 6.1}, 
							{nuemro: 15, nombre: "Sergio Ramos", posicion: "defensa", puntaje: 6.4}, 
							{nuemro: 18, nombre: "Jordi Alba", posicion: "defensa", puntaje: 5.6}, 
							{nuemro: 8, nombre: "Koke", posicion: "mediocampo", puntaje: 5.6}, 
							{nuemro: 10, nombre: "Thiago Alcantara", posicion: "mediocampo", puntaje: 6.7}, 
							{nuemro: 6, nombre: "Andres Iniesta", posicion: "mediocampo", puntaje: 6.9}, 
							{nuemro: 22, nombre: "Isco", posicion: "delantera", puntaje: 8.3}, 
							{nuemro: 19, nombre: "Diego Acosta", posicion: "delantera", puntaje: 7.0}, 
							{nuemro: 20, nombre: "Marco Asensio", posicion: "delantera", puntaje: 6.8}
				],
				suplentes: [
							{nuemro: 13, nombre: "Arrizabalaga", posicion: "defensa"}, 
							{nuemro: 25, nombre: "Jose Reina", posicion: "arquero"}, 
							{nuemro: 4, nombre: "Nacho Fernandez", posicion: "defensa"}, 
							{nuemro: 5, nombre: "Cesar Azpilicueta", posicion: "mediocampo"}, 
							{nuemro: 16, nombre: "Alvaro Odriozola", posicion: "mediocampo"}, 
							{nuemro: 24, nombre: "Marcos Alonso", posicion: "mediocampo"},
							{nuemro: 7, nombre: "Saul Ñiguez", posicion: "delantera"},
							{nuemro: 12, nombre: "Rodri Hernandez", posicion: "defensa"},
							{nuemro: 14, nombre: "Lucas Vazquez", posicion: "mediocampo"},
							{nuemro: 23, nombre: "Dani Parejo", posicion: "delantera"},
							{nuemro: 9, nombre: "Rodrigo Moreno", posicion: "delantera"},
							{nuemro: 17, nombre: "Iago Aspas", posicion: "delantera"},
				], 
				cambios: [
							{minuto: 45, entra: 17, sale: 19, motivo: "tactico", puntaje: 8.9}, 
							{minuto: 55, entra: 7, sale: 6, motivo: "tactico", puntaje: 5.7}, 
							{minuto: 72, entra: 5, sale: 3, motivo: "tactico", puntaje: 5.6}, 
							{minuto: 76, entra: 14, sale: 22, motivo: "tactico", puntaje: 6.2},
							{minuto: 79, entra: 24, sale: 18, motivo: "tactico", puntaje: 5.6},
							{minuto: 82, entra: 23, sale: 10, motivo: "tactico", puntaje: 5.7},
				], 
				amonestados: [
							{minuto: 68, numero: 22}, 
							{minuto: 89, numero: 22}
				], 
				expulsados: [], 
				goles: [
							{minuto: 12, numero: 19}, 
							{minuto: 27, numero: 22}, 
							{minuto: 52, numero: 22}, 
							{minuto: 55, numero: 10}, 
							{minuto: 72, numero: 22}, 
							{minuto: 74, numero: 17}
				]
			}
			const equipoVisitante = {
				nombre: "Argentina", 
				goles: 1, 
				titulares: [
							{nuemro: 1, nombre: "Sergio Romero", posicion: "arquero", puntaje: 3.5}, 
							{nuemro: 26, nombre: "Fabricio Bustos", posicion: "defensa", puntaje: 3.8}, 
							{nuemro: 17, nombre: "Nicolas Otamendi", posicion: "defensa", puntaje: 5.4}, 
							{nuemro: 16, nombre: "Marcos Rojo", posicion: "defensa", puntaje: 3.9}, 
							{nuemro: 3, nombre: "Nicolas Tagliafico", posicion: "defensa", puntaje: 3.9}, 
							{nuemro: 6, nombre: "Lucas Biglia", posicion: "mediocampo", puntaje: 4.6}, 
							{nuemro: 14, nombre: "Javier Mascherano", posicion: "mediocampo", puntaje: 4.4}, 
							{nuemro: 20, nombre: "Giovani Lo Celso", posicion: "mediocampo", puntaje: 5.2}, 
							{nuemro: 19, nombre: "Ever Banega", posicion: "mediocampo", puntaje: 5.2}, 
							{nuemro: 27, nombre: "Maximiliano Meza", posicion: "delantera", puntaje: 4.4}, 
							{nuemro: 9, nombre: "Gonzalo Higuain", posicion: "delantera", puntaje: 6.0}
				],
				suplentes: [
							{nuemro: 12, nombre: "Nahuel Guzman", posicion: "defensa"}, 
							{nuemro: 23, nombre: "Wilfredo Caballero", posicion: "arquero"}, 
							{nuemro: 2, nombre: "Gabriel Mercado", posicion: "defensa"}, 
							{nuemro: 4, nombre: "Federico Fazio", posicion: "defensa"}, 
							{nuemro: 13, nombre: "Ramiro Funes Mori", posicion: "defensa"}, 
							{nuemro: 5, nombre: "Leandro Paredes", posicion: "mediocampo"},
							{nuemro: 8, nombre: "Marcos Acuña", posicion: "mediocampo"},
							{nuemro: 15, nombre: "Pablo Perez", posicion: "mediocampo"},
							{nuemro: 18, nombre: "Angel Correa", posicion: "mediocampo"},
							{nuemro: 21, nombre: "Cristian Pavon", posicion: "delantera"},
							{nuemro: 22, nombre: "Lautaro Martinez", posicion: "delantera"},
							{nuemro: 24, nombre: "Diego Perotti", posicion: "delantera"},
				], 
				cambios: [
							{minuto: 22, entra: 23, sale: 1, motivo: "lesion", puntaje: 3.8}, 
							{minuto: 56, entra: 21, sale: 14, motivo: "tactico", puntaje: 4.2}, 
							{minuto: 59, entra: 22, sale: 9, motivo: "tactico", puntaje: 5.1}, 
							{minuto: 62, entra: 15, sale: 19, motivo: "tactico", puntaje: 4.0},
							{minuto: 62, entra: 2, sale: 26, motivo: "tactico", puntaje: 5.9},
							{minuto: 87, entra: 8, sale: 20, motivo: "tactico", puntaje: 5.7},
				], 
				amonestados: [
							{minuto: 68, numero: 3}, 
							{minuto: 81, numero: 27},
							{minuto: 87, numero: 16},
							{minuto: 89, numero: 21}
				], 
				expulsados: [], 
				goles: [
							{minuto: 39, numero: 17} 
				]
			}
```

Como se observa: cada jugador se lo identifica por su número, la lista completa de los jugadores convocados para el partido serían los titulares más los suplentes, luego en las listas de amonestados, cambios, etc. identificamos a los mismos por su número.

<br/>

## Requerimiento básico

Visualizar la formación inicial de los equipos indicando: número, nombre y puntaje de los jugadores, hacerlo en dos paneles independientes, uno para el equipo local ubicado a la izquierda de la pantalla, y otro para el equipo visitante ubicado a la derecha de la pantalla; para los paneles izquierdo y derecho utilizar DIVs y para la formación de los equipos utilizar TABLEs, donde los datos de cada jugador forman una fila y el número, nombre y puntaje son las columnas de la misma.

<br/>

## Estadísticas del partido

Mostrar un boton debajo de cada formación que nos permita visualizar y ocultar las estadísticas de los equipos, las mismas incluiran la siguiente información:
- cantidad de jugadores del equipo que disputaron el partido, es decir titulares y suplentes que ingresaron.
- promedio de ambos equipos, calculado por el puntaje de los jugadores que disputaron el partido.
- el nombre de los jugadores amonestados del equipo.
- jugadores que jugaron menos de 20 minutos, sabiendo que la duración del partido fue de 90 minutos.

<br/>

## Estadística Avanzada

- total de mediocampistas amonestados.
- formacion del equipo que finalizo en el campo de juego
