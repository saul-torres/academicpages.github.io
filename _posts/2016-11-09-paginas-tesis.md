---
title: 'El número de páginas de las tesis en España'
date: 2016-11-09
permalink: /posts/2016/11/paginas-tesis/
tags:
  - r
  - tesis
  - big data
---

Hace un tiempo leí un interesante (\*) artículo sobre el número de páginas de las tesis en España y cómo se tiende hacia valorar (o preferir, o simplemente es lo que marca la tendencia) más el peso que el contenido y calidad. El artículo en cuestión se titula "Tesis al peso" y se publicó en el blog Nada Es Gratis (podéis leerlo [aquí](http://nadaesgratis.es/fernandez-villaverde/tesis-al-peso)). Los datos que en ese artículo citaban eran los publicados en un blog sobre R (si no sabéis qué es R [ya estáis tardando](https://saul-torres.github.io/posts/2018/01/r-info/)...) y en los que se analizaba el tamaño de las tesis doctorales en la Universidad de Minnesota (podéis leer la entrada [aquí](http://www.r-bloggers.com/average-dissertation-and-thesis-length-take-two/)).

Aprovechando un ratillo que he tenido, que cada vez me encuentro más cómodo programando en R, y dada la buena bondad que la comunidad de usuarios de este lenguaje tiene de publicar sus códigos en abierto, me he planteado la posibilidad de adaptar/aplicar el código de Marcus W. Beck ([fawda123 en github](https://github.com/fawda123/diss_proc)) al caso de las tesis españolas. Y bueno, aunque la cosa tiene su miga, comentarios, aclaraciones y margen de mejora, para los impacientes dejo aquí el gráfico en cuestión.

<p align="center">
  <figure>
    <a href="https://github.com/saul-torres/saul-torres.github.io/blob/master/images/tesis.box.final.png">
      <img src="https://github.com/saul-torres/saul-torres.github.io/blob/master/images/tesis.box.final.png" width="600" >
    </a>
    <figcaption>Número de páginas de tesis españolas por materia. Datos de Tesis Doctorales en Red (http://www.tdx.cat/).</figcaption>
  </figure> 
</p>

Y ahora las diversas aclaraciones, explicaciones metodológicas y demás comentarios que considero más que oportunos y necesarios:

1. La primera cuestión que me planteé fue de donde obtener los datos. Teseo (link) no proporciona datos de número de páginas. Alguna que otra base de datos europea tampoco. Afortunadamente Tesis Doctorales en Red (link) sí, así que sobre ella está basado el código.
2. Sobre este respecto, hay que añadir que no todas las tesis españolas están en TDR, pero sí que creo que sirve como muestra más que representativa.
3. El código en cuestión está disponible aquí. Si alguien se anima a mejorarlo o utilizarlo para análisis más completos, bienvenido sea.
4. Sobre el código lo primero que quiero decir es que estoy, como quien dice, empezando a dar pasitos con R. Seguramente no sea ni lo más eficiente del mundo ni bonito, pero creo que de momento sirve para empezar. Eso sí, he intentado comentar lo máximo posible para aquellos interesados en saber qué demonios hace. En todo caso, recuerdo que está basado en el citado anteriormente para la Universidad de Minnesota.
5. La información que se captura de TDR de cada tesis es "código", "fecha de defensa", "número de páginas" y "materia".
6. El dato "materia" puede resultar problemático. En más de un registro (y de dos, y de...) vienen asignadas varias materias. Incluso en alguno se recogen de forma de descendente todos los relacionados (p.ej. 3 - Ciencias Sociales, 33 - Economía, 332 - Economía regional y territorial. Economía del suelo y de la vivienda). A falta de saber cómo conseguir una mejor clasificación de una tesis en función de la materia, el código simplemente almacena el primero de las materias presente (en el ejemplo anterior, 3 - Ciencias Sociales).
7. Para realizar el análisis, obtengo los últimos 5.000 registros que se han publicado en TDR (los 5.000 más recientes quiero decir). En la base de datos del sistema hay un total de más de 20.000, así que supongo que puede llegar a ser un número representativo. En todo caso, cambiando dos números en el código se puede ampliar el número de registros.
8. No obstante, algunos de esos registros (y me temo que por un pequeño lío con los idiomas de TDR que no consigo entender - algunas veces la información aparece en español, otras en catalán, otras en inglés -), no capturan bien los datos, por lo que realmente los válidos se han quedado reducidos a poco menos de la mitad.
9. Las categorías se han simplificado y agrupado. Por ejemplo, todas las variaciones matemáticas ("512 - Álgebra", "514 - Geometría", "517 - Análisis"...) bajo la categoría "51 - Matemáticas". Igual se ha hecho con casi todas ellas.

![](https://github.com/saul-torres/saul-torres.github.io/blob/master/images/tesis.num.final.png)
*Número de tesis incluídas en el análisis por materia. Datos de Tesis Doctorales en Red (http://www.tdx.cat/).*

Tengo la intención de seguir trabajando un poco más con el código y ver si todo esto se puede analizar un poco más y representar algo mejor, pero de momento queda aquí una primera pincelada. Posiblemente más cosas se pueden hacer (así a bote pronto, un análisis temporal de la variación del número de páginas a lo largo del tiempo y por materias), pero poco a poco.

De momento, _ahí queda eso_...

___
(*) "Interesante" principalmente para los que hemos pasado por el proceso de escribir una tesis doctoral, con todas las vicisitudes que ello mismo implica...
