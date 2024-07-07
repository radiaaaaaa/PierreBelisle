# PierreBelisle


Travail pratique 1 : Viualiseur de tri graphique

Auteur : Pierre Bélisle
Version : Copyright E2024
Ce document a été rédigé avec l'assistance de ChatGPT, un modèle de langage développé par OpenAI. L'utilisation de cette intelligence artificielle a contribué à l'amélioration de la clarté et de la précision des instructions et des critères d'évaluation.

Table des matières
1)	Objectifs	2
2)	Description	2
3)	Exigences	3
3.1	Interface Graphique et contraintes	3
3.2	Algorithmes de Tri	3
3.3	Gestion des Threads :	3
4)	Exemples d'Utilisation	4
4.1	Sélection d'un algorithme et exécution du tri choisi :	4
5)	Instructions	5
5.1	Mise en place de l'interface graphique :	5
5.2	Implémentation des algorithmes de tri :	5
6)	Livrables	5
7)	Évaluation	5
8)	Contraintes de IA et aide	6
9)	Conclusion	6

 
1)	Objectifs
L'objectif de ce travail pratique est de créer une application Java avec une interface graphique en utilisant le paquetage (package) Swing de Java. Cette application permettra de visualiser différents algorithmes de tri. 
Vous devrez utiliser une hiérarchie de classes contenant plusieurs algorithmes de tri, utiliser des threads pour exécuter les tris sans bloquer l'interface utilisateur, et gérer l'interaction utilisateur via des composants Swing.

2)	Description
Vous devez concevoir une application Java qui permet de visualiser le fonctionnement de différents algorithmes de tri sur un tableau d'entiers. 
L'application inclura une interface graphique pour sélectionner un des tris, définir les indices de début et de fin pour le tri, d'exécuter le tri tout en visualisant le processus. Une fois le tri terminé, l'interface doit redevenir interactive puisqu’elle ne doit pas l’être durant le processus.
Vous devez donc permettre de trier une portion d’un tableau avec un algorithme et une autre portion avec un autre algorithme ou le même selon le choix de la personne.  

*** Une vidéo montrant le fonctionnement de ce qui est demandé est fournie avec cet énoncé (cela est rare en entreprise).

 
3)	Exigences

3.1	Interface Graphique et contraintes
•	Utilisez Swing pour créer l'interface graphique.

•	Créez des composants pour : 

o	Sélectionner l'algorithme de tri (par exemple, JComboBox).
o	Définir les indices de début et de fin (tout sauf JComboBox).
o	Lancer le tri (tout sauf JButton)
o	Réinitialiser le tableau (seul JButton est permis).

•	Un panneau affichera le tableau et les modifications pendant le tri, se mettre à jour visuellement les changements au fur et à mesure que le tri progresse.

3.2	Algorithmes de Tri  
Montrez seulement les algorithmes de tri suivants qui sont déjà implémentés :

•	Tri à bulles (Bubble Sort)
•	Tri par sélection (Selection Sort)
•	Tri par insertion (Insertion Sort)
•	Tri cocktail (Cocktail Shaker Sort)
•	Tri de Shell (Shell Sort)

3.3	Gestion des Threads :
•	Utilisez le modèle Observateur/Observable pour mettre à jour l'interface graphique au fur et à mesure que le tri progresse .  

•	Le tri doit être exécuté dans un thread séparé pour ne pas bloquer l'interface graphique.
•	À chaque permutation, chaque décalage et à la fin de chaque tri, il faudra aviser les observateurs du tableau.  

•	Les composants de l'interface graphique doivent être désactivés pendant le tri et réactivés une fois le tri terminé.  

•	Évidemment, les fonctions de rappel passées aux composants qui permettent de trier et de réinitialiser le tableau, fonctionnent dans le thread nommé EDT.

•	Gérez l'exécution des threads et la mise à jour de l'interface graphique.  L’application doit être démarré avec SwingUtilities.invokeLater.  

4)	Exemples d'Utilisation

4.1	Sélection d'un algorithme et exécution du tri choisi :
•	La personne sélectionne un algorithme de tri et les indices des valeurs à trier dans des composants de votre choix qui respectent les contraintes déjà énoncé.

•	Vous devez offrir la possibilité de ‘trier’ ou de ‘reinitialiser’ le tableau.  Le tri s’effectue sur un tableau initialisé au départ avec des valeurs de votre choix.  La réinitialisation met le tableau dans son état original sinon le tri s’effectue sur le dernier tableau montré.  Toujours en tenant compte des indices.

