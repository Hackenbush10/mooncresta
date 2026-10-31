# Moon Cresta Arcade

Versión web del arcade *Moon Cresta* (Nichibutsu, 1980). Un único `index.html` con canvas, sin dependencias ni compilación. Mismo planteamiento que [Phoenix](../phoenix).

**Demo:** https://mooncresta.vercel.app

## Controles

| Acción | Teclas |
|---|---|
| Mover | ← → / A D |
| Disparar | Espacio |
| Retrocohete (en el acoplamiento) | Espacio |
| Pausa | P |
| Sonido | M |
| Efecto CRT | C |
| Barrera (si está activada) | ↓ / Shift |
| Nivel (fácil / normal / difícil) | ← → en la pantalla de título |
| Activar la barrera | E (en la pantalla de título) |
| Conservar el acople al morir | R (en la pantalla de título) |
| Empezar | Enter |
| Naves infinitas | I (en la pantalla de título) |
| Probar el acoplamiento en bucle | D (en la pantalla de título) |

En móvil aparecen botones táctiles.

## Cómo se juega

Empiezas con una pila de tres segmentos de cohete y vuelas sólo con el primero (MCX-1).
Cada ronda son **diez oleadas** agrupadas de dos en dos, y hay una **maniobra de acoplamiento
tras la 4ª y tras la 8ª** siempre que te quede algún segmento en reserva.

- **Acoplar** suma dos cañones (1 → 3 → 5 láseres), pero también convierte la nave en un blanco mucho mayor.
- Un impacto destruye la nave **entera**: si te tocan volando los tres segmentos, lo pierdes todo.
- En el acoplamiento el botón de fuego hace de retrocohete. Tienes 30 segundos y hay que alinearse:
  si llegas descentrado, el segmento con el que ibas a acoplar se destruye. Un pasillo a trazos marca
  el margen exacto (±11 px) y se pone verde cuando encajas.

## Dos opciones que no están en la recreativa

Se activan en la pantalla de título y quedan guardadas entre partidas.

- **Barrera (E)** — la misma que en Phoenix: con ↓ o Shift levantas una cúpula que desintegra las balas
  enemigas y mata a lo que te embista. Dura 1,6 s, **te deja clavado en el sitio** mientras está activa
  y tarda 5 s en recargarse. El indicador de carga sale abajo a la derecha. En móvil aparece un cuarto
  botón táctil.
- **Conservar acople (R)** — en la recreativa un impacto destruye la nave **entera** y vuelves a volar
  con un solo segmento, así que morir con los tres acoplados es el final de la partida. Con esta opción
  el impacto cuesta **una sola nave** y sigues volando con la nave acoplada que tenías.

## Modo de prueba del acoplamiento

La tecla **D** en el título encadena acoplamientos sin parar, con naves infinitas y sin oleadas de por
medio, recorriendo en bucle los tres multiplicadores (I con II, I+II con III, II con III). En pantalla
aparece la desviación en píxeles y la altura que falta para el enganche, para afinar el margen.
**Enter** sale al título.

## Oleadas

| Oleadas | Enemigo | Puntos |
|---|---|---|
| 1-2 | Bicho que se parte en dos mitades al primer impacto | 50 por mitad |
| 3-4 | Enjambre de moscas, pican de dos en dos | 30 |
| 5-6 | Peine que se desvanece y reaparece mientras pica | 60 |
| 7-8 | Cápsula que se transforma en misil y cae a plomo | 100 |
| 9-10 | Tormenta de meteoritos en diagonal | 200 |

Bonus de acoplamiento: **100 / 200 / 300 puntos por segundo restante** según qué segmentos unas
(I con II o III, II con III, I+II con III). **Pila nueva de tres naves al llegar a 30.000 puntos.**

## Niveles

Los tres del manual original. Cambian la velocidad de los enemigos y, sobre todo, cómo reaparecen
los que se te escapan por abajo:

- **Fácil**: vuelven a entrar por arriba, por el centro.
- **Normal**: a veces asoman por debajo de la pantalla.
- **Difícil**: asoman por debajo muy a menudo, justo bajo tu nave.

A partir de la segunda ronda, el último superviviente de cada oleada se vuelve mucho más rápido.

## Desarrollo

Es un archivo estático. Para verlo en local basta abrir `index.html`, o:

```bash
npx serve .
```

## Despliegue

El repositorio está conectado a Vercel: **cada push a `main` despliega a producción solo**, y las
ramas y los pull requests generan despliegues de vista previa.

```bash
git push
```

Para desplegar a mano sin pasar por git:

```bash
npx vercel deploy --prod
```

## Notas

Las reglas (número de oleadas, momento de los acoplamientos, tabla de puntos, bonus por segundo
restante, vida extra a 30.000 y el comportamiento de los tres niveles de dificultad) están tomadas
del manual de la conversión para Atari 7800. Los sprites, los sonidos y las trayectorias son una
recreación propia en el estilo de la recreativa; no contienen material extraído de ninguna ROM.
