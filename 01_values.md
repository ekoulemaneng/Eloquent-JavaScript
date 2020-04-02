{{meta {docid: values}}}

# Valeurs, types et opérateurs

{{quote {author: "Master Yuan-Ma", title: "The Book of Programming", chapter: true}

Sous la surface de la machine, le programme se déplace. Sans effort, il se dilate et se contracte. Dans une grande harmonie, les électrons se dispersent et se regroupent. Les formes sur l'écran ne sont que des ondulations sur l'eau. L'essence reste invisiblement en dessous.

quote}}

{{index "Yuan-Ma", "Book of Programming"}}

{{figure {url: "img/chapter_picture_1.jpg", alt: "Image d'une mer de bits", chapter: framed}}}

{{index "binary data", data, bit, memory}}

Dans le monde de l'informatique, il n'y a que des données. Vous pouvez lire des données, les modifier, en créer de nouvelles, mais ce qui n'est pas donnée ne peut être mentionnée. Toutes ces données sont stockées sous forme de longues séquences de bits et sont donc fondamentalement semblables.

{{index CD, signal}}

Les _bits_ sont des entités à deux valeurs, généralement décrites comme des zéros et des uns. À l'intérieur de l'ordinateur, ils prennent des formes telles qu'une charge électrique élevée ou faible, un signal fort ou faible, ou une tache brillante ou terne sur la surface d'un CD. Tout élément d'information discret peut être réduit à une séquence de zéros et de uns et donc être représenté en bits.

{{index "binary number", radix, "decimal number"}}

Par exemple, nous pouvons exprimer le nombre 13 en bits. Cela fonctionne de la même manière qu'un nombre décimal, mais au lieu de 10 ((chiffre))s différents, vous n'en avez que 2, et le poids de chacun augmente d'un facteur 2 de droite à gauche. Voici les bits qui composent le nombre 13, avec les poids des chiffres indiqués en dessous:

```{lang: null}
   0   0   0   0   1   1   0   1
 128  64  32  16   8   4   2   1
```

C'est donc le nombre binaire 00001101. Ses chiffres non nuls sont les suivants : 8, 4 et 1, et s'additionnent pour donner 13.

## Valeurs

{{index [memory, organization], "volatile data storage", "hard drive"}}

