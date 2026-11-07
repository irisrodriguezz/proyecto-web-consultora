# Comentario sobre la Tarea UP6 de los módulos LMSGI y Proyecto Intermodular

En este archivo README.md explico algunos aspectos pertenecientes a mi entrega como son las decisiones de diseño elegidas así como las dificultades que han surgido a la hora de realizarla.

## Diseño

El concepto de la web gira en torno al _Modern Tech Design_ por ello he decidido usar una paleta de colores que combina morados, azules eléctricos y blancos en conjunto con tendencias como el _Glassmorphism_ y aunque el resultado final luzca bastante oscura esa era la intencionalidad que yo quería darle.

+ La tipografía he querido que sea en color blanco y **bold** para que destaque sobre los fondos oscuros.

+ He querido añadir un fondo en movimiento y que estuviese en bucle para que no hubiese ningún corte durante el tiempo que el usuario está visualizando la página. A ese fondo le he añadido un _blur_ para que haga contraste con las letras y éstas sean más legibles.

+ Las tarjetas de 'Servicios' las he hecho con un degradado de 3 colores claritos y les he bajado la opacidad para darle ese efecto _glass_.

+ Los iconos de las tarjetas de 'Servicios' las he buscado en webs de imágenes de uso libre y he querido que todas tuvieran el mismo estilo 3D glossy para mantener la coherencia entre ellas.

+ El icono del _header_ y del favicon lo he buscado también en una web de imágenes de uso libre. El del favicon venía a color y el del _header_ lo he convertido en blanco en un programa de edición de imágenes para que vaya a conjunto con el nombre de la empresa y el _nav_.

+ Para la tabla también he elegido colores azules y para las filas pares e impares he añadido un cebreado como indicaba el enunciado de la tarea.

## Dificultades

1. **Posicionamiento con el degradado de fondo**

Mi intención en todas las páginas era añadir un fondo con un degradado que fuera de transparente a morado a modo de transición entre el fondo en movimiento y los elementos que están delante.
El problema que me surgía constantemente era que ese "flexbox-fondo" se encogía, no abarcaba todo el ancho de la pantalla, a veces aparecía arriba del todo, otras abajo o incluso no llegaba hasta el footer dejando un hueco entre ambos.
Me dí cuenta de que había un problema de posicionamiento, en mi caso que no estaba cerrando bien la etiqueta /div donde correspondía. La solución finalmente llegó al poner el /div de ese class="flexbox-fondo" JUSTO DESPUÉS de /main y no antes como yo lo estaba haciendo.

2. **Variables CSS para colores y degradados con transparencia**

A la hora de hacer uso de variables CSS (:root { --color-primary: ... }) para la paleta de colores me surgió un problema, y es que, cuando yo quería añadir colores o degradados con transparencia éstos no funcionaban. Leyendo en páginas y foros descubrí que mi problema venía porque la notación hexadecimal no puede almacenar información del canal alfa en CSS.
(Esto es algo que ha cambiado con CSS Color 5 que ya presenta algunas funciones nuevas y estupendas para manipular valores hexadecimales existentes, incluido el cambio de su canal alfa). Encontré la solución en la web stackoverflow de la mano del siguiente comentario:

https://stackoverflow.com/a/78541165

>Posted by Weber K.
Retrieved 2025-12-22, License - CC BY-SA 4.0
*/

:root {
  --color: #f0f0f0;
  --opacity: 0.5;
}
.myclass {
  background-color: rgb(from var(--color) r g b / var(--opacity))
}

Por tanto la solución fue establecer por un lado el --color y por otro lado su --opacity y unir ambos con esa línea de código en la propiedad background-color.
