:shipit: # Introduction-BlockChain-Ethereum  :chains:

### __DLT: Distributed Ledger Techonlogy ou technologie de registres distribués alias Chaîne de blocs (*BlockChain*)__

La Blockchain résoud deux types de problèmes : 

1. L'immutabilité : les données ne peuvent être modifiées
2. Le processus de distribution : désormais il n'y à pas un seul point de gouvernance ou/et possiblement un seul point de faille (cible unique et trop visible pour l'attaquant appelée *`SPOF`*), chaque noeud travaille ensemble basée sur un mécanisme de consensus qui protège d'agents malicieux.

### __Immutabilité (*Immutability*)__

Dans une chaîne de blocs toutes les transactions sont stockées dans un block. Chaque bloc contient un `hash de chiffrement`__(*cryptographic hash*)__ du block précédent dans la chaîne, liant les deux blocks, ainsi qu'un `hash de chiffrement` de toutes les transactions qu'il stocke.
Le `hash de chiffrement` est un hash produit par une `fonction de hash de chiffrement`.
La `fonction de hash de chiffrement` est une fonction à sens unique(fonction irréversible)qui va remplacer le contenu d'un block par un nombre.
Ces deux nombres, le hash de chiffrement du bloc précédent ainsi que le hash de chiffrement de toutes les transactions confirmées sont enregistrés dans l'`entête` du  nouveau bloc __(*block header*)__ en cours.


 ![Exemple](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/blockchain.jpeg)
 
 __Dessous regardons comment ce processus est implémenté dans par le code:__
 
 ![Exemple](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/codeview.jpg)
 
 __Ici une vue d'ensemble d'entêtes de blocs:__
 
 ![Exemple](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/blockheader.png)
 
 Ce processus confirme l'intégrité d'un bloc, en partant celui-ci, en passant par tous les précédents jusqu'au tout premier bloc de la chaîne `*genesis block*`.
 
 Si un agent malicieux veut modifier un bloc, par exemple en chageant un montant de transaction, il va altérer le hash de toutes les transactions dans le bloc. Donc il devra à nouveau miner ce bloc. Cette opération va changer la totalité des hash du bloc reforgé, et à parti de lui et tous les blocs suivants auront un hash différent du bloc qui les précède, stocké dans leur entête. Par conséquent l'acteur malveillant devra aussi reminer tous les blocs suivants celui qu'il a modifié afin qu'ils soient basés sur le hash du bloc fabriqué par l'attaquant.
 Une autre solution de protection tendant à prévenir ce genre de modifications est le mécanisme de consensus. Les attaquants on besoin de contrôler 51% de la puissance de calcul du réseau pour modifier à leur avantage ou inverser les transactions déjà effectuées dans la chaîne de blocs. Ce phénomène est appelé `Attaque des 51%` __51% Attack__. Inutile de dire que c'est actuellement impossible, car les attaquants aurait besoin de beaucoup trop de puissance de calcul et quand bien même ils réussiraient, celà annihilerait la confiance placée dans cette blockchain par les acteurs et ces derniers partiraient.
 

### __Centralisé contre Décentralisé contre Distribué__

![Exemple](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/CDD.png)

 Dans une réseau distribué __*Distributed network*__ il n'y à pas d'unique ou même plusieurs points de gouvernance faisant autorité. L'objectif étant de d'éviter la centralisation d'une attaque et donc un seul point de faille __(*SPOF*)__ C'est pourquoi les mécaniques de consensus sont utilisées pour être certain que chaques noeuds, dans un réseau distribué, fonctionnent ensemble et jamais de manière malveillante.
 Dans le cas d'un réseau de chaîne de blocs, les mécanismes de consensus sont utilisés afin de contrôler comment une transaction de chaînes de blocs peut être confirmée écrite et executée.
 
 
 
 
