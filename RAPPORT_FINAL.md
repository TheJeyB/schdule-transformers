# Rapport final - SchedulingTransformer

## 1. Introduction

Le present document constitue le rapport final du projet **SchedulingTransformer**. Son objectif n'est pas de reintroduire en detail le sujet, deja presente dans le cahier des charges et le rapport de conception, mais d'analyser l'ecart entre ce qui etait prevu et ce qui a ete effectivement realise dans le produit final observe au 29 mars 2026.

Le document est organise en quatre parties. La section 2 presente l'analyse des ecarts entre les objectifs initiaux et le resultat final, aussi bien sur le plan technique que sur le plan organisationnel. La section 3 propose un retour d'experience sur les acquis du projet. La section 4 conclut sur l'etat global du projet et sur ses suites possibles.

## 2. Analyse des ecarts

### 2.1 Objectifs techniques

#### 2.1.1 Objectifs atteints

Plusieurs objectifs techniques importants ont ete atteints.

D'abord, l'architecture generale prevue dans les livrables initiaux est effectivement retrouvee dans le produit final. Le systeme repose bien sur une architecture separee en trois parties:

- un frontend React pour l'interface utilisateur;
- un backend Spring Boot pour la logique metier, l'authentification et la persistance;
- un service IA Python/FastAPI pour la negociation basee sur un modele Transformer.

Ensuite, le coeur pedagogique du projet a bien ete concretise. Le module Python implemente un mecanisme de negociation multi-agents inspire du fonctionnement d'un Transformer. Les trois parties prenantes virtuelles du sujet sont representees:

- gestionnaire de salles;
- enseignant;
- etudiants.

Le moteur de negociation effectue plusieurs tours, utilise l'attention multi-tetes, produit des propositions de creneaux, evalue la satisfaction des acteurs et retourne une decision finale assortie d'explications. Sur ce point, l'objectif de comprendre et de mettre en scene le mecanisme d'attention comme une forme de "negociation" est atteint de maniere convaincante.

Par ailleurs, des fonctionnalites applicatives concretes ont ete livrees dans le produit final:

- creation de compte;
- authentification;
- edition du profil utilisateur;
- changement de mot de passe;
- creation d'une negociation;
- sauvegarde de la negociation en base;
- consultation de l'historique des negociations;
- consultation du detail d'une negociation;
- synchronisation d'une negociation avec la section "Mes emplois du temps";
- suppression d'une negociation avec suppression de l'entree synchronisee.

Le choix de persister les negociations et de les lier a l'utilisateur connecte constitue une amelioration importante par rapport a une simple demonstration locale du modele IA. Le produit final n'est donc pas seulement une maquette theorique: il s'agit d'une application web fonctionnelle, avec un cycle complet de creation, consultation et conservation des negociations.

#### 2.1.2 Objectifs partiellement atteints

Certains objectifs sont atteints seulement de facon partielle.

Le premier ecart concerne la notion d'"emploi du temps". Dans les documents initiaux, le projet visait la generation d'emplois du temps universitaires acceptables par les parties prenantes. Dans le produit final, la logique est davantage centree sur la **negociation d'un creneau** que sur la construction d'un emploi du temps complet au sens institutionnel du terme. Autrement dit, l'application gere bien une negotiation sur un slot final, mais elle ne produit pas encore une grille hebdomadaire complete pour plusieurs cours, groupes, enseignants et salles.

Le deuxieme ecart concerne la richesse du modele de contraintes. Les contraintes principales sont presentes:

- disponibilites des salles;
- preferences et indisponibilites des enseignants;
- preferences et contraintes horaires des etudiants.

En revanche, certaines dimensions annoncees ou attendues restent simplifiees. La capacite des salles est stockee mais n'influence pas encore fortement la decision finale. Les contraintes sont en partie evaluees comme preferences souples plutot que comme veritables contraintes metier complexes. Le systeme fonctionne donc comme un negociateur hybride coherent, mais pas encore comme un planificateur universitaire complet.



Enfin, plusieurs choix techniques annonces dans les documents ont ete adaptes en cours de projet.

Ces ecarts ne remettent pas en cause la coherence du projet, mais ils montrent un recentrage progressif sur le noyau utile: la negociation, la persistance et l'integration web.

#### 2.1.3 Objectifs non atteints ou depasses

Plusieurs objectifs annonces dans le cahier des charges ne sont pas atteints dans le produit final:

- generation d'emplois du temps complets a grande echelle;
- edition manuelle avancee avec verification temps reel;
- exports documentaires;
- visualisations poussee du processus d'attention;
- outillage Docker/CI-CD visible dans le depot;
- batterie de tests automatisee complete.

En revanche, certains aspects sont depasses par rapport a une simple interpretation pedagogique minimale:

