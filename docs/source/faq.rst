Questions Fréquemment Posées
====================================

	:ref:`Q01 Principe de fonctionnement de HPC <Q01>`
	
	:ref:`Q02 Que dois-je faire pour être autorisé à utiliser le cluster HPC-MARWAN? <Q02>`
	
	:ref:`Q03 Ai-je besoin d'un programme spécial pour accéder au cluster HPC? <Q03>`
	
	:ref:`Q04 Combien d'espace disque puis-je utiliser? <Q04>`
	
	:ref:`Q05 Demander de l'aide <Q05>`
	
	:ref:`Q06 Formulaire reçue incomplet <Q06>`
	
	:ref:`Q07 Problèmes d’accès à l’HPC <Q07>`
	
	:ref:`Q08 Probléme de lancement d'un calcul <Q08>`
	
	:ref:`Q09 Combien de calculs je peux lancer ? <Q09>`
	
	:ref:`Q10 Comment annuler un process lancé par erreur  sur la machine login? <Q10>`

	:ref:`Q11 Saisie de mot de passe ou de code de vérification sur le client SSH  <Q11>`


.. _Q01:
Q01 Principe de fonctionnement de HPC
------------------------------------------------


En principe, l’utilisation du cluster de calcul haute performance se fait en ``mode batch`` .Ce qui signifie que le chercheur prépare ses fichiers inputs au préalable et lance le calcul via une commande ``sbatch``.

- Le calcul atterrit par la suite dans une file d’attente contenant d’autres calculs appartenant aux autres utilisateurs du HPC ``squeue`` et le gestionnaire des calculs (SLURM pour notre cas) a pour rôle d’affecter une ressource libre au premier calcul de la file d’attente.
 
 * Le calcul est géré par SLURM et le chercheur peut fermer la session . Il peut consulter de temps en temps l’état de calcul avec le commande ``squeue`` pour voir si son calcul a été lancé.

 * Une fois le calcul lancé, le chercheur consulte le dossier d’exécution et suit l’avancement via les fichiers logs et outputs.

 * Quand le calcul se termine, il disparait de la file d’attente et le chercheur peut récupérer les résultats sur son laptop.

 * Les commandes utiles pour le mode batch sont décrite dans la deuxième partie du tutoriel : Gestion des calculs.

- Le mode interactif avec interface graphique est aussi possible, mais présente des limitations.  S’il n’y a pas de ressources libre, le chercheur doit attendre devant son pc jusqu’à que la ressource lui soit affectée . 
Une fois il a la main et fait les manipulations nécessaires, il ne doit pas quitter la session jusqu’à la fin de l’exécution. 
Aussi la réservation de la ressource ne peut généralement pas dépasser quelques heures si le programme ne se termine pas avant, il sera arrété.

.. Note::
     Nous conseillons au chercheur d’utiliser le ``mode batch`` pour la partie lourde du travail,programme qui a besoin d’un temps de calcul important , 
     et laisser le mode interactif pour le ``post-processing`` par exemple la visualisation d’un fichier output.

	
.. _Q02:	
Q02 Que dois-je faire pour être autorisé à utiliser le cluster HPC-MARWAN?
-----------------------------------------------------------------------------------


Afin d'accéder au Cluster HPC-MARWAN , il vous suffit de remplir ce formulaire , le signer et le retourner à l'équipe HPC-MARWAN par l'un des moyens suivants :
   
   • En vous rendant au CNRST , Angle Allal Al Fassi et Avenue des FAR, Hay Ryad, BP. 8027 10102 Rabat
   • Par Fax : (+212) 05 37.56.98.34
   • Par Mail :hpc@marwan.ma

Une fois la demande reçue ,l'équipe vous contactera dans les plus brefs délais pour la création du compte d'accès.


.. _Q03:
Q03 Ai-je besoin d'un programme spécial pour accéder au cluster HPC?
----------------------------------------------------------------------


Cela dépend du système d'exploitation que vous utilisez sur votre ordinateur privé et de la façon dont vous devez utiliser le système HPC. Vous avez besoin ``d'un client SSH`` pour pouvoir vous connecter au système.

