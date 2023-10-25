
## Temps réel : 

* Application temps-réel : 
    * composé d'au moins 1 tâche (processus) temps réel
    * si elle exécute ses tâches et actions dans un délai borné
    * définie entre autre par des contraintes temporelles
    * une contrainte tempo limite la validité d'un action ou d'une information dans le temps 

* Système temps réel : 
    * Un système est dit temps réel lorsque l'information après acquisition et traitement reste encore pertinente





* Rôle d'un algo d'ordonnancement :
    * Décider de l'allocation de la ressource aux **entités** qui l'attendent, de sorte à atteindre certains objectifs 

* entités :
    * Un processus
    * Un fil d'exécution à l'intérieur d'un processus (thread)

* Ex : Le CPU 
    * Objectif : Aboutir à un partage **efficace** du temps d'utilisation du processeur

* Critères d'efficacités :
    * Respect de la priorité (priorités différentes, statique ou dynamique)
    * Respect de l'équité (2 processus de mm priorité doivent pouvoir utiliser le CPU de la mm manière )


* Ordonnancement **préemptif** si il peut interrompre une tâche au profit d'une autre plus prioritaire (laisse exec un processu pdt un delai determiné)
* **Non-préamptif** laisse exec un processus jusqu'a ce q'uil bloque ou libère volontairement le processeur 

* Ordonnanceur **non oisif** s'il fonctionne sans intersion de tps creux (non-idling). Si il y a au - 1 tâche prête à etre ex, alors il en choisi forcément une. **Oisif** si il ex aucune tâche pdt un certain temps, alors qu'il y en a au - 1 prête a être ex 

* Ordo **off-line** s'il est pré-calculé avant ex puis ex avec ou sans préemption. **on-line** s'il décide dynamiquement avec ou sans préemption de l'ex des tâches 

* **tâche indépendantes** ne partagent qu'1 ressource : le processeur 
* **tâche dépendantes** partagent d'autres ressouces ou sont reliées par des contraintes de précédences.
* **précédences** : certaines tâches peuvent s'ex que si d'autres se sont ex avant 


* Ordo à **priorité fixe** : chaque tâche possède une priorité qu'elle conservera tt sa durée de vie 
* Ordo a **priorité dynamique** : priorité d'un tâche peut changeer lors de son éxe 


* Ordo a priorités fixe : 
    * Priorités determinées selon :
        * D : l'échéance relative
        * T : La période 
        * P : L'importance de la tâche
    * **Rate monotonic** (RM) : La tâche ayant la + petite période est la + prioritaire 
    * **Deadline Monotonic** (DM) : La tâche ayant la + petite échéance relative est la + prioritaire 
    * **Heighest Priority First** (HPF) : Priorités en fonction de leurs importances

