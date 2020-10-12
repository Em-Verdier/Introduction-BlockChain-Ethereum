# Introduction-BlockChain-Ethereum  :chains: :shipit: :chains:

###  __DLT: Distributed Ledger Techonlogy ou technologie de registres distribués alias Chaîne de blocs (*BlockChain*)__

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


### __Les mécanismes de consensus__ (non exhaustif)
 
#### 1. Le problème des généraux byzantins (*BFT :  Byzantine Fault Tolerance*)

https://fr.wikipedia.org/wiki/Probl%C3%A8me_des_g%C3%A9n%C3%A9raux_byzantins


#### 2. La preuve de travail __(*PoW: Proof of Work*)__

C'est un algoritme de consensus original. Avec la *`preuve de travail`*, les mineurs sont en compétition les uns avec les autres afin de terminer des transactions et d'ajouter les nouveaux blocs à la BlockChain.
Les mineurs doivent résoudre un puzzle complexe en utilisant la puissance de processeur de leur(s) machine(s).
Le puzzle mathématique à résoudre consiste à trouver le nombre du hash de l'entête du bloc courant en manipulant le champs du *`nonce`* de ce bloc.
Le `nombre du hash` à trouver doit être inférieur au `hash cible`. `Le hash cible` est défini par la `difficulté`.

![Exemple](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/bitcoin_block_hashing.jpg)

Le premier mineur qui résoud le puzzle est récompensé pour son travail.
Une preuve de travail est un bout de données qui est difficile à produire(coûteux, chronophage), mais facile à vérifier par les autres et qui répond à certaines exigences.

#### 3. La preuve d'enjeu ou preuve de participation __(*PoS: Proof of Stake*)__

La `preuve de travail` ou `preuve de participation` est un type d'algoritme de consensus grâce auquel un réseau BlockChain de crypto-monnaie a pour objectif de réaliser un consensus distribué. Dans les BlockChains basées sur la preuve d'enjeu, le créateur du prochain bloc est choisi par de nombreuses combinaisons de sélections aléatoires, et sa fortune(en crypto-monnaie) et son âge. Dans le cas de la BlockChain Ethereum, il y à un minimum de 32 ETH requis pour participer à l'enjeu, et les validateurs doivent lancer un noeud de validation. Ca ne necessite pas d'être un spécialiste hardware, celà peut être réaliser sur un ordinateur ayant un grade de simple client ou un pc portable. Toutefois, les validateurs sont attendus comme suffisamment connectés sous peine de pénalités mineures.
Dans le cas où la chaîne de blocs applique un consensus de `preuve de travail` __(*PoS*)__, mineurs, validateurs, stackers(accumulateurs) peuvent miner ou valider des blocs de transactions en fonction du montant de crypto-monnaie qu'ils possèdent.
Dans l'objectif d'ajouter un bloc malveillant, il faudrait que l'attaquant possède 51% du total de la crypto-monnaie du réseau.

Historiquement, Ethereum a appliqué par le passé un consensus de preuve de travail. Cependant une des raisons pour lesquelles elle a migré vers la preuve d'enjeu est, que celle-ci est bien plus efficace énergétiquement que la preuve de travail.


### __Minage__









 
 
 
 
