---
layout: post
title:  "Les Mixins de Foundation 6"
date:   2017-08-23 12:10:42 +0000
categories: frontend
---
Dans le jargon des `pré-processeurs css`, un mixin c'est une `fonction`. Il prend un ou plusieurs paramétres.

#### Qu'est un pré-pocesseur css?

Les pré-processeurs sont outils qui premettent de dynamiser le css. Le `CSS` n'a jamais évolué, ça a toujours été selecteurs, attributes, valeurs.

{% highlight css %}
.seleteur {
	color: #fff
}
{% endhighlight %}

Il n'y a pas de possbilité en css d'ecrire une fonction, heritage, boucles, les conditions etc. C'est là qu'arrivent les pré-processeurs apportant ainsi ces fonctionalités au `css. Le plus connu et le plus utilisé se nomme `SASS`, il y'en a d'autre LESS, STYLUS etc.

Le `SASS` (Syntactically Awesome Stylesheets) a langage de script qui compile du css. Il a été créé par Hampton Catlin (créateur de `haml`) et Nathalie Weizenbaum en 2007.

`SASS` a beaucoup d'aventage, la rapidité ainsi que les autres fonctionnalités et concepts (les variales, Nesting, Mixins, Extand, Opération sur les couleurs, If/Else, Loop, Math, @import, etc... )

Il y'a deux types de syntaxe: la version nommé `syntaxe indentée` plus proche de `haml`

{% highlight css %}
<!-- extension du fichier .sass -->
$blue: blue

.button
	background-color: $blue
	padding: 10px
	color: $white
	&:hover
		background-color: darken($blue, 10)
<!-- Bizzar comme changement -->
{% endhighlight %}

et la version nommé `SCSS` plus proche du `CSS`

{% highlight css %}
<!-- extension du fichier .scss -->
$blue: blue;

.button {
	background-color: $blue;
	padding: 10px;
	color: $white;
	//Nesting
	&:hover {
		background-color: darken($blue, 10);
	}
}
{% endhighlight %}

#### Maintenant que vous savais les pré-processeurs, écrivons un mixin
Je veux ajouter l'effet arrondi et un ombre sur les boutons, formulaire, card etc. 
Ex: Une maquette oû les boutons, form, cards sont tous arrondi avec un hombre. Au lieu d'écrire des lignes de code sur les boutons, les form, card etc... Ecrivons un mixins (une fonction) à chaque fois que l'on a besoin de cette effect (DRY)

{% highlight css %}
<!-- Sass syntax -->
=round-effect()
	border-radius: 50px
	box-shadow: 0 2px 4px rgba(#000, 0.20)
	&:focus
		box-shadow: 0 0 2px rgba(green, 0.20)


<!-- Mixin avec paramettre -->
=round-effect($radius, $color)
	border-radius: $radius
	box-shadow: 0 2px 4px rgba($color, 0.20)
	&:focus
		box-shadow: 0 0 2px rgba($color, 0.20)

.button
	+round-effect
	+round-effect(50px, yellow)
{% endhighlight %}

{% highlight css %}
<!-- Scss syntax -->
@mixin round-effect() {
	border-radius: 50px;
	box-shadow: 0 2px 4px rgba(#000, 0.20);
	&:focus {
		box-shadow: 0 0 2px rgba(green, 0.20)
	}
}

<!-- Mixin avec paramettre -->
@mixin round-effect($radius, $color) {
	border-radius: $radius;
	box-shadow: 0 2px 4px rgba($color, 0.20);
	&:focus {
		box-shadow: 0 0 2px rgba($color, 0.20);
	}
}
.button {
	@include round-effect();
	@include round-effect(50px, yellow);
}
{% endhighlight %}

## DEMO

#### Ok, revenons à l'objet de la présentation: `Les Mixins de Foundation 6`

Foundation est le framework css responsive le plus avancé au monde. Il est Mobile first, modulable etc. Tout les component des foundations ont des mixins (Button, Grid, Forms, Pagination etc ...)



# DEMO

# Message