•	Notez que si le tri est demandé sur un tableau trié, il s’effectuera mais rien ne sera visible puisqu’aucun changement n’aura lieu dans le tableau.  Cela est dû au fait que les observateurs ne sont avisés que s’il y a permutation, décalage ou qu’un tri est terminé.

•	Pendant l'exécution du tri, les composants du panneau de contrôle sont désactivés et le panneau de visualisation affiche les changements en temps réel.


•	Une fois le tri terminé, les composants sont réactivés et le résultat final est affiché.

*** On vous demande au moins un tableau de 15 valeurs mais, pendant le développement utilisé moins de valeurs pour sauver du temps d’attente lors des tests.
5)	Instructions

5.1	Mise en place de l'interface graphique :

•	Créez une classe principale CadreTriGUI qui hérite de JFrame et implémente à la fois Runnable.  

•	Après son initialisation de base, créez un panneau de contrôle afin d’y ajouter des composants Swing pour sélectionner l'algorithme de tri et les indices de tri.  Ajoutez-le à un panneau principal dont la référence sera dans le JFrame (contentPane ou non).    Rendez le cadre visible.

Rappel : On n’ajoute pas directement dans un JFrame.

•	À chaque fois que l’action de trier est demandée par la personne utilisatrice, créez un panneau de tri qui montre les valeurs du tableau à trier et les modifications à chaque modification.  Ce panneau doit être ajouté avec le panneau de contrôle dans un panneau principal.  À l’exception la première fois, supprimez ce panneau avant de le recréer.

5.2	Implémentation des algorithmes de tri :
•	Utilisez votre hiérarchie de classes pour les algorithmes de tri, en modifiant le code pour rendre le tout observable et notifier les observateurs des changements.
6)	Livrables
•	Code source de l'application complet et de qualité, dans un fichier compressé de type .zip seulement.  

•	10% des points pour des fichiers remis qui ne vont pas avec le projet.
7)	Évaluation
•	Fonctionnalité et exactitude des algorithmes de tri (10%).

•	Utilisation correcte des threads pour maintenir la réactivité de l'interface (25%).

•	Qualité de l'interface graphique et de l'expérience de la personne utilisatrice (15%).

•	Clarté et qualité du code, y compris les commentaires (50%).

•	La qualité implique de programmer en ayant en tête la philosophie du programmeur qui évite la répétition de code inutile, les déclarations de variables et d’instructions inutiles.
8)	Contraintes de IA et aide
•	Il est interdit de consulter le code d'une autre équipe ou de partager son propre code avec une autre équipe.

•	Il est interdit de copier-coller du code provenant d'une intelligence artificielle. Vous devez taper le code vous-même et corriger les erreurs si nécessaire.  Cela inclut les commentaires et les bonnes pratiques.

•	Demandez de l'aide à vos partenaires, auxiliaires d'enseignement ou tuteurs de Nimbus sans les laisser taper du code à votre place.

•	Toute preuve de manquement à l’une de ces règles entraînera des sanctions disciplinaires, pouvant inclure le refus du travail d’équipe soumis et une dénonciation aux comités de discipline de l'établissement.

9)	Conclusion
Ce travail vous permettra si vous le désirez de mettre en pratique les concepts orientées-objet dans l’utilisation du paquetage swing.  Cela implique l’utilisation de composants autres que ceux de bases enseignées dans le cours.
De plus l’élève devra comprendre la notion de thread et de fonctions de rappel.
Enfin, cela permettra de concrétiser l’utilisation et l’organisation des classes décrivant les composants swing et les interfaces tels JFrame, JPanel, JButton, ActionListener, …

Finalement de pratiquer la programmation de manière autonome.
Bon travail !!!
















1.	Interface graphique avec Swing :
o	Utilisation de JComboBox pour sélectionner l'algorithme de tri.
o	Utilisation de JTextField pour définir les indices de début et de fin.
o	Utilisation de JButton pour lancer le tri et réinitialiser le tableau.
2.	Algorithmes de tri :
o	Implémentation des différents algorithmes de tri dans des classes qui héritent de Tri.
3.	Gestion des Threads :
o	Exécution des tris dans des threads séparés.
o	Utilisation de SwingUtilities.invokeLater pour mettre à jour l'interface graphique sans bloquer le thread principal.

JComboBox est un composant de l'interface graphique Swing en Java qui permet à l'utilisateur de choisir une option parmi une liste déroulante.
Caractéristiques; Affichage d'une liste d'options, Sélection unique, Entrée de texte par l’utilisateur par moment. 
JTextField
JButton 






