Dnuos : Faire une liste !
=========================

Dnuos est un programme shell qui génère une liste de votre bibliothèque
musicale, en se basant sur la structure des dossiers.

Par exemple, une liste pourrait ressembler à ceci :

    Album/Artiste                      | Taill | Type | Qualité
    ===========================================================
    Ambient                            |       |      |
        Alva Noto                      |       |      |
            2001 - Transform           | 70,9M | MP3  | -V2
            2004 - Transrapid          | 30,2M | MP3  | -aps
            2005 - Transspray          | 31,7M | MP3  | -aps
            2005 - Transvision         | 32,3M | MP3  | -aps
        Alva Noto and Ryuichi Sakamoto |       |      |
            2002 - Vrioon              | 72,6M | MP3  | -aps
            2005 - Insen               | 99,1M | MP3  | 320 C
            2006 - Revep               | 27,9M | MP3  | -V2n

Le format de la liste est complètement personnalisable. On peut générer du
texte brut ou du code HTML.

Dnuos supporte les formats MP3, AAC, Musepack, Ogg Vorbis, et FLAC. Une
détection des profils de qualité est effectuée, notamment par les informations
du [LAME quality preset][].

Les informations sur les fichiers audio sont enregistrées sur le disque dur
lorsque la liste est générée pour la première fois, ce qui permet d'accélèrer
la création des listes ultérieures. En effet, seuls les fichiers audio et les
dossiers qui ont été modifiés depuis lors seront analysés.

Dnuos est basé sur le code d'[Oidua][]. Oidua peut générer des listes
similaires, mais c'est un très vieux programme moins puissant, qui n'est plus
maintenu.

[LAME quality preset]: https://wiki.hydrogenaud.io/index.php?title=Lame#Recommended_encoder_settings
[Oidua]: https://oidua.suxbad.com


Télécharger
-----------

Voici <https://github.com/brodie/dnuos>.


Installation / Utilisation
--------------------------

Lancez `dnuos --help` pour des informations détaillées sur toutes les options.

### Linux, Mac OS X, Unix

Extrayez l'archive et exécutez `setup.py` pour l'installer :

    tar zxvf dnuos-1.0.11.tar.gz
    cd dnuos-1.0.11
    sudo python2 setup.py install

Cela installera un script nommé `dnuos` dans `/usr/local/bin`.
(Sous Mac OS X 10.4 et les anciennes versions, il peut être placé dans
`/Library/Frameworks/Python.framework/Versions/Current/bin`.)

Après l'installation, ouvrez votre terminal préféré et exécutez `dnuos`.
Sur Mac OS X, *Terminal* serait un bon choix (situé dans
`/Applications/Utilities`).


### Windows

Il n'y a pas d'installation à proprement parler. Extrayez simplement le
fichier zip à l'endroit où vous souhaitez l'installer. Vous pouvez exécuter
l'application avec la commande `dnuos.exe`.

Pour ce faire, après avoir extrait Dnuos, appuyez simultanément sur les
touches Windows et R pour ouvrir la fenêtre *Commande*. Tapez *cmd* et
appuyez sur enter pour lancer la ligne de commande. Ensuite, tapez la lettre
du disque dur où l'exécutable est placé et `cd [le dossier]` pour aller au bon
emplacement. Une fois rendu dans le bon dossier, exécutez `dnuos.exe`.


### Interfaces graphiques

Si vous êtes allergique à la ligne de commande, vous pouvez utiliser l'une
des interfaces graphiques suivantes :

* [Guidua][] - Un front-end graphique pour Windows.

[Guidua]: https://oidua.suxbad.com/setup_guidua_0.16.exe


Quoi de neuf
------------

### Version 1.0.11 (18 jui. 2010)

* Voyez le README anglais.

### Version 1.0.10 (13 fév. 2009)

* Corrigé l'installation par dessus une installation egg.
* Corrigé l'ordre des fichiers individuels dans la sortie.
* Corrigé la trace apparaissant pour des fichiers ou répertoires
  non-existants.
* Ajouté le tri pour les entiers (`9.mp3` affiché avant `10.mp3`).
* Les fichiers individuels peuvent maintenant être passés comme arguments.
* Les chaînes sont reformattées en se basant sur la taille du terminal. La
  colonne de nom sera retaillée pour que la sortie s'adapte mieux à la sortie
  du terminal. *(Unix seulement)*
* Ajouté une mise en cache se basant sur SQLite, disponible sous Python 2.5.
  Le chargement du cache est bien plus rapide, et lors de la suppression
  d'entrées, la taille du cache est effectivement réduite.
* Meilleure compatibilité avec Python 2.6.
* Corrections de la localisation française (par Jean-Denis Vauguet).

### Version 1.0.9 (20 sep. 2008)

* Corrigé un plantage lors de l'utilisation du format de sortie HTML.
* Corrigé un plantage arrivant lors d'usage de symboles `=` dans les tags
  FLAC/Ogg Vorbis.
