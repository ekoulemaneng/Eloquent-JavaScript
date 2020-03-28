{{meta {load_files: ["code/intro.js"]}}}

# Introduction

{{quote {author: "Ellen Ullman", title: "Close to the Machine: Technophilia and its Discontents", chapter: true}

Nous pensons que nous créons le système pour nos propres besoins. Nous pensons que nous le faisons à notre propre image... Mais l'ordinateur n'est pas vraiment comme nous. Il est la projection d'une partie très mince de nous-mêmes : celle qui est consacrée à la logique, à l'ordre, à la règle et à la clarté.

quote}}

{{figure {url: "img/chapter_picture_00.jpg", alt: "Photo d'un tournevis et d'une carte de circuit imprimé", chapter: "framed"}}}

Ce livre traite des techniques visant à donner des instructions aux ((ordinateur))s. Les ordinateurs sont à peu près aussi répandus que les tournevis aujourd'hui, mais ils sont un peu plus complexes, et il n'est pas toujours facile de leur faire faire ce que vous voulez qu'ils fassent.

Si la tâche que vous demandez à votre ordinateur d'effectuer est banale et bien définie, par exemple vous afficher votre courrier électronique ou vous servir de calculatrice, vous pouvez ouvrir l'((application)) appropriée et vous mettre au travail. Mais pour les tâches singulières ou ouvertes, il n'y a probablement pas d'application.

C'est ici que la ((programmation)) peut entrer en jeu. La _programmation_ est l'action qui consiste à construire un _programme_, c'est-à-dire un ensemble d'instructions précises indiquant à un ordinateur ce qu'il doit faire. Les ordinateurs étant des créatures stupides et pointilleuses, la programmation est foncièrement fastidieuse et frustrante.

{{index [programming, "joy of"], speed}}

Heureusement, si vous arrivez à surmonter ce fait, et peut-être même à apprécier la rigueur de la pensée en des termes que des machines stupides peuvent assimiler, la programmation peut être enrichissante. Elle vous permet de faire en quelques secondes des choses qui prendraient à la main _une éternité_. C'est un moyen de faire faire à votre outil informatique des choses qu'il ne pouvait pas faire auparavant. Et c'est un merveilleux exercice de pensée abstraite.

La plupart des programmes sont réalisés avec des ((langages de programmation)). Un _langage de programmation_ est un langage construit artificiellement et utilisé pour donner des instructions aux ordinateurs. Il est intéressant de constater que le moyen le plus efficace que nous ayons trouvé pour communiquer avec un ordinateur est fortement inspiré de la façon dont nous communiquons entre nous. Tout comme les langues humaines, les langages informatiques permettent de combiner des mots et des phrases de manière nouvelle, ce qui permet d'exprimer des concepts toujours nouveaux.

{{index [JavaScript, "availability of"], "casual computing"}}

À un moment donné, les interfaces basées sur des langages, tels que les invites de commande BASIC et DOS dans les années 1980 et 1990, étaient la principale méthode d'interaction avec les ordinateurs. Ils ont été largement remplacées par des interfaces graphiques, qui sont plus faciles à apprendre mais offrent moins de liberté. Les langages informatiques sont toujours là, si vous savez où chercher. L'un de ces langages, JavaScript, est intégré à tous les ((navigateurs)) web modernes et est donc disponible sur presque tous les appareils.

{{indexsee "web browser", browser}}

Ce livre tentera de vous familiariser suffisamment avec ce langage pour vous permettre de faire des choses utiles et amusantes.

## A propos de la programmation

{{index [programming, "difficulty of"]}}

En plus d'expliquer le langage JavaScript, je présenterai les principes de base de la programmation. Il s'avère que la programmation est difficile. Les règles fondamentales sont simples et claires, mais les programmes construits sur la base de ces règles ont tendance à devenir suffisamment complexes pour introduire leurs propres règles et leur propre complexité. Vous construisez votre propre labyrinthe, d'une certaine manière, et vous risquez de vous y perdre.

{{index learning}}

Il y aura des moments où la lecture de ce livre sera terriblement frustrante. Si vous êtes nouveau dans la programmation, il y aura beaucoup de nouveaux éléments à digérer. Une grande partie de ce matériel sera alors _combiné_ d'une façon qui vous obligera à faire des connexions supplémentaires.