* Ordo a priorités dynamiques : 
    * 1 tâche peut changer de priorité à chaques activations selon :
        * D : l'échéance absolue
        * T : La période (instant d'activation)
        * C : Le temps d'exec restant 
    * **Earliest Deadline First** (EDF) : La tâche la + proche de son échéance absolue aura la priorité la plus élevée
    * **Least Laxity First** (LLF) : la tâche la plus prio est celle de moindre laxité (diff entre l'échéance absolue et l'instant de terminaison de la tâche si on l'exec totalement)


* Faisabilité : 

    * Charge U = Somme Ci/Ti 
    * RM : 
        * Urm = n(2^(1/n)-1)
        * U > 1 : système non faisable 
        * U <= Urm : sys faisable 
        * sinon : on ne peut pas décider au regard de la condiion de charge 
        * Si 1>U>Urm --> verifier si tt les tâches sont exec avant leur echeance 
    * EDF : 
        * ppqc des périodes = durée d'etude 
        * ou 
        * trouver une durée + courte ou scenario au pire cas = **busy period**
        * **point d’inactivité (idle point)** : L’instant dans le quel le processeur est oisif (exec aucune tâche).
        * calcul busy period : 
            * W(t)=Somme(t/Ti)Ci (on veux t=W(t), init t=1) 

* Optimalité : 
(préemptif : peut interrompre une tache pour en exec une autre)
* RM : préemptive / Di = Ti.
* DM : préemptive / Di <=Ti.
* LLF : préemptive.
* EDF : toujours


* **Inversion de priorité** :Une tâche de haute priorité peut se bloquer sur une SC par une tâche moins prioritaire, laissant le temps à une tâche moins prioritaire qu’elle de la dépasser en exécution

* **Interblocage** : quand deux tâches ont besoin d’accéder simultanément à deux ressources partagées.

faire edf p130
faire Calcul du temps de réponse d’une tâche 121


* **PIP (Priority Inheritance Procotol - Protocole d'héritage de priorité)** :
    * Tâche peut etre bloqué autant de fois que le nbr de section critique qu'elle utilise 
    * Blocage direct ou héritage de priorité 
    * + mauvais cas de blocage : B(direct) + B(heritage)
    * Tps de blocage borné 
    * Pas besoin de connaître les ressources utilisées par les tâches 
    * MAIS 
    * Ne permet pas d'éviter l'inter blocage
    * chaîne de blocage ? 

* **PCP (Priority Ceiling Protocol - Protocol de priorité plafond)** : 
    * Une tâche ne sera bloqué que par une seule section critique 
    * Blocage Direct, priorité plafond, heritage de priorité 
    * chaque ressource possède une priorité plafond 
    * chaque tâche possède une priorité statique 
    * chaque tâche possède une priorité dynamique (max entre plafond et statique )





## Cours systèmes

* **Système d'exploitation** 
    * Ensemble de programmes responsable de la liaison entre les ressource matérielles d'un ordinateur et les applications informatiques de l'utilisateur 
    * Fournit au programmes d'applications des points d'entrée génériques pour les périphériques
    * Gère les ressource comme le processeur, mémoire, timers...

* **processus** 
    * Programme en cours d'exec
    * Processus system (deamons) : assure les services généraux accesssible à tt les users, propriétaire root, pas sous controle de terminal
    * Processus utilisateur : dédié à l'exec d'une tâche particulière, propriétaire est l'user, ss control du temrinal ou il a ete lancé


* **Scheduling premier arrivé premier service FCFS (First come, first served)**
    * Géré avec une file d'attente FIFO


## DE 

* Notion tps réel : 

    * Un système est dit temps réel lorsque l'information après acquisition et traitement reste encore pertinente. Le système respecte des contraintes temporelles (tâches et actions dans un temps fini et borné). 

* SE vs RTSE

| OS      | RTOS |
| ----------- | ----------- |
| ordonnancement complexe      | ordonnancement temps réel        |
| priorités peu considérées   | gestion stricte des priorités         |
| limite de la gestion du temps | perspective du temps |
| incertitude des temps | primitives de synchonisation |
| noyau préemptif | noyau non preamptif | 
| gestion des E/S génère des tps morts/blocages | respecte la norme POSIX |


* Citer quatre paramètres d’une tâche temps réel pouvant être utilisés pour avoir une politique d’ordonnancement dynamique et donner le nom de l’ordonnanceur
    * priorité 
    * echeance absolue
    * période
    * cout 
    * EDF


* Pb inversion de priorité 

    * Une tâche de H priorité peut se bloquer sur une section critique par un tâche moins prioritaire, laissant le temps à une tâche moins prioritaire qu'elle la dépasser en execution 
    * --> utiliser PCP ou PIP 

* Avantages PCP : 
    * Une tâche ne sera bloqué que par une seule section critique 
    * Blocage Direct, priorité plafond, heritage de priorité 
    * chaque ressource possède une priorité plafond 
    * chaque tâche possède une priorité statique 
    * chaque tâche possède une priorité dynamique (max entre plafond et statique )



* Dans un système d’exploitation LINUX classique : 
    * Un processus a toujours une priorité même si nous ne la fixons pas par programme

* Quel(s) est(sont) les caractéristique(s) d'un tube(pipe) utilisé dans la communication inter-process? 
    * FIFO
    * L'information disparaît après lecture 

* Quelle(s) politique(s) d'ordonnancement est/sont dynamique(s) ? 
    * Earliest Deadline First (EDF)

* Parmi les exemples sur le problème de synchronisation entre processus, nous pouvons citer 
    * Producteurs/consommateurs 
    * Rédacteurs / lecteurs





* Avantages EDF :
    * EDF est un algorithme d'ordonnancement qui choisit toujours la tâche dont la date limite est la plus proche. 
    * Contrairement à RM et DM, EDF n'a pas de contraintes strictes sur les dates limites ou les périodes