Imaginez une mer de bits, un océan de bits. Un ordinateur moderne typique possède plus de 30 milliards de bits dans sa mémoire de données volatile (mémoire de travail). Le stockage non volatil (le disque dur ou l'équivalent) tend à avoir encore quelques ordres de grandeur de plus.

Pour pouvoir travailler avec de telles quantités de bits sans se perdre, nous devons les séparer en morceaux qui représentent des informations. Dans un environnement JavaScript, ces morceaux sont appelés _((valeur))s_. Bien que toutes les valeurs soient constituées de bits, elles jouent des rôles différents. Chaque valeur a un ((type)) qui détermine son rôle. Certaines valeurs sont des nombres, d'autres des morceaux de texte, d'autres encore des fonctions, etc.

{{index "garbage collection"}}

Pour créer une valeur, il suffit d'invoquer son nom. Ceci est la norme pratique. Vous n'avez pas besoin de rassembler des matériaux de construction pour vos valeurs ou les payer. Il suffit d'en appeler un, et _hop_, vous l'avez. Ils ne sont pas vraiment créés de toutes pièces, bien sûr. Chaque valeur doit être stockée quelque part, et si vous voulez en utiliser à en même temps une quantité gigantesque, vous risquez d'être à court de mémoire. Heureusement, cela ne pose problème que si vous avez besoin de tous les éléments simultanément. Dès que vous cesserez d'utiliser une valeur, elle se dissipera, laissant derrière elle ses bits qui peuvent être réutilisés comme matériau de construction pour la prochaine génération de valeurs.

Ce chapitre présente les éléments de base des programmes JavaScript, c'est-à-dire les types de valeurs simples et les opérateurs qui peuvent agir sur ces valeurs.

## Nombres

{{index [syntax, number], number, [number, notation]}}

Les valeurs du type _nombre_ sont, sans surprise, des valeurs numériques. Dans un programme JavaScript, elles sont écrites comme suit :

```
13
```

{{index "binary number"}}

Utilisez-le dans un programme, et il fera en sorte que le format binaire du chiffre 13 prenne place dans la mémoire de l'ordinateur.

{{index [number, representation], bit}}

JavaScript utilise un nombre fixe de bits, 64 au total, pour stocker une valeur numérique unique. Le nombre de combinaisons possibles avec 64 bits est limité, ce qui signifie que le nombre de nombres différents pouvant être représentés est limité. Avec _N_ ((chiffre))s décimals, vous pouvez représenter 10^N^ nombres. De même, avec 64 chiffres binaires, vous pouvez représenter 2^64^ nombres différents, soit environ 18 quintillions (un 18 avec 18 zéros après). Cela fait beaucoup.

La mémoire des ordinateurs était autrefois beaucoup plus petite, et les gens avaient tendance à utiliser des groupes de 8 ou 16 bits pour représenter leurs nombres. Il était facile d'accidentellement _((dépasser la capacité))_ des nombres aussi petits - pour se retrouver avec un nombre qui ne correspondait pas au nombre de bits donné. Aujourd'hui, même les ordinateurs qui tiennent dans votre poche ont beaucoup de mémoire, vous êtes donc libre d'utiliser des blocs de 64 bits, et vous ne devez vous soucier du débordement que lorsque vous avez affaire à des nombres vraiment astronomiques.

{{index sign, "floating-point number", "sign bit"}}

Cependant, ce ne sont pas tous les nombres entiers inférieurs à 18 quintillions qui peuvent être représentés par un nombre JavaScript. Ces bits stockent également des nombres négatifs, de sorte qu'un bit indique le signe du nombre. Le fait que les nombres non entiers doivent également être représentés pose un problème plus important. Pour ce faire, certains des bits sont utilisés pour stocker la position de la virgule décimale. Le nombre entier maximum pouvant être stocké est plutôt de l'ordre de 9 quadrillions (15 zéros), ce qui reste fort énorme.

{{index [number, notation], "fractional number"}}

Les nombres décimaux s'écrivent avec une virgule.

```
9.81
```

{{index exponent, "scientific notation", [number, notation]}}

Pour les très grands ou très petits nombres, vous pouvez également utiliser la notation scientifique en ajoutant un _e_ (pour _exposant_), suivi de l'exposant du nombre.

```
2.998e8
```

Soit 2.998 × 10^8^ = 299,800,000.

{{index pi, [number, "precision of"], "floating-point number"}}

Les calculs avec nombres entiers (également appelés _((entier))s_) plus petits que les 9 quadrillons susmentionnés sont garantis pour toujours être précis. Malheureusement, les calculs avec des nombres décimaux ne le sont généralement pas. Tout comme π (pi) ne peut pas être exprimé avec précision par un nombre fini de chiffres décimaux, beaucoup de nombres perdent de leur précision lorsque seuls 64 bits sont disponibles pour les stocker. C'est chose regrettable, mais cela ne pose des problèmes pratiques que dans des situations spécifiques. Il est important d'en être conscient et de considérer les nombres décimaux comme des approximations, et non des valeurs précises.

### Arithmétique

{{index [syntax, operator], operator, "binary operator", arithmetic, addition, multiplication}}

La principale chose à faire avec les nombres est l'arithmétique. Les opérations arithmétiques telles que l'addition ou la multiplication prennent deux valeurs numériques et produisent un nouveau nombre à partir de celles-ci. Voici à quoi ils ressemblent en JavaScript :

```
100 + 4 * 11
```

{{index [operator, application], asterisk, "plus character", "* operator", "+ operator"}}

Les symboles `+` et `*` sont appelés _opérateurs_. Le premier représente l'addition, et le second la multiplication. Le fait de placer un opérateur entre deux valeurs l'appliquera à ces valeurs et produira une nouvelle valeur.

{{index grouping, parentheses, precedence}}

Mais l'exemple signifie-t-il "additionner 4 et 100, et multiplier le résultat par 11", ou la multiplication est-elle faite avant l'addition ? Comme vous l'avez peut-être deviné, la multiplication se fait d'abord. Mais comme en mathématiques, vous pouvez changer cela en mettant l'addition entre parenthèses.

```
(100 + 4) * 11
```

{{index "hyphen character", "slash character", division, subtraction, minus, "- operator", "/ operator"}}

Pour la soustraction, il y a l'opérateur "-", et la division peut être faite
avec l'opérateur "/".

Lorsque les opérateurs apparaissent ensemble sans parenthèses, l'ordre dans lequel qu'ils sont appliqués est déterminé par le _((préséance))_ des opérateurs. L'exemple montre que la multiplication passe avant l'addition. L'opérateur "/" a la même priorité que "*". Il en est de même pour "+" et "-". Lorsque plusieurs opérateurs ayant la même priorité apparaissent l'un à côté de l'autre, comme dans "1 - 2 + 1", ils sont appliqués de gauche à droite : " (1 - 2) + 1 ".

Ces règles de préséance ne sont pas une chose dont vous devez vous préoccuper. En cas de doute, il suffit d'ajouter des parenthèses.

{{index "modulo operator", division, "remainder operator", "% operator"}}

Il y a un autre opérateur arithmétique, que vous ne reconnaîtrez peut-être pas immédiatement. Le symbole `%` est utilisé pour représenter l'opération _reste de division entière_. X % Y est le reste de la division de X par Y. Par exemple, `314 % 100` donne `14`, et `144 % 12` donne `0`. La préséance de l'opérateur du reste de la division entière est la même que celle de la multiplication et de la division. Vous verrez aussi souvent cet opérateur appelé _modulo_.

### Nombres spéciaux

{{index [number, "special values"]}}

Il y a trois valeurs spéciales dans JavaScript qui sont considérées comme des nombres mais qui ne se comportent pas comme des nombres normaux.

{{index infinity}}

Les deux premiers sont `Infinity` et `-Infinity`, qui représentent les infinis positif et négatif. `Infinity - 1` est toujours `Infinity`, et ainsi de suite. Cependant, ne faites pas trop confiance au calcul basé sur l'infini. Ce n'est pas mathématiquement correct, et cela conduira rapidement au prochain nombre spécial : `NaN`.

{{index NaN, "not a number", "division by zero"}}

`NaN` signifie "pas un nombre (not a number)", même s'il _est_ une valeur du type nombre. Vous obtiendrez ce résultat lorsque vous essaierez, par exemple, de calculer `0 / 0` (zéro divisé par zéro), `Infinity - Infinity`, ou tout autre nombre avec d'autres opérations numériques qui ne donnent pas de résultat significatif.

## Chaînes de caractères

{{indexsee "grave accent", backtick}}

{{index [syntax, string], text, character, [string, notation], "single-quote character", "double-quote character", "quotation mark", backtick}}

Le type de données de base qui suit est la _((chaîne de caractères))_. Les chaînes de caractères sont utilisées pour représenter du texte. Ils sont écrits en insérant leur contenu entre guillemets.

```
`Descends sur la mer`
"Allonge-toi sur l'océan"
'Flotte sur l'océan'
```

Vous pouvez utiliser des guillemets simples, des guillemets doubles ou des guillemets inversés pour marquer les chaînes de caractères, pourvu que les guillemets soient au début et à la fin de la chaîne de caractères correspondant.

{{index "line break", "newline character"}}

Presque tout peut être mis entre guillemets, et JavaScript en fera une valeur de chaîne de caractères. Mais quelques caractères sont plus difficiles. Vous peut imaginer combien il peut être difficile de mettre des guillemets entre guillemets. _Nouvelle ligne_ (les caractères que vous obtenez lorsque vous appuyez sur [Entrée]{keyname}) peuvent être inclus sans caractère d'échappement uniquement lorsque la chaîne de caractères est mise entre guillemets  avec des guillemets inversés (`` ` ``).

{{index [escaping, "in strings"], ["backslash character", "in strings"]}}

Pour qu'il soit possible d'inclure de tels caractères dans une chaîne, le la notation suivante est utilisée : chaque fois qu'une barre oblique inversée ou antislash (`\`) est trouvée à l'intérieur texte cité, il indique que le caractère qui suit a une signification spéciale. C'est ce qu'on appelle _échapper_ un caractère. Un guillemet qui est précédé d'un antislash ne terminera pas la chaîne mais en fera partie. Lorsqu'un caractère "n" apparaît après un antislash, il est interprété comme un nouvelle ligne.  De même, un "t" après un antislash représente un ((caractère de tabulation)). Prenez la chaîne de caractères suivante:

```
"Voici la première ligne\nEt voici la deuxième ligne"
```

Voici le texte qu'il contient:

```{lang: null}
Voici la première ligne
Et voici la deuxième ligne
```

Il existe bien sûr des cas où l'on souhaite qu'un antislash dans une chaîne de caractère soit juste un antislash, et non un code spécial. Si deux antislashes se succèdent, ils seront interprétés ensemble, et un seul sera laissé dans la valeur de la chaîne de caractères résultante. Voici comment la chaîne de caractères "_Un caractère de nouvelle ligne s'écrit comme `"`\n`"`._" peut être reécrite:

```
"Un caractère de nouvelle ligne s'écrit comme \"\\n\"."
```

{{id unicode}}

{{index [string, representation], Unicode, character}}

Les chaînes de caractères doivent elles aussi être modélisées sous forme de séries de bits pour pouvoir exister dans l'ordinateur. La façon dont JavaScript procède est basée sur la norme _((Unicode))_. Cette norme attribue un numéro à pratiquement tous les caractères dont vous pourriez avoir besoin, y compris les caractères grecs, arabes, japonais, arméniens, etc. Si nous avons un nombre pour chaque caractère, une chaîne peut être décrite par une séquence de chiffres.

{{index "UTF-16", emoji}}

Et c'est ce que fait JavaScript. Mais il y a une complication : La modélisation de JavaScript utilise 16 bits par élément de chaîne, ce qui permet de décrire jusqu'à 2^16^ caractères différents. Mais l'Unicode définit plus de caractères que cela - environ deux fois plus, à ce stade. Ainsi, certains caractères, comme beaucoup d'emoji, prennent deux "positions de caractères" dans les chaînes JavaScript. Nous y reviendrons dans le [chapitre ?](higher_order#code_units).

{{index "+ operator", concatenation}}

Les chaînes de caractères ne peuvent pas être divisées, multipliées ou soustraites, mais l'opérateur `+` _peut_ être utilisé sur elles. Il n'additionne pas, mais il _concatène_- il colle deux chaînes ensemble. La ligne suivante produira la chaîne `"concatenate"`:

```
"con" + "cat" + "e" + "nate"
```

Les valeurs des chaînes de caractères ont un certain nombre de fonctions associées (_methods_) qui peuvent être utilisées pour effectuer d'autres opérations sur elles. J'en dirai plus à ce sujet au [chapitre ?](data#methods).

{{index interpolation, backtick}}

Les chaînes écrites avec des guillemets simples ou doubles se comportent de la même manière, la seule différence étant le type de guillemet dont vous avez besoin pour échapper à l'intérieur de la chaîne. Les chaînes avec guillemets inversés, généralement appelées _((modèles littérales))_, peuvent faire quelques trucs de plus. En plus de pouvoir enjamber les lignes, elles peuvent aussi intégrer d'autres valeurs.

```
`La moitié de 100 est ${100 / 2}`
```

Lorsque vous écrivez quelque chose à l'intérieur de `${}` dans un modèle littéral, son résultat sera calculé, converti en une chaîne de caractères, et inséré à cette position. L'exemple produit "_la moitié de 100 est 50_".

## Opérateurs unaires

{{index operator, "typeof operator", type}}

Ce ne sont pas tous les opérateurs qui sont des symboles. Certains sont écrits sous forme de mots. Il en est ainsi par exemple de l'opérateur `typeof`, qui produit une valeur de chaîne désignant le type de la valeur que vous lui donnez.

```
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

{{index "console.log", output, "JavaScript console"}}

{{id "console.log"}}

Nous utiliserons `console.log` dans le code en exemple pour indiquer que nous voulons voir le résultat de l'évaluation de quelque chose. Plus d'informations à ce sujet dans le [chapitre suivant](program_structure).

{{index negation, "- operator", "binary operator", "unary operator"}}

Les autres opérateurs présentés ont tous fonctionné sur deux valeurs, mais `typeof` n'en prend qu'une. Les opérateurs qui utilisent deux valeurs sont appelés opérateurs _binaires_, tandis que ceux qui n'en prennent qu'une sont appelés opérateurs _unaires_. L'opérateur `-` peut être utilisé à la fois comme un opérateur binaire et comme un opérateur unaire.

```
console.log(- (10 - 2))
// → -8
```

## Valeurs booléennes

{{index Boolean, operator, true, false, bit}}

Il est souvent utile d'avoir une valeur qui ne distingue que deux possibilités, comme "oui" et "non" ou "on" et "off". À cette fin, JavaScript a un type _booléen_, qui n'a que deux valeurs, true et false, qui s'écrivent en toutes lettres.

### Comparaison

{{index comparison}}

Voici une façon de produire des valeurs booléennes:

```
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

{{index [comparison, "of numbers"], "> operator", "< operator", "greater than", "less than"}}

Les signes `>` et `<` sont respectivement les symboles traditionnels de " est supérieur à " et " est inférieur à ". Ce sont des opérateurs binaires. En les appliquant, on obtient une valeur booléenne qui indique s'ils sont vrais dans ce cas.

Les cordes peuvent être comparées de la même manière.

```
console.log("Aardvark" < "Zoroaster")
// → true
```

{{index [comparison, "of strings"]}}

En principe, les chaînes de caractères sont classées par ordre alphabétique, mais ce n'est pas vraiment ce à quoi on s'attendrait dans un dictionnaire : les lettres majuscules sont toujours "moins" que les minuscules, donc `"Z" < "a"`, et les caractères non alphabétiques ( !, -, etc.) sont également inclus dans le classement. Lors de la comparaison des chaînes de caractères, JavaScript passe sur les caractères de gauche à droite, en comparant les codes ((Unicode)) un par un.

{{index equality, ">= operator", "<= operator", "== operator", "!= operator"}}

Les autres opérateurs similaires sont `>=` (supérieur ou égal à), `<=` (inférieur ou égal à), `==` (égal à), et `!=` (non égal à).

```
console.log("Itchy" != "Scratchy")
// → true
console.log("Apple" == "Orange")
// → false
```

{{index [comparison, "of NaN"], NaN}}

Il n'y a qu'une seule valeur dans JavaScript qui n'est pas égale à elle-même, et il s'agit de `NaN` ("not a number", pas un nombre).

```
console.log(NaN == NaN)
// → false
```

Le terme `NaN` est censé désigner le résultat d'un calcul absurde, et en tant que tel, il n'est pas égal au résultat d'un _autre_ calcul absurde.

### Opérateurs logiques

{{index reasoning, "logical operators"}}

Certaines opérations peuvent également être appliquées aux valeurs booléennes elles-mêmes. JavaScript prend en charge trois opérateurs logiques : _et_, _or_, et _not_. Ils peuvent être utilisés pour "raisonner" sur les booléens.

{{index "&& operator", "logical and"}}

L'opérateur `&&` représente le _et_ logique. C'est un opérateur binaire, et son résultat n'est vrai que si les deux valeurs qui lui sont données sont vraies.

```
console.log(true && false)
// → false
console.log(true && true)
// → true
```

{{index "|| operator", "logical or"}}

L'opérateur `||` indique un _ou_ logique. Il produit vrai si l'une des valeurs qui lui sont données est vraie.

```
console.log(false || true)
// → true
console.log(false || false)
// → false
```

{{index negation, "! operator"}}

_Not_ est écrit comme un point d'exclamation (`!`). C'est un opérateur unaire qui retourne la valeur qui lui est donnée - `true` donne `false`, et `false` retourne `true`.

{{index precedence}}

Lorsque l'on mélange ces opérateurs booléens avec des opérateurs arithmétiques et autres, il n'est pas toujours évident de savoir quand il faut mettre des parenthèses. En pratique, on peut généralement s'en sortir en sachant que parmi les opérateurs que nous avons vus jusqu'à présent, `||` a la plus faible préséance, puis vient `&&`, puis les opérateurs de comparaison (`>`, `==`, et ainsi de suite), et enfin le reste. Cet ordre a été choisi de manière à ce que, dans des expressions typiques comme la suivante, le moins de parenthèses possible soient nécessaires:

```
1 + 1 == 2 && 10 * 10 > 50
```

{{index "conditional execution", "ternary operator", "?: operator", "conditional operator", "colon character", "question mark"}}

Le dernier opérateur logique dont je vais parler n'est pas unaire, ni binaire, mais _ternaire_, opérant sur trois valeurs. Il est écrit avec un point d'interrogation et un deux-points, comme ceci :

```
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

Celui-ci est appelé l'opérateur _conditionnel_ (ou parfois seulement, l'opérateur _ternaire_ ,puisqu'il est le seul opérateur de ce type dans la langue). La valeur à gauche du point d'interrogation "choisit" laquelle des deux autres valeurs sortira. Lorsqu'elle est vraie, elle choisit la valeur du milieu, et lorsqu'elle est fausse, elle choisit la valeur de droite.

## Valeurs vides

{{index undefined, null}}

Il y a deux valeurs spéciales, appelées `null` et `undefined`, qui sont utilisées pour indiquer l'absence d'une valeur _significative_. Elles sont elles-mêmes des valeurs, mais elles ne contiennent aucune information.

Beaucoup d'opérations dans le langage qui ne produisent pas de valeur significative (vous en verrez plus tard) génèrent des valeurs `undefined` simplement parce qu'elles doivent générer une _valeur.

La différence de signification entre `undefined` et `null` est un accident de la conception de JavaScript, et cela n'a pas d'importance la plupart du temps. Dans les cas où vous devez réellement vous préoccuper de ces valeurs, je recommandent de les traiter comme étant pour la plupart interchangeables.

## Conversion automatique de type

{{index NaN, "type coercion"}}

Dans l'introduction, j'ai mentionné que JavaScript fait tout son possible pour accepter presque tous les programmes que vous lui donnez, même ceux qui font des choses bizarres. Les expressions suivantes le démontrent bien :

```
console.log(8 * null)
// → 0
console.log("5" - 1)
// → 4
console.log("5" + 1)
// → 51
console.log("five" * 2)
// → NaN
console.log(false == 0)
// → true
```

{{index "+ operator", arithmetic, "* operator", "- operator"}}

Lorsqu'un opérateur est appliqué au "mauvais" type de valeur, JavaScript convertira discrètement cette valeur dans le type dont il a besoin, en utilisant un ensemble de règles qui, souvent, ne sont pas celles que vous souhaitez ou attendez. C'est ce qu'on appelle la _((coercition de type))_. Le `null` de la première expression devient `0`, et le `"5"` de la deuxième expression devient `5` (de la chaîne de caractères au nombre). Cependant, dans la troisième expression, `+` essaie la concaténation de chaînes de caractères avant l'addition numérique, de sorte que le `1` est converti en `"1"` (du nombre
à la chaîne de caractères).

{{index "type coercion", [number, "conversion to"]}}

Lorsque quelque chose qui ne correspond pas à un nombre de manière évidente (comme `"five"` ou `undefined`) est converti en un nombre, vous obtenez la valeur `NaN`. D'autres opérations arithmétiques sur `NaN` génèrent toujours du `NaN`, donc si vous obtenez l'une de ces valeurs à un endroit inattendu, recherchez les conversions accidentelles de type.

{{index null, undefined, [comparison, "of undefined values"], "== operator"}}

Lorsque l'on compare des valeurs du même type en utilisant `==`, le résultat est facile à prévoir : vous devriez obtenir true lorsque les deux valeurs sont identiques, sauf dans le cas de `NaN`. Mais lorsque les types diffèrent, JavaScript utilise un ensemble de règles compliquées et déroutantes pour déterminer ce qu'il faut faire. Dans la plupart des cas, il essaie simplement de convertir une des valeurs en le type de l'autre valeur. Cependant, lorsque les valeurs `null` ou `undefined` apparaissent sur l'un ou l'autre côté de l'opérateur, il ne produit true que si les deux côtés à la fois sont soit `null` soit `undefined`.

```
console.log(null == undefined);
// → true
console.log(null == 0);
// → false
```

Ce comportement est souvent utile. Lorsque vous voulez tester si une valeur a une valeur réelle au lieu d'être `null` ou `undefined`, vous pouvez la comparer à `null` avec l'opérateur `==` (ou `!=`).

{{index "type coercion", [Boolean, "conversion to"], "=== operator", "!== operator", comparison}}

Mais que faire si vous voulez vérifier si quelque chose se réfère à la valeur précise `false` ? Des expressions comme `0 == false` et `"" == false` sont toutes vraies en raison de la conversion automatique des types. Lorsque vous _ne_ voulez pas qu'une conversion de type se produise, il y a deux opérateurs supplémentaires : `===` et `!==`. Le premier vérifie si une valeur est _strictement_ égale à l'autre, et le second vérifie si elle n'est pas strictement égale. Ainsi, `"" === false` est faux comme prévu.

Je recommande d'utiliser les opérateurs de comparaison à trois caractères de manière préventive pour éviter que les conversions de type inattendues ne vous fassent trébucher. Mais lorsque vous êtes certain que les types des deux côtés seront identiques, il n'y a pas de problème avec en utilisant les opérateurs les plus courts.

### Court-circuitage des opérateurs logiques

{{index "type coercion", [Boolean, "conversion to"], operator}}

Les opérateurs logiques `&&` et `||` traitent des valeurs de différents types d'une manière particulière. Ils vont convertir la valeur de leur côté gauche en type booléen afin de décider de ce qu'il faut faire, mais selon l'opérateur et le résultat de cette conversion, ils retourneront soit la valeur _initiale_ de gauche, soit la valeur de droite.

{{index "|| operator"}}

L'opérateur `||`, par exemple, retournera la valeur placée à sa gauche lorsque celle-ci peut être convertie en true et retournera la valeur placée à sa droite dans le cas contraire. Cela a l'effet escompté lorsque les valeurs sont booléennes et il en va de même pour les valeurs d'autres types.

```
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

{{index "default value"}}

Nous pouvons utiliser cette fonctionnalité comme un moyen de recourir à une valeur par défaut. Si vous avez une valeur qui pourrait être vide, vous pouvez mettre "||" après elle ensuite une valeur de remplacement. Si la valeur initiale peut être convertie en false, vous obtiendrez la valeur de remplacement à la place. Les règles de conversion des chaînes et des nombres en valeurs booléennes stipulent que `0`, `NaN`, et la chaîne vide (`""`) comptent comme `false`, tandis que toutes les autres valeurs comptent comme `true`. Donc, `0 || -1` donne `-1`, et `"" || "!?"` renvoie `"!?"`.

{{index "&& operator"}}

L'opérateur `&&` fonctionne de la même manière, mais dans l'autre sens. Lorsque la valeur à sa gauche peut se convertir en false, il renvoie cette valeur, sinon, elle rend la valeur placée à sa droite.

Une autre propriété importante de ces deux opérateurs est que la valeur placée à droite n'est évaluée que lorsque cela est nécessaire. Dans le cas de `true || X`, peu importe la valeur de `X` - même si c'est un morceau de programme qui fait quelque chose de _formidable_ - le résultat sera true, et `X` ne sera jamais évalué. Il en va de même pour `false && X`, qui est false et ignorera `X`.  Cela s'appelle l'_((évaluation en court-circuit))_.

{{index "ternary operator", "?: operator", "conditional operator"}}

L'opérateur conditionnel fonctionne de manière similaire. Entre la deuxième et la troisième valeur, seule celle qui est sélectionnée est évaluée.

## Résumé

Nous avons étudié quatre types de valeurs JavaScript dans ce chapitre: les nombres, les chaînes de caractères, les booléens et les valeurs non définies.

Ces valeurs sont créées en saisissant leurs noms (`true`, `null`) ou valeurs (`13`, `"abc"`). Vous pouvez combiner et transformer des valeurs avec opérateurs. Nous avons vu des opérateurs binaires pour l'arithmétique (`+`, `-`, `*`, `/`, et `%`), la concaténation de chaînes (`+`), la comparaison (`==`, `!=`, `===`, `!==`, `<`, `>`, `<=`, `>=`), et la logique (`&&`, `||`), ainsi que plusieurs opérateurs unaires (`-` pour rendre un nombre négatif, `!` pour inverser sa valeur booléenne, et `typeof` pour trouver le type d'une valeur) et un opérateur ternaire (`?:`) pour choisir une des deux valeurs basées sur une troisième valeur.

Cela vous donne suffisamment d'informations pour utiliser JavaScript comme une calculatrice de poche, mais pas davantage. Le [chapitre suivant](program_structure) commencera à relier ces expressions entre elles dans des programmes de base.