Si vous souhaitez utiliser des programmes avec une interface utilisateur graphique, vous pouvez installer le logiciel ``Mobaxtream`` (disponible pour Windows). Les instructions sont disponibles sous le rubrique Guide utilisateur.


.. _Q04:
Q04 Combien d'espace disque puis-je utiliser? 
-----------------------------------------------------------------------

Chaque utilisateur de HPC-MARWAN dispose d'un répertoire personnel de ``100Go`` (/home/login). Vous pouvez déposer vos fichiers volumineux sur /data/login ou /scratch/users/login ,dont la limite est 500 Go chacun.


.. _Q05:
Q05 Demander de l'aide
---------------------------------------

Le modèle de soutien du service HPC-MARWAN fournit une assistance personnelle individualisée pour répondre aux besoins uniques et complexes de chaque chercheur.

Si vous avez des questions ou si vous avez besoin d'aide pour utiliser le cluster, envoyez un e-mail à hpc@marwan.ma.


.. _Q06:
Q06 Formulaire reçue incomplet
----------------------------------------

Au cas de réception du formulaire incomplet,nous demandons à l’utilisateur de nous ré-envoyez le formulaire rempli et signé.


.. _Q07:
Q07 Problèmes d’accès à l’HPC
--------------------------------------------

La majorité des problèmes d’accès à l’HPC-MARWAN, sont dus:

   * Plusieurs tentative de connexion erronées.

   * Mot de passe erronée (erreur de frape/ ajout d’espace …).

   * Adresse IP public bloquée.

Pour cela on demande aux utilisateurs de nous envoyer une capture d’écran du message d’erreur, et de nous envoyer leur adresse IP public https://www.whatismyip.com.



.. _Q08:
Q08 Probléme de lancement d'un calcul
------------------------------------------------

En cas d’utilisation d’un éditeur de fichier sous Windows pour écrire le script Slurm run.sl ; le lancement de ce dernier run.sl sous linux, vous donnera l’erreur suivante :

.. code-block:: bash

  $ sbatch run.sl

  sbatch: error: Batch script contains DOS line breaks (\r\n)

  sbatch: error: instead of expected UNIX line breaks (\n).


Afin de résoudre se problème, on vous propose d’utiliser un éditeur de fichier (Notepad++) qui permet de spécifier linux comme format.

.. image:: /source/figures/mobaxterm.png



.. _Q09:
Q09 Combien de calculs je peux lancer ?
------------------------------------------------------


Le nombre de calculs qui peuvent être exécutés ``Etat Running`` simultanément pour chaque utilisateur est de ``10`` calculs. 
Le nombre de calcul pouvant être placés dans la queue ``Etat Pending`` est limité à ``10`` calculs.
Le nombre de CPU pouvant être exploité par un utilisateur est limité à ``64`` CPU.

.. _Q10:
Q10 Comment annuler un process lancé par erreur  sur la machine login?
------------------------------------------------------
Afin de lister les process lancés par l'utilisateur , utiliser la commande suivante :
 

.. code-block:: bash

  ps -o uid_hack,pid,lastcpu,%cpu,cmd --headers -u username -L




Pour annuler un process : 
 

.. code-block:: bash

  kill -9 PID


(PID est l'identifiant du process affiché  via la commande précédente)

.. _Q11:
Q11 Saisie de mot de passe ou de code de vérification sur le client SSH 
------------------------------------------------------------------------

Lorsque vous vous connectez à Linux, vous devez saisir un mot de passe. Si vous entrez le mot de passe correctement, , vous devez simplement appuyer sur la touche "Entrée" après avoir saisi le mot de passe pour ouvrir une session.
Il est important de noter que Linux est différent des autres systèmes d'exploitation, comme Windows ou MacOS, car il ne montre pas les caractères de mot de passe que vous tapez à l'écran. Cela signifie que lorsque vous tapez votre mot de passe, il n'y aura pas d'étoiles  ou de points qui apparaissent à l'écran. C'est une mesure de sécurité pour empêcher les autres personnes de voir votre mot de passe si elles sont à proximité de vous. Donc, ne vous inquiétez pas si vous ne voyez pas les caractères que vous tapez, Linux est toujours en train de les enregistrer.