C'est à vous de faire les efforts nécessaires. Lorsque vous avez du mal à suivre le livre, ne tirez pas de conclusions hâtives sur vos propres capacités. Vous êtes sur la bonne voie, il vous suffit de continuer. Faites une pause, relisez quelques documents et assurez-vous de lire et de comprendre les exemples de programmes et d'exercices. L'apprentissage est un travail difficile, mais tout ce que vous apprenez vous appartient et facilitera l'apprentissage ultérieur.

{{quote {author: "Ursula K. Le Guin", title: "La Main gauche de la nuit"}

{{index "Le Guin, Ursula K."}}

Lorsque l'action devient peu fructueuse, rassemblez des informations ; lorsque l'information devient peu fructueuse, dormez.

quote}}

{{index [program, "nature of"], data}}

Un programme, c'est beaucoup de choses. C'est un morceau de texte saisi par un programmeur, c'est la force directrice qui fait faire à l'ordinateur ce qu'il fait, ce sont des données dans la mémoire de l'ordinateur, et pourtant il contrôle les actions effectuées sur cette même mémoire. Les analogies qui tentent de comparer des programmes à des objets qui nous sont familiers ont tendance à se révéler insuffisantes. Une analogie superficielle est celle d'une machine - beaucoup de pièces détachées sont impliquées, et pour faire fonctionner l'ensemble, nous devons considérer les façons dont ces pièces s'interconnectent et contribuent au fonctionnement de l'ensemble.

Un ((ordinateur)) est une machine physique qui agit comme un hôte pour des machines virtuelles. Les ordinateurs eux-mêmes ne peuvent faire que des choses ridiculement simples. La raison pour laquelle ils sont si utiles est qu'ils font ces choses à une ((vitesse)) incroyablement élevée. Un programme peut ingénieusement combiner un nombre énorme de ces actions simples pour faire des choses très compliquées.

{{index [programming, "joy of"]}}

Un programme est une construction de la pensée. Il ne coûte rien à construire, il est léger et il se développe facilement sous nos mains dactylographiques.

Mais si l'on n'y prend garde, la taille et la ((complexité)) d'un programme deviendront de plus en plus incontrôlables, semant la confusion même chez son créateur. Garder les programmes sous contrôle est le principal problème de la programmation. Quand un programme fonctionne, il est beau. L'art de la programmation est la capacité à contrôler la complexité. Le superbe programme est maîtrisé, rendu simple dans sa complexité.

{{index "programming style", "best practices"}}

Certains programmeurs pensent que la meilleure façon de gérer cette complexité est de n'utiliser qu'un petit ensemble de techniques bien assimilées dans leurs programmes. Ils ont composé des règles strictes ("meilleures pratiques") prescrivant la forme que les programmes devraient avoir et restent soigneusement dans leur petite zone de confort.

{{index experiment}}

Non seulement c'est barbant, mais c'est inefficace. Les nouveaux problèmes exigent souvent de nouvelles solutions. Le domaine de la programmation est jeune et se développe encore rapidement, et il est suffisamment varié pour laisser la place à des approches radicalement différentes. Il y a beaucoup de graves erreurs à faire lors de la conception des programmes, et vous devriez les commettre pour les comprendre. C'est dans la pratique que l'on se fait une idée de ce à quoi ressemble un bon programme, et non à partir d'une liste de règles.

## Pourquoi la langage est importante

{{index "programming language", "machine code", "binary data"}}

Au début, à la naissance de l'informatique, il n'y avait pas de langages de programmation. Les programmes ressemblaient à quelque chose comme ça:

```{lang: null}
00110001 00000000 00000000
00110001 00000001 00000001
00110011 00000001 00000010
01010001 00001011 00000010
00100010 00000010 00001000
01000011 00000001 00000000
01000001 00000001 00000001
00010000 00000010 00000000
01100010 00000000 00000000
```

{{index [programming, "history of"], "punch card", complexity}}

