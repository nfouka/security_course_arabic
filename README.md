Security course arabic
Cours de cryptage en arabe/english



Quel algorithme de chiffrement symétrique (symmetric cipher) choisir ?

Vous souhaitez installer OpenVPN, OpenPGP, OpenSSH ou une autre solution nécessitant l’utilisation d’un algorithme de chiffrement symétrique. Mais entre AES, Blowfish ou DES vous ne savez pas lequel choisir. Voici un comparatif afin de vous aider à choisir.

Un chiffrement symétrique utilise la même clé pour chiffrer et déchiffrer contrairement au chiffrement asymétrique qui utilise des clés différentes (en fait 2 clés : une clé publique, servant au chiffrement, et une clé privée, servant à déchiffrer).

Un rappel de la réglementation en vigueur en France me semble nécessaire. Toute information chiffrée par un algorithme à clef symétrique ne doit pas utiliser de clé supérieure à 128 bits (« service de confidentialité » défini par les décrets du 17 mars 1999, avec une clef de 128 bits).

Pour commencer, je ne vais présenter que les algorithmes le plus souvent rencontrés (la liste des algorithme étant existant étant très longue) : IDEA, TripleDES (DES est exclu du fait de sa lenteur et du fait de la possibilité d’une attaque systématique dans un temps raisonnable), CAST-5, blowfish et AES.

Avant de rentrer plus dans le détail, la solidité d’un algorithme dépend fortement de la taille de la clé. Une clé est une donnée qui permet de chiffrer et de déchiffrer une information après traitement par un algorithme. Par exemple, en 1997, une recherche exhaustive de clé de l’algorithme DES a été réussie. DES est basée sur des clés de 56 bits, soit 2 puissance 56 possibilités !

IDEA est un algorithme breveté par la société Suisse Mediacrypt et depuis tombé dans le domaine public (en 2011 en Europe) est dérivé de l’algorithme PES. Il até présenté la première fois en 1991. Il utilise des blocs de 64 bits avec une clé de 128 bits. Depuis la société, a présenté en 2005 son successeur FOX breveté sous le nom IDEA NXT (clé 128 bits/blocs 64 bits ou clé 256 bits/blocs 128 bits).

Publié en 1979, 3DES ou Triple DES a été développé par Walter Tuchman en enchainant 3 traitements successifs de l’algorithme DES. Il utilise 3 clés DES de 56 bits sur des blocs de 64 bits. Il est vulnérable aux attaques de type « rencontre au milieu ». De ce fait, il est admis qu’il fournit une sécurité effective de 112 bits seulement. 3DES est largement utilisé dans l’industrie électronique.

CAST5 ou CAST-128, a été conçu en 1996 utilise des clés allant de 40 à 128 bits pour des blocs de 64 bits. Il est notamment validé par le gouvernement canadien et est utilisé par défaut dans de nombreux produits.

Blowfish est aussi présent dans de nombreuses solutions (par défaut dans OpenVPN par exemple). Présenté en 1993, c’est un algorithme de référence avec AES. Un des gros points forts de Blowfish réside sans sa légèreté qui lui permet d’être utilisé dans le domaine de l’embarqué. A noter, que son créateur, Bruce Schneier, recommande d’utiliser son successeur Twofish.

AES est le standard issu du concours lancé en 1997 par le NIST (National Institute of Standards and Technology). C’est le standard par défaut du gouvernement US. Comme Blowfish, il n’y a pas d’attaque connue contre cet algorithme (hormis par brute force, mais difficilement réalisable en l’état actuel de la technologie).
	IDEA	3DES	CAST-5	BLOWFISH	AES (128-192-256)
Date de publication	1992	1979	1996	1993	1998
Dérivé de	PES	DES			SQUARE
Taille des clés (bits)	128	56, 112 ou 168	de 40 à 128, multiple de 8 bits. Par défaut 128 bits.	de 32 à 448, multiple de 8 bits. Par défaut 128 bits.	128-192-256
Taille de bloc (bits)	64	64	64	64	64-128-128
Structure	Add-Rotate-Xor 8,5 tours	Schéma de Feistel	Schéma de Feistel – 12 ou 16 tours	Schéma de Feistel – 16 tours	Substitution, permutation – 10, 12 ou 14 tours selon la taille de la clé.
Variante	FOX (breveté)		CAST-256	TWOFISH	
Commentaires sur la sécurité	Attaque par collisions possibles	Selon la taille de la clé, des exploits existent.	Aucune attaque réalisable connue	Aucune attaque réalisable connue	Aucune attaque réalisable connue
Sécurité (/5)	4	4	5	5	5
Performance (/5)	2	1	4	5	4
Commentaires	IDEA était soumis au brevet jusqu’en 2011 en Europe.	La taille de la clé dépend de l’option choisie : 1, 2 ou 3	Aussi appelé CAST-128	Empreinte mémoire très faible et très performant.	Certifié par la NSA.

Il existe plusieurs versions AES128, AES192 et AES256. le chiffre définissant la longueur de la clé.

En conclusion, les 3 algorithmes les plus sécurisés sont CAST-5, AES et Blowfish dont à ce jour, aucune attaque réalisable n’est connue. J’ai une petite préférence pour Blowfish de par sa performance.
