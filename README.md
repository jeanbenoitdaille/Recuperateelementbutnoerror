# Recuperateelementbutnoerror
Récupérer un élément dans une liste sans générer d'erreur 
Le but de cet exercice était de créer une fonction qui nous permette de récupérer un élément dans une liste à partir de son indice, sans retourner d'erreur au cas où l'indice est en dehors des limites de la liste.

Pour ce faire, nous commençons par créer une fonction qui accepte en premier argument la liste et en deuxième argument l'indice à récupérer :

    def recuperer_item(liste, indice):

Nous créons ensuite une structure conditionnelle pour gérer tous les cas de figure. Le plus simple à gérer est le cas de figure dans lequel l'indice est égal à 0 :

    elif indice == 0 and liste:
        return liste[0]

Dans ce cas-ci, on vérifie si l'indice est égal à 0 et si la liste n'est pas vide (une liste vide est évaluée à False, si la liste contient au moins un élément, elle sera évaluée à True, pas besoin donc d'utiliser la fonction len pour vérifier la longueur de la liste).

Si c'est le cas, on retourne tout simplement l'élément 0 de la liste.

Le deuxième cas de figure abordé correspond à un indice négatif, ce que nous vérifions avec indice < 0.

Si l'indice est plus petit que 0, il faut également vérifier qu'il n'est pas en dehors des limites de la liste.
Pour cela, nous utilisons la fonction abs, qui permet de retourner la valeur absolue d'un nombre. Dans le cas de l'indice -13, la fonction abs nous retournera donc 13. Il ne reste plus qu'à vérifier si ce nombre est inférieur ou égal à la longueur de la liste :

    if indice < 0 and abs(indice) <= len(liste):
        return liste[indice]

Le dernier cas à gérer est celui dans lequel l'indice est positif. Dans ce cas-ci, il suffit de vérifier également si l'indice est plus petit que la longueur de la liste pour s'assurer que l'on reste bien dans les limites :

    elif indice > 0 and indice < len(liste):
        return liste[indice]

Vous vous demandez peut-être pourquoi dans un cas, on vérifie si l'indice est inférieur ou égal à la longueur de la liste et dans l'autre cas on vérifie si l'indice est strictement inférieur.
Tout simplement parce que quand on récupère un indice en partant de la fin de la liste, on commence à -1 (-1 pour récupérer le dernier élément, -2 pour l'avant dernier etc).
Dans l'autre cas, on commence à 0 (car l'indice du premier élément d'une liste est égal à 0).

Dans le cas d'une liste comprenant 4 éléments, si nous voulons récupérer le premier élément en partant de la fin, on peut utiliser l'indice -4. La valeur absolue de l'indice (4), sera donc égal à la longueur de la liste.

Si par contre nous commençons par le début, et que nous voulons récupérer le dernier élément, alors vu que nous partons de 0, le dernier élément aura l'indice 3. C'est pourquoi dans le cas d'un indice positif, nous vérifions si l'indice est strictement inférieur à la longueur de la liste.

Pour finir avec cet exercice, si on ne passe dans aucune de ces conditions, c'est donc que l'indice est en dehors des limites de la liste. Dans ce cas-ci, nous retournons une chaîne de caractère indiquant que l'indice est hors de la liste :

    return "Index {} hors de la liste".format(indice)