Il s'agit d'un programme permettant d'additionner les chiffres de 1 à 10 et d'imprimer le résultat : `1 + 2 + ... + 10 = 55`. Il pourrait fonctionner sur une machine simple théorique. Pour programmer les premiers ordinateurs, il était nécessaire de placer de grands ensembles de commutateurs dans la bonne position ou de percer des trous dans des bandes de carton et de les introduire dans l'ordinateur. Vous pouvez probablement imaginer à quel point cette procédure était fastidieuse et sujette à l'erreur. Même l'écriture de programmes simples exigeait beaucoup d'intelligence et de discipline. Les programmes complexes étaient presque inconcevables.

{{index bit, "wizard (mighty)"}}

Évidemment, la saisie manuelle de ces mystérieux motifs de bits (les uns et les zéros) a donné au programmeur le sentiment profond d'être un puissant magicien. Et cela doit valoir quelque chose en termes de satisfaction professionnelle.

{{index memory, instruction}}

Chaque ligne du programme précédent contient une seule instruction. Elle pourrait être écrite en français comme suit:

 1. Stockez le nombre 0 dans l'emplacement mémoire 0.
 2. Stockez le nombre 1 dans l'emplacement mémoire 1.
 3. Stockez la valeur de l'emplacement de mémoire 1 dans l'emplacement de mémoire 2.
 4. Soustrayez le nombre 11 de la valeur de l'emplacement mémoire 2.
 5. Si la valeur de l'emplacement mémoire 2 est le nombre 0, allez à l'instruction 9.
 6. Ajoutez la valeur de l'emplacement de mémoire 1 à celle de l'emplacement de mémoire 0.
 7. Ajoutez le nombre 1 à la valeur de l'emplacement de mémoire 1.
 8. Allez à l'instruction 3.
 9. Donnez la valeur de l'emplacement de mémoire 0.

{{index readability, naming, binding}}

Bien que cela soit déjà plus lisible que la soupe de bits, c'est encore assez obscur. L'utilisation de noms au lieu de nombres pour les instructions et les emplacements de mémoire est utile.

```{lang: "text/plain"}
 Affecter 1 à “count”.
[boucle]
 Affecter (la valeur de) “compare” à “count”.
 Soustraire 11 à “compare”.
 Si “compare” est égal à zéro, aller à la [fin].
 Ajouter (la valeur de) “count” à (celle de) “total” (et affecter le résultat à "total").
 Ajouter 1 à “count”.
 Aller à [boucle].
[fin]
 Afficher “total”
```

{{index loop, jump, "summing example"}}

Pouvez-vous voir comment le programme fonctionne à ce stade ? Les deux premières lignes donnent à deux emplacements mémoire leurs valeurs de départ : `total` sera utilisé pour construire le résultat du calcul, et `count` gardera la trace du nombre que nous sommes en train d'examiner. Les lignes utilisant `compare` sont probablement les plus bizarres. Le programme veut voir si `count` est égal à 11 pour décider s'il peut s'arrêter de fonctionner. Comme notre machine théorique est plutôt primitive, elle ne peut que tester si un nombre est égal à zéro et prendre une décision en fonction de cela. Elle utilise donc l'emplacement mémoire appelé `compare` pour calculer la valeur de `count - 11` et prend une décision basée sur cette valeur. Les deux lignes suivantes ajoutent la valeur de `count` au résultat et incrémentent `count` de 1 chaque fois que le programme a décidé que `count` n'est pas encore 11.

Voici le même programme en JavaScript:

```
let total = 0, count = 1;
while (count <= 10) {
  total += count;
  count += 1;
}
console.log(total);
// → 55
```

{{index "while loop", loop, [braces, block]}}

Cette version nous apporte quelques améliorations supplémentaires. Plus important encore, il n'est plus nécessaire de spécifier la façon dont nous voulons que le programme fasse des allers-retours. La construction `while` s'en charge. Il continue d'exécuter le bloc (entouré d'accolades) situé en dessous tant que la condition qui lui a été donnée est maintenue. Cette condition est `count <= 10`, ce qui signifie que "_count_ est inférieur ou égal à 10". Nous n'avons plus besoin de créer une valeur temporaire et de la comparer à zéro, ce qui n'était qu'un détail inintéressant. Une partie de la puissance des langages de programmation est qu'ils peuvent s'occuper de détails inintéressants pour nous.

{{index "console.log"}}

At the end of the program, after the `while` construct has finished,
the `console.log` operation is used to write out the result.

À la fin du programme, lorsque la structure `while` est achevée, l'opération `console.log` est utilisée pour afficher le résultat.