- persistance en base des negociations et de leur historique;
- gestion utilisateur plus complete que le strict minimum initial;
- synchronisation entre negociations et section "Mes emplois du temps";
- enrichissement du moteur de negociation avec propositions d'agents, concessions et contre-propositions;
- construction d'un petit pipeline de generation de donnees et d'entrainement utile pour faire evoluer le modele.

En ce sens, le projet final est plus avance qu'une simple preuve de concept academique, mais moins large qu'une plateforme complete de gestion d'emplois du temps universitaires.

### 2.2 Objectifs organisationnels

Du point de vue organisationnel, les livrables documentaires principaux semblent avoir ete produits dans les temps prevus:

- cahier des charges date du 27 janvier 2026;
- rapport de conception date du 3 fevrier 2026;
- le depot contient bien un produit final operationnel a la fin du mois de mars 2026.

Cela suggere que la progression globale du projet a ete maintenue, au moins sur les grandes etapes. En revanche, l'analyse du depot montre aussi une realite classique des projets de developpement: la priorisation s'est deplacee vers les fonctionnalites les plus critiques.

Le produit final privilegie:

- la mise en place d'un parcours utilisateur complet;
- la stabilisation backend/frontend;
- la persistance des donnees;
- et la credibilite du moteur de negociation.

En consequence, des aspects prevus mais plus couteux en temps, comme les exports, les visualisations d'attention ou l'edition manuelle avancee, ont ete reportes ou abandonnes.

Sur le plan des contraintes, plusieurs choix restent conformes a l'esprit initial:

- architecture hybride respectee;
- utilisation de PostgreSQL;
- separation claire entre logique metier et moteur IA;
- gestion de donnees utilisateur reelles en base.

En revanche, certaines contraintes organisationnelles ou de qualite n'ont ete couvertes que partiellement:

- peu de tests automatises sont presents dans le depot;
- aucune chaine de deploiement ou conteneurisation n'est visible;
- la securisation reste simple pour un prototype applicatif.

Ainsi, les objectifs organisationnels apparaissent **globalement tenus sur le plan du livrable fonctionnel**, mais **partiellement tenus sur le plan de l'industrialisation et de la finition**.

### 2.3 Analyse

Les reussites du projet s'expliquent d'abord par un bon recentrage du perimetre. Le sujet initial etait ambitieux: il melangeait apprentissage des Transformers, negotiation multi-agents, application web complete et problematique des emplois du temps universitaires. Face a cette ampleur, le projet a evolue vers un noyau plus realiste:

- une application web simple mais exploitable;
- un moteur de negociation interpretable;
- un stockage persistant des interactions;
- une integration bout en bout entre frontend, backend et IA.

Cette decision a ete pertinente. Elle a permis d'aboutir a un produit demonstrable et coherent, plutot qu'a une architecture tres large mais inachevee.

Les ecarts observes s'expliquent principalement par trois facteurs.

Le premier facteur est la complexite intrinseque du domaine. Generer un vrai emploi du temps universitaire est un probleme beaucoup plus vaste qu'une simple selection de creneau. Il faudrait gerer simultanement:

- plusieurs cours;
- plusieurs promotions;
- plusieurs enseignants;
- plusieurs salles;
- des contraintes institutionnelles fortes;
- et des dependances temporelles nombreuses.

Le deuxieme facteur est la complexite technique de l'integration. Le projet combine:

- Java/Spring Boot;
- React;
- Python/FastAPI;
- apprentissage automatique;
- persistance en base de donnees.

Cette heterogeneite est interessante pedagogiquement, mais elle augmente la charge de synchronisation, de debogage et de validation.

Le troisieme facteur est la difference entre objectif pedagogique et objectif produit. Le sujet insistait sur la comprehension du Transformer plutot que sur la construction d'un optimiseurl de planning parfait. Le produit final reste donc logiquement plus fort sur la dimension explicative et experimentale que sur la couverture totale d'un besoin metier reel.

Concernant l'anticipation des risques, certains risques semblent avoir ete correctement identifies:

- complexite du modele IA;
- difficulte de l'integration inter-services;
- ampleur fonctionnelle du sujet.

En revanche, l'ecart entre "negociation d'un creneau" et "generation d'un emploi du temps complet" aurait probablement merite d'etre formalise plus tot comme une reduction officielle de perimetre.

Les outils et methodes choisis etaient globalement adaptes pour un projet universitaire:

- React pour une interface moderne;
- Spring Boot pour la logique metier;
- FastAPI et PyTorch pour l'IA;
- PostgreSQL pour la persistance.

Leur principal inconvenient a ete la dispersion de l'effort entre plusieurs piles techniques, ce qui a probablement reduit le temps disponible pour les fonctionnalites secondaires et pour les tests.

## 3. Retour d'experience

Ce projet a apporte plusieurs enseignements importants.

Le premier apprentissage concerne le mecanisme d'attention. Le projet a permis de passer d'une comprehension theorique du Transformer a une comprehension beaucoup plus concrete. En representant l'attention comme une forme de discussion entre parties prenantes, il devient plus facile d'expliquer comment des representations se modifient progressivement au fil des couches.

Le deuxieme enseignement concerne la valeur d'une architecture hybride. Le projet montre bien qu'il est possible de combiner plusieurs technologies specialisees dans un meme systeme:

- React pour l'experience utilisateur;
- Spring Boot pour la robustesse metier;
- Python pour l'experimentation IA.

Le troisieme enseignement concerne la gestion du perimetre. Un sujet ambitieux doit etre transforme en increments successifs. Dans ce projet, le recentrage sur les negociations persistantes et sur un moteur interpretable a permis de garder une direction claire, alors qu'une tentative de couvrir immediatement tout le domaine de l'emploi du temps aurait probablement abouti a un resultat plus fragile.

Le quatrieme enseignement concerne la difference entre prototype intelligent et produit complet. Un systeme peut etre convaincant sur le plan conceptuel, tout en restant limite sur le plan industriel. Cette distinction est importante pour juger correctement le resultat final: le projet reussit bien comme application pedagogique avancee et comme prototype web fonctionnel, mais il ne pretend pas encore remplacer un veritable logiciel institutionnel d'emplois du temps.

Enfin, le projet a aussi mis en evidence l'importance des tests et de la stabilisation. Une grande partie du travail final ne consiste pas a "ajouter des fonctionnalites", mais a fiabiliser les parcours existants, corriger les synchronisations entre modules, et simplifier les flux de donnees entre frontend, backend et moteur IA.

## 4. Conclusion

Le projet SchedulingTransformer aboutit a un resultat globalement positif. Le produit final est coherent avec le coeur pedagogique du sujet: il met en oeuvre un systeme de negociation multi-agents inspire du mecanisme d'attention des Transformers, integre dans une application web avec persistance des donnees.

L'objectif principal de comprehension et de mise en pratique du paradigme Transformer est donc atteint. L'application permet de creer des comptes, lancer des negociations, consulter leur historique, visualiser leur detail et les synchroniser avec une section d'emplois du temps. Le systeme forme un ensemble demonstrable et techniquement credible.

L'ecart principal avec les ambitions initiales concerne l'ampleur metier du produit. Le resultat final ne constitue pas encore une plateforme complete de generation et d'edition d'emplois du temps universitaires. Il s'agit plutot d'un **prototype fonctionnel centre sur la negociation de creneaux**, avec une base technique solide pour aller plus loin.

Les suites les plus pertinentes pour le projet seraient:

- renforcer la prise en compte des contraintes fortes, notamment la capacite des salles et les conflits multi-cours;
- passer d'une negociation de creneau a une generation de planning multi-seances;
- ajouter des visualisations du processus d'attention et de la negociation;
- developper les exports attendus;
- renforcer la securite et les tests;
- eventuellement conteneuriser et industrialiser le deploiement.

En conclusion, le projet est reussi en tant que livrable universitaire et base d'experimentation serieuse. Il ne realise pas toute l'ambition fonctionnelle formulee au depart, mais il livre un noyau pertinent, pedagogiquement riche et techniquement exploitable.

## Références

1. HADJADJ Mohammed, ROMDHANE Iskander, *Cahier des Charges - Scheduling Transformer*, 27 janvier 2026.
2. HADJADJ Mohammed, ROMDHANE Iskander, *Rapport de Conception - SchedulingTransformer*, 3 fevrier 2026.
3. Depot source du projet SchedulingTransformer, etat observe le 29 mars 2026:
   - frontend React/Vite;
   - backend Spring Boot/PostgreSQL;
   - service IA Python/FastAPI/PyTorch.

## Annexes

### Annexe A - Principaux elements effectivement presents dans le produit final

- Authentification par inscription et connexion.
- Gestion du profil et changement de mot de passe.
- Creation de negociations avec informations de contexte (nom, niveau, filiere).
- Sauvegarde en base de donnees des requetes et reponses de negociation.
- Historique et detail des negociations par utilisateur.
- Synchronisation des negociations sauvegardees avec "Mes emplois du temps".
- Moteur de negociation Transformer avec tours, propositions d'agents et scores de satisfaction.
- Jeu de donnees synthetique compact et script d'entrainement.

### Annexe B - Principaux elements annonces mais non visibles ou non finalises

- Generation d'un emploi du temps complet multi-cours.
- Grille hebdomadaire complete de consultation.
- Edition manuelle par glisser-deposer.
- Exports PDF, CSV et iCalendar.
- Heatmaps d'attention et visualisations avancees.
- Docker Compose et pipeline CI/CD.
- Jeu de tests automatise etendu.
