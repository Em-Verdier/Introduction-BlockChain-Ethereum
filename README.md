# Introduction-BlockChain-Ethereum

__DLT: Distributed Ledger Techonlogy ou technologie de registres distribués alias Chaîne de blocs (BlockChain)__

La Blockchain résoud deux types de problèmes : 

1.l'immutabilité : les données ne peuvent être modifiées.
2.le processus de distribution : désormais il n'y à pas un seul point de gouvernance ou/et possiblement un seul point de faille (cible unique et trop visible pour l'attaquant appelée `SPOF`), chaque noeud travaille ensemble basée sur un mécanisme de consensus qui protège d'agents malicieux.

__Immutabilité (Immutability)__

Dans une chaîne de blocs toutes les transactions sont stockées dans un block. Chaque bloc contient un `hash de chiffrement`__(cryprtographic hash)__ du block précédent dans la chaîne, liant les deux blocks, ainsi qu'un `hash de chiffrement` de toutes les transactions qu'il stocke.
Le `hash de chiffrement` est un hash produit par une `fonction de hash de chiffrement`.
La `fonction de hash de chiffrement` est une fonction à sens unique(fonction irréversible)qui va remplacer le contenu d'un block par un nombre.
Ces deux nombres, le hash de chiffrement du bloc précédent ainsi que le hash de chiffrement de toutes les transactions confirmées sont enregistrés dans l'`entête` du  nouveau bloc__(block header)__ en cours.