{{index "sum function", "range function", abstraction, function}}

Enfin, voici à quoi pourrait ressembler le programme si nous disposions des opérateurs pratiques `range` et `sum`, qui créent respectivement une ((série)) de nombres dans une plage et calculent la somme d'une collection de nombres:

```{startCode: true}
console.log(sum(range(1, 10)));
// → 55
```

{{index readability}}

La morale de cette histoire est que le même programme peut être exprimé de manière longue ou courte, illisible ou lisible. La première version du programme était extrêmement obscure, alors que cette seconde version est presque en français : afficher (`log`) la somme (`sum`) d'une série (`range`) de nombres compris entre 1 et 10. (Nous verrons dans [les prochains chapitres](data) comment définir des opérations comme `sum` et `range`).

{{index ["programming language", "power of"], composability}}

A good programming language helps the programmer by allowing them to
talk about the actions that the computer has to perform on a higher
level. It helps omit details, provides convenient building blocks
(such as `while` and `console.log`), allows you to define your own
building blocks (such as `sum` and `range`), and makes those blocks
easy to compose.

Un bon langage de programmation aide le programmeur en lui permettant de parler des actions que l'ordinateur doit effectuer à un niveau supérieur. Il permet d'omettre des détails, fournit des blocs de structure appropriés (tels que `while` et `console.log`), vous permet de définir vos propres blocs de structure (tels que `sum` et `range`), et rend ces blocs faciles à composer.

## Qu'est-ce que JavaScript?

{{index history, Netscape, browser, "web application", JavaScript, [JavaScript, "history of"], "World Wide Web"}}

{{indexsee WWW, "World Wide Web"}}

{{indexsee Web, "World Wide Web"}}

Le JavaScript a été lancé en 1995 comme moyen d'ajouter des programmes aux pages web dans le navigateur Netscape Navigator. Ce langage a depuis été adopté par tous les autres grands navigateurs graphiques. Il a rendu possible les applications web modernes - des applications avec lesquelles vous pouvez interagir directement sans avoir à recharger une page pour chaque action. Le JavaScript est également utilisé dans des sites web plus traditionnels pour offrir diverses formes d'interactivité et d'intelligence.

{{index Java, naming}}

Il est important de noter que JavaScript n'a presque rien à voir avec le langage de programmation appelé Java. Ce nom proche a été inspiré par des considérations de marketing plutôt que par un bon jugement. Lorsque JavaScript a été lancé, le langage Java faisait l'objet d'un marketing intensif et gagnait en popularité. Quelqu'un a pensé que c'était une bonne idée d'essayer de surfer sur ce succès. Aujourd'hui, nous sommes coincés avec ce nom.

{{index ECMAScript, compatibility}}

Après son adoption au delà de Netscape, un document ((standard)) a été rédigé pour décrire la façon dont le langage JavaScript devrait fonctionner afin que les différents logiciels qui prétendaient supporter JavaScript parlent en fait du même langage. C'est ce qu'on appelle la norme ECMAScript, du nom de l'organisation Ecma International qui a procédé à la normalisation. Dans la pratique, les termes ECMAScript et JavaScript peuvent être utilisés de manière interchangeable - ce sont deux noms désignant le même langage.

{{index [JavaScript, "weaknesses of"], debugging}}

Il y a ceux qui diront des choses _terribles_ sur JavaScript. Beaucoup de ces choses sont vraies. Quand on m'a demandé d'écrire quelque chose sur JavaScript pour la première fois, j'en suis vite venu à le mépriser. Il acceptait presque tout ce que je tapais, mais l'interprétait d'une manière complètement différente de ce que je voulais dire. Cela tenait beaucoup au fait que je n'avais pas la moindre idée de ce que je faisais, bien sûr, mais il y a là un véritable problème : JavaScript est extrêmement permissif dans ce qu'il permet. L'idée derrière cette conception était de rendre la programmation en JavaScript plus facile pour les débutants. En réalité, il rend surtout plus difficile la détection des problèmes dans vos programmes parce que le système ne vous les signalera pas.

{{index [JavaScript, "flexibility of"], flexibility}}

Mais cette flexibilité a aussi ses avantages. Elle laisse de la place pour de nombreuses techniques impossibles dans des langages plus rigides et, comme vous le verrez (par exemple dans le [chapitre ?](modules)), elle peut être utilisée pour surmonter certaines des lacunes de JavaScript. Après ((avoir appris)) le langage correctement et travaillé avec lui pendant un certain temps, j'ai appris à vraiment _aimer_ JavaScript.

{{index future, [JavaScript, "versions of"], ECMAScript, "ECMAScript 6"}}

Il y a eu plusieurs versions de JavaScript. La version 3 de l'ECMAScript était la version la plus largement soutenue à l'époque de la montée en puissance de JavaScript, entre 2000 et 2010 environ. Pendant cette période, des travaux étaient en cours sur une ambitieuse version 4, qui prévoyait un certain nombre d'améliorations et d'extensions substantielles du langage. Changer un langage dynamique et largement utilisé de manière aussi radicale s'est avéré politiquement difficile, et le travail sur la version 4 a été abandonné en 2008, pour aboutir à une version 5 beaucoup moins ambitieuse, qui n'a apporté que quelques améliorations non controversées, et qui est sortie en 2009. Puis, en 2015, la version 6 est sortie, une mise à jour majeure qui comprenait certaines des idées prévues pour la version 4. Depuis lors, nous avons eu de nouvelles petites mises à jour chaque année.

Le fait que le langage évolue implique que les navigateurs doivent constamment suivre le rythme, et si vous utilisez un navigateur plus ancien, il peut ne pas prendre en charge toutes les fonctionnalités. Les concepteurs du langage font attention à ne pas apporter de modifications qui pourraient casser les programmes existants, de sorte que les nouveaux navigateurs peuvent toujours exécuter les anciens programmes. Dans ce livre, j'utilise la version 2017 de JavaScript.

{{index [JavaScript, "uses of"]}}

Web browsers are not the only platforms on which JavaScript is used.
Some databases, such as MongoDB and CouchDB, use JavaScript as their
scripting and query language. Several platforms for desktop and server
programming, most notably the ((Node.js)) project (the subject of
[Chapter ?](node)), provide an environment for programming JavaScript
outside of the browser.

Les navigateurs web ne sont pas les seules plateformes sur lesquelles le JavaScript est utilisé. Certaines systèmes de gestion de bases de données, tels que MongoDB et CouchDB, utilisent JavaScript comme langage de script et de requête. Plusieurs plateformes de programmation pour desktop et serveur, notamment le projet ((Node.js)) (le sujet du [chapitre ?](node)), fournissent un environnement pour la programmation de JavaScript en dehors du navigateur.

## Le code et ce qu'il faut en faire

{{index "reading code", "writing code"}}

Le _code_ est le texte qui constitue les programmes. La plupart des chapitres de ce livre contiennent beaucoup de code. Je suis convaincu que la lecture et l'écriture du code sont des éléments indispensables pour ((apprendre)) à programmer. Essayez de ne pas vous contenter de jeter un coup d'œil sur les exemples - lisez-les attentivement et comprenez-les. Cela peut être lent et déroutant au début, mais je vous promets que vous y arriverez rapidement. Il en va de même pour les exercices. Ne supposez pas que vous les comprenez avant d'avoir réellement écrit une solution valable.

{{index interpretation}}

Je vous recommande de tester vos solutions aux exercices dans un véritable interpréteur JavaScript. Ainsi, vous aurez un retour d'information immédiat sur la validité de ce que vous faites et, je l'espère, vous serez tenté d'expérimenter et d'aller au-delà des exercices.

{{if interactive

Lorsque vous lirez ce livre dans votre navigateur, vous pourrez modifier (et exécuter) tous les exemples de programmes en cliquant dessus.

if}}

{{if book

{{index download, sandbox, "running code"}}

La façon la plus simple d'exécuter le code des exemples du livre et de le tester est de le consulter dans la version en ligne du livre à l'adresse [_https://eloquentjavascript.net_](https://eloquentjavascript.net/). Une fois sur cette page, vous pouvez cliquer sur n'importe quel exemple de code pour l'éditer et l'exécuter et pour voir le résultat qu'il produit. Pour travailler sur les exercices, cliquez sur [_https://eloquentjavascript.net/code_](https://eloquentjavascript.net/code), qui fournit un code de départ pour chaque exercice de codage et vous permet d'examiner les solutions.

if}}

{{index "developer tools", "JavaScript console"}}

Si vous souhaitez exécuter les programmes définis dans ce livre en dehors de son site web, il vous faudra faire preuve de prudence. De nombreux exemples se suffisent à eux-mêmes et devraient fonctionner dans n'importe quel environnement JavaScript. Mais le code des chapitres ultérieurs est souvent écrit pour un environnement spécifique (le navigateur ou Node.js) et ne peut être exécuté que dans cet environnement. En outre, de nombreux chapitres définissent des programmes plus importants, et les morceaux de code qui y figurent dépendent les uns des autres ou de fichiers externes. Le [bac à sable](https://eloquentjavascript.net/code) du site web fournit des liens vers des fichiers zip contenant tous les scripts et fichiers de données nécessaires pour exécuter le code d'un chapitre donné.

## Vue d'ensemble du livre

Ce livre comprend en gros trois parties. Les 12 premiers chapitres traitent du langage JavaScript. Les sept chapitres suivants concernent les ((navigateurs)) web et la façon dont JavaScript est utilisé pour interagir avec eux. Enfin, deux chapitres sont consacrés à ((Node.js)), un autre environnement pour programmer JavaScript.

D'un bout à l'autre du livre, il y a cinq _chapitres à projet_, qui contiennent des exemples de programmes plus importants pour vous donner un avant-goût de la programmation réelle. Par ordre chronologique, nous allons construire un [robot de livraison](robot), un [langage de programmation](language), un [jeu de plateformes](game), un [programme de peinture au pixel](paint), et un [site web dynamique](skillsharing).

La partie du livre consacrée au langage commence par quatre chapitres qui présentent la structure de base du langage JavaScript. Ils introduisent les [structures de contrôle](program_structure) (comme le mot `while` que vous avez vu dans cette introduction), les [fonctions](functions) (en écrivant vos propres blocs de construction), et les [structures de données](data). Après cela, vous serez en mesure d'écrire des programmes de base. Ensuite, les chapitres [?](higher_order) et [?](object) exposent des techniques permettant d'utiliser des fonctions et des objets pour écrire davantage de code _abstrait_ et garder la complexité sous contrôle.

Après un [premier chapitre à projet](robot), la partie du livre consacrée au langage se poursuit avec des chapitres sur la [gestion des erreurs et la correction des bugs](error), les [expressions régulières](regexp) (un outil important pour travailler avec du texte), la [modularité](modules) (une autre parade contre la complexité), et la [programmation asynchrone](async) (pour traiter des événements qui prennent du temps). Le [deuxième chapitre à projet](language) conclut la première partie du livre.

La deuxième partie, des chapitres [?](browser) à [?](paint), décrit les outils auxquels le JavaScript du navigateur a accès. Vous apprendrez à afficher des choses à l'écran (chapitres [?](dom) et [?](canvas)), répondre aux informations saisies par l'utilisateur ([Chapter ?](event)), et communiquer sur le réseau ([Chapter ?](http)). Cette partie comporte également deux chapitres à projet.

After that, [Chapter ?](node) describes Node.js, and [Chapter
?](skillsharing) builds a small website using that tool.

Par la suite, le [chapitre ?](node) décrit Node.js, et le [chapitre ?](skillsharing) construit un petit site web en utilisant cet outil.

{{if commercial

Enfin, le [chapitre ?](fast) décrit certaines des considérations soulevées lors de l'optimisation des programmes JavaScript pour améliorer la vitesse d'exécution.

if}}

## Typographic conventions

{{index "factorial function"}}

Dans ce livre, le texte écrit en police `monospaced` représentera des éléments de programmes - parfois ce sont des fragments autonomes, et parfois ils font simplement référence à une partie d'un programme voisin. Les programmes (dont vous avez déjà vu quelques-uns) sont écrits comme suit :

```
function factorial(n) {
  if (n == 0) {
    return 1;
  } else {
    return factorial(n - 1) * n;
  }
}
```

{{index "console.log"}}

Parfois, pour montrer le résultat qu'un programme produit, le résultat attendu est écrit en dessous, avec deux barres obliques et une flèche devant.

```
console.log(factorial(8));
// → 40320
```

Bonne chance!