* `--delete-cache` supprime maintenant correctement le répertoire de cache.
* Les répertoires avec à la fois des MP3S LAME et non-LAME sont désormais
  détectés comme tels, au lieu d'être listés avec le quality preset LAME.
* Ajouté un raccourci `-C` pour `--disable-cache`.
* Ajouté un nouveau tag de sortie, `[Y]` (year) pour l'année.
* Rétabli le tag de profondeur `[D]` (depth).
* Meilleure compatibilité avec Python 2.6.
* L'encodage préferé est maintenant utilisé pour la sortie sur le terminal.
  (Les caractères qui ne peuvent pas être encodés sont remplacés par des
  points d'interrogation.)
* Corrigé la localisation française.
* Corrigé le fait que la localisation française ne soit pas installée avec
  `easy_install`.

### Version 1.0.8 (16 jui. 2008)

* Corrigé des plantages sous les environnements Unix avec les noms de
  dossiers qui ont des caractères qui ne sont pas compatibles avec
  l'encodage du système de fichiers.

### Version 1.0.7 (3 jui. 2008)

* Ajouté les améliorations de portabilité du Makefile à `setup.py`.
  `make` n'est pas toujours disponible, donc `setup.py` est maintenant
  recommandé.

### Version 1.0.6 (31 mai 2008)

* Changé le lieu du cache sous Linux de `~/.dnuos` à `~/.cache/dnuos`
  (`$XDG_CACHE_HOME/dnuos`).
* Amélioré la portabilité du Makefile. C'est maintenant le moyen
  recommandé pour installer Dnuos.
* Corrigé l'information d'album et d'artiste pas étant rempli avec
  les fichiers FLAC.
* Corrigé des plantages possibles d'UTF-8 avec des noms de fichiers qui
  ne sont pas encodés avec l'encodage du système de fichiers.

### Version 1.0.5 (5 mai 2008)

* Corrigé des plantages possibles du passage à l'UTF-8 du format du cache.

### Version 1.0.4 (4 mai 2008)

* Fortement amélioré l'appui pour les noms de fichiers et dossiers avec
  des caractères Unicode sous Windows. Dnuos devrait maintenant être
  capable de scanner des dossiers et ouvrir des fichiers avec des
  caractères Unicode dans leurs noms, et des caractères Unicode
  peuvent maintenant être utilisés dans des arguments de ligne de
  commande.
* Amélioré l'appui du format du cache entre les versions de Python.

### Version 1.0.3 (27 avr. 2008)

* Corrigé un plantage avec des variables locales mal formés
  d'environnement (par ex. `LANG`, `LC_ALL`, etc.)
* Corrigé la sortie incorrecte lorsque scanner des dossiers racines sous
  Windows (par ex. `C:\`).

### Version 1.0.2 (29 mar. 2008)

* Corrigé `-V`/`--version` ne fonctionne pas avec la sortie normale.

### Version 1.0.1 (24 mar. 2008)

* Amélioré la sortie des tags ID3 avec des caractères null.
* Corrigé la compatilibité Python 2.3.
* Corrigé un plantage possible avec le cache sous certains
  environnements Mac OS X.

### Version 1.0 (20 mar. 2008)

* Ajouté le cachage des métadonnées audio.
* Ajouté une traduction française et l'appui pour le formatage des nombres par
  les paramètres régionaux.
* Ajouté `-L`/`--list-files` pour lister les fichiers individuels dans des
  dossiers. Néanmoins, l'information des fichiers individuels n'est pas caché.
* Ajouté `-u`/`--unknown-types` pour lister les dossiers avec les fichiers
  non soutenus.
* Ajouté l'appui pour calculer les bitrates des fichiers AAC.
* Ajouté une balise de sortie `[V]` qui affiche l'information du encodeur
  (actuellement seulement pour MP3).
* Corrigé le traitement des MP3 avec l'en-tête VBRI (par ex. fait par
  Fraunhofer).
* Nettoyé les messages d'aide.
* Supprimé l'appui pour Python 2.2.


Développement
-------------

Le dépôt officiel de développement est situé à
<https://github.com/brodie/dnuos>. Avec [Git][], exécutez :

    git clone https://github.com/brodie/dnuos.git

Exécuter les tests unitaires nécessite d'avoir les [données de test][] (dans
le même dossier que `setup.py`). Une fois que vous les avez récupérée, vous
pouvez exécuter les tests avec la commande suivante :

    python2 setup.py test

Voici [GitHub][] pour forker le projet, surveillez de nouveaux changements,
ou pour faites un rapport de bogue.

[Git]: https://git-scm.com
[test data]: https://bitheap.org/dnuos/files/testdata.zip
[GitHub]: https://github.com/brodie/dnuos


Contacter
---------

### Contributeurs retirés

* [brodie](https://github.com/brodie)
* [Mattias Päivärinta](https://github.com/mattias-p)
* frunksock
