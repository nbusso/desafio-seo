*ReadMe entrega desafío SEO - Nicolás Busso*

#### Índice
- [Optimizaciones SEO](#optimizaciones-seo)
    * [Index](#index)
    * [Resto de páginas](#resto-de-páginas)
- [Uso de SASS](#uso-de-sass)
    * [@extend](#extend)
    * [Mapas](#mapas)
    * [@mixin](#mixins)
- [FAVICON](#favicon)


---


# Optimizaciones SEO:

## Index

Meta tags base, los cuales se van a repetir y modificar mínimamente en el resto de las páginas.

```html
<meta name="title" content="Guild Wars 2 Fansite en Español - Inicio">

<meta name="description" content="En este sitio vas a encontrar todo lo que necesitas saber sobre Guild Wars 2 si eres un nuevo jugador!">

<meta name="keywords" content="guild wars, guild wars 2, guias, nuevos jugadores, principiantes, gw2">
```
[`volver al índice`](#índice)

## Resto de páginas

Modificaciones y agregados respecto al index:
- cambios en los títulos para tener relación con la página.
- cambios en el meta name='title' para tener relación con la página.
- cambios en el meta name='description' para tener relación con la página (ejemplificados abajo).
- se agregaron (en conjunto con los globales del index) los siguentes *keywords* en las paginas:

```html
<!-- razas.html -->
<meta name="description" content="Toda la información sobre las razas de Guild Wars 2 en español, ideal para nuevos jugadores">

<meta name="keywords" content="razas, asura, humanos, charr, sylvari, norn">

<!-- personajes.html -->
<meta name="description" content="Toda la información sobre los personajes principales de Guild Wars 2 en español, ideal para nuevos jugadores">

<meta name="keywords" content="personajes, npc, historia">

<!-- noticias.html -->
<meta name="description" content="Las últimas novedades sobre Guild Wars 2 en español, directo de la página oficial!">

<meta name="keywords" content="noticias, novedades, oficial, ofertas">

<!-- mundo.html -->
<meta name="description" content="Toda la información sobre Tyria, el mundo de Guild Wars 2, en español, ideal para nuevos jugadores">

<meta name="keywords" content="mundo, mundo abierto, contenido, tyria">

<!-- links-utiles.html -->
<meta name="description" content="Colección de guias y contenido sobre Guild Wars 2">

<meta name="keywords" content=" monturas, mapeo, mapas, profesiones, crafteo, add-ons">

<!-- jefes.html -->
<meta name="description" content="Toda la información sobre los Jefes de campo de Guild Wars 2 en español, ideal para nuevos jugadores">

<meta name="keywords" content="jefes, jefes de campo, boss, world boss">

<!-- clases.html -->
<meta name="description" content="Toda la información sobre las clases de Guild Wars 2 en español, ideal para nuevos jugadores">

<meta name="keywords" content="clases, hipnotizador, guardian, nigromante, guardabosques, elementalista, guerrero, ladrón, ingeniero, retornado">
```
[`volver al índice`](#índice)

---

# Uso de SASS

## Extend
Usé @extend para setear el valor del espaciado en los contenedores, podría haber usado una clase pero con el fin de aplicarlo por la consigna lo usé de esta manera (no encontré otra aplicación más útil dada la composición de mi página)

```scss
//----  variable
%spacing {
    margin: 8em 0 3em 0;
}

//---- algunas aplicaciones
//mundo
.mainMundo {
    @extend %spacing;
}

//jefes
.mainJefes {
    min-height: 80vh;
    @extend %spacing;
}

//personajes
.mainPersonajes {
    min-height: 80vh;
    @extend %spacing;
}
```
[`volver al índice`](#índice)

## MAPAS
Use mapas para las cards en la sección 'explora tyria' de mi index.
```scss
$cards: (
    1: '../img/Concept07.jpg',
    2: '../img/caithe.jpg',
    3: '../img/LegendaryMed.jpg',
    4: '../img/LegendaryLight.jpg',
    5: '../img/boss_1.jpg'
);

@each $number, $img in $cards {
    .card_#{$number} {
        background-image: url($img);
    }
}
```
lo cual compiló en:
```css
.card_1 {
  background-image: url("../img/Concept07.jpg");
}

.card_2 {
  background-image: url("../img/caithe.jpg");
}

.card_3 {
  background-image: url("../img/LegendaryMed.jpg");
}

.card_4 {
  background-image: url("../img/LegendaryLight.jpg");
}

.card_5 {
  background-image: url("../img/boss_1.jpg");
}
```
queda bien para editar rápidamente las imagenes de cada card o agregar/quitar alguna en caso de necesitarlo.

[`volver al índice`](#índice)

## MIXINS
Utilicé @mixin para aplicar flex más rapido, ya que lo uso constantemente en casi todos mis contenedores.

```scss
// en _utilities.scss

@mixin flex-type($dir, $wrap, $just_cont, $align_items) {
    display: flex;
    flex-flow: $dir $wrap;
    justify-content: $just_cont;
    align-items: $align_items;
}

// ejemplo de aplicación en links-utiles
.wrapperCardLinks {
    @include flex-type(row, wrap, center, flex-start);
    margin-top: 4vh;
    gap: 20px;

    .cardLinks {
        border: 1px solid $color_4;
        padding: 2vh 2vw;
        width: 100%;
        max-width: 320px;

        h4 {
            color: $color_2;
        }

        ul {
            padding-left: 20px;

            li {
                line-height: 150%;

                a {
                    color: $color_2;
                }
            }
        }
    }
}

```
[`volver al índice`](#índice)

# FAVICON
## Imagen y herramientas utilizadas
Imagen de logo: <br>
<img src='./img/logo_notext.png' width='200'>

la cual convertí en .ico usando [Favicon Generator](https://www.favicon-generator.org) y luego apliquén todos los .html del sitio.

[`volver al índice`](#índice)