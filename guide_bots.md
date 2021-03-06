# Guide des bots

## Dynobot (Cotentin)

Dynobot est un bot multifonction. Pour le configurer, vous devez être membre de l'équipe technique.
[La page de configuration se trouve ici](https://www.dynobot.net/)

### Créer une nouvelle commande

Allez sur [la page de configuration de DynoBot](https://www.dynobot.net/), connectez-vous, puis sélectionnez le serveur « La Commune ». Dans le menu, cliquez sur « Custom Commands ». Dans l'onglet « Add Command », remplissez les champs « Command » (sans marquer le !) et « Response » (le code de votre commande). Validez avec « Add », attendez quelques minutes et testez votre commande.

### Modifier une commande

Allez sur [la page de configuration de DynoBot](https://www.dynobot.net/), connectez-vous, puis sélectionnez le serveur « La Commune ». Dans le menu, cliquez sur « Custom Commands ». Dans l'onglet « Commands », trouvez la commande à modifier. Copiez le code de la commande dans un fichier, puis cliquez sur « Remove » dans l'interface. Vous pouvez maintenant ajouter une version modifiée de cette commande comme décrit dans la séction « Créer une nouvelle commande ».
Attention, lorsque vous copiez le code de la commande, les retours à la ligne sont supprimez. Vous devez les ajouter vous-même.

### Commande d'acceptation des invité.e.s

La commande ``!public`` prend en paramètre le nom de la personne à passer en invité.e. Elle change les rôles de la personne et affiche une annonce dans #discussions_publique. Elle s'utilise de la façon suivante :

```
!public @LeNom#1234
```

Son code source est le suivant :

```
{require:Admis-es}
{delete}
{!role $1+ +A interroger, +Invité-e-s, -Nouveaux-lles}
{silent}
{respond:#discussions_publiques}
Bienvenue dans le salon publique, $1+ ! Tu peux discuter ici avec tout le monde en attendant le vocal de validation.
```

La ligne ``{require:Admis-es}`` permet de n'autoriser que les admis-es à utiliser cette commande.
La ligne ``{delete}`` indique à Dynobot de supprimer la commande tapée du salon.
La ligne ``{!role +A intéroger, +Invité-e-s, -Nouveaux.lles}`` permet de supprimer le rôle ``Nouveaux.lles`` et d'ajouter les rôles ``À interroger`` et ``Invité-e-s``.
La ligne ``{silent}`` permet de ne pas afficher le message automatique de Dynobot quand la commande ``!role`` est utilisée.
La ligne ``{respond:#discussions_publique}`` indique où afficher le message, indépendament d'où est tapée la commande.
Le reste de la commande représente le message à afficher. Le symbole ``#1+`` est remplacé par tout ce qui suivra après ``!public ``, c'est à dire le nom de l'utilisateur

### Commande d'acceptation des admis.es

La commande ``!admission`` prend en paramètre le nom de la personne à accepter. Elle change les rôles de la personne et affiche une annonce dans #general. Elle s'utilise de la façon suivante :

```
!admission @LeNom#1234
```

Son code source est le suivant :

```
{require:Modération}
{delete}
{!role $1+ +Admis-es, -A interroger, -Invité-e-s, -Nouveaux-lles}
{silent}
{respond:#general}
Bienvenue $1+ ! Maintenant que tu es admis-e, n'hésite pas à lire la {#constitution} et à suivre notre compte Twitter @LaCommuneNet. Tu peux t'ajouter tes propres étiquettes en cliquant sur ton pseudo, et n'hésite pas à nous dire si tu es concerné-e par un salon non mixte. Si tu as des abonnements à des journaux, des compétences en informatique ou en langue, tu peux aussi te mettre les rôles correspondants. Bonne continuation camarade !
```

La ligne ``{require:Modération}`` permet de n'autoriser que l'équipe de modération à utliser cette commande.
La ligne ``{delete}`` indique à Dynobot de supprimer la commande tapée du salon.
La ligne ``{!role +Admis-es, -A intéroger, -Invité-e-s, -Nouveaux.lles}`` permet de supprimer les rôles ``A intéroger``, ``Invité-e-s`` et ``Nouveaux.lles`` et d'ajouter le rôle ``Admis-es``.
La ligne ``{silent}`` permet de ne pas afficher le message automatique de Dynobot quand la commande ``!role`` est utilisée.
La ligne ``{respond:#general}`` indique où afficher le message, indépendament d'où est tapée la commande.
Le reste de la commande représente le message à afficher. Le symbole ``#1+`` est remplacé par tout ce qui suivra après ``!admission ``, c'est à dire le nom de l'utilisateur

## FredBoat

FredBoat est un bot pour difuser de la musique dans les salons vocaux.

## DuckHunt (Chasse aux fafs)

DuckHunt est me bot permetant de jouer dans le salon #chasse_aux_fafs.

## NotSoBot

NosSoBot est un bot permettant de faire du shitpost dans #shitpost.

## People's Democratic Bot

People's Democratic Bot est un bot permettant de faire des visuels détournés d'affiches de propagandes communistes.

## La Commune

La Commune est un bot fait par les membres de La Commune. Il permet de faire d'organiser des votes, de faire des annonces et de permettre aux admis·es de bannir.
Le code source de ce bot est [disponible ici](https://github.com/DiscordLaCommune/BotVote).

## Réseau Antifa

Le Réseau Antifa est un bot qui permet de bannir de façon synchronisée les fafs sur plusieurs serveurs en même temps. 

