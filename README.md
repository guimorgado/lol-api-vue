# kaikoo-code-challenge

## Build Setup

```bash
# Instalar dependencias
$ npm install

# Arrancar proyecto en local en localhost:3000
$ npm run dev
```

## Code Challenge
En este Challenge, usarás **Nuxt.js** para maquetar el diseño de una página a partir de un diseño en Figma. El challenge será replicar una de las páginas de nuestra plataforma: https://lol.kaikoo.pro/champions (sin side-bar ni nav-bar, solo el contenido).

### Descripción de la tarea
· Haz una nueva página que al cargar realice una petición al backend para pedir los datos actualizados de todos los campeones de League of Legends. El endpoints es:
```bash
$ GET https://back.kaikoo.pro:8888/api/champions
```
· Pinta una Card para cada campeón con los datos de su JSON, incluyendo el efecto de hover, siguiendo el diseño que aparece en el figma:

https://www.figma.com/file/EVwNS7MNeEujU5GUiTjfQ0/Prueba-de-nivel

Las imágenes necesarias para el hover las puedes obtener con esta URL:
```bash
https://cdn.communitydragon.org/latest/champion/${nameId}/splash-art/centered
```
**COMMUNITY DRAGON ESTÁ CAÍDO.** Esperamos que vuelva pronto, si sigue sin funcionar podéis obtener las imágenes con esta URL:
```bash
https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${nameId}_0.jpg
```

· Por último, añade una barra de filtrado para los campeones. Se puede filtrar por nombre, por posición y por dificultad. Los filtros tienen que aplicarse en tiempo real y pueden ser borrados en cualquier momento.

### Tarea opcional
· Añade una funcionalidad para guardar campeones en favoritos. No te preocupes por el diseño, añade un botón en algún sitio dentro de la card para añadir/eliminar campeones de Favoritos. Añade también un filtro que muestre solo los campeones guardados en favoritos.


## Instrucciones
  · **NO QUEREMOS ROBARTE MUCHO TIEMPO.** No hace falta hacer over-engineering, haz simplemente lo que te pedimos de la mejor forma que sepas, del mismo modo que lo harías en tu día a día en nuestra empresa.

  · No te preocupes de diseño responsive ni de dispositivos móviles.

  · No hace falta hacer tests.

  · Puedes usar Tailwind si lo prefieres.

## Instrucciones para compartir tu solución
Clona nuestro repositorio y súbelo a tu github como repositorio privado. Invita a nuestro CTO [Jose Pina](https://github.com/josepinaKaikoo) y a nuestro Frontend [Alejandro Maldonado](https://github.com/amaldonadokaikoo). De esta manera, podremos revisar tu código y tenerlo a mano para el siguiente paso: una entrevista personal 👻

