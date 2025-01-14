# Présentation du logiciel John The Ripper

Vous êtes en possession d'un dossier crypté dont vous avez oublié le mot de passe ou vous êtes en entreprise et devez tester la force des mots de passe de votre service ?
Le logiciel John The Ripper est un logiciel open source qui vous permettra de réaliser vos tests de façon rapide et simple afin d'assurer votre sécurité et celle de vos collaborateurs. 

## Comment fonctionne John The Ripper ?

John réussit à trouver les mots de passe en comparant leur hash avec les hashs des mots de passe qu'il essaye afin de trouver une correspondance.
Le hachage de mot de passe est une pratique de sécurité des plus basiques qui consiste à brouiller les données en changer ce mot de passe en une série de caractères unique : le hash. Ce hash peut être créé par différents algorithmes (comme MD5, SHA1, SHA56...). Heureusement, John The Ripper est capable de décrypter les hashs de nombreux algorithmes de hashage. Il est même possible de télécharger des extensions si un algorithme n'est pas reconnu.

## Choix techniques : 

Ce logiciel fonctionnant de façon similaire sur une multitude d'OS, dans ce guide, nous verrons les étapes d'installation du logiciel sur un système Ubuntu. Ubuntu est un OS libre d'accès et simple à utiliser, nous le recommandons pour une première prise en main. Il faudra l'adapter à vos besoins si vous décidez de changer d'OS par la suite.
Pour l'installation de ce logiciel, il est nécessaire de connaître le système Ubuntu ainsi que son terminal.
Ce guide d'installation est créé à des fins éducatives et s'applique ici uniquement à un système Ubuntu. Vous pouvez visiter le [site officiel](https://www.openwall.com/john/) pour plus de renseignements ou pour l'installation sur d'autres OS. 


## Étapes d'installation et de configuration : instruction étape par étape  

Ce logiciel peut être installé sur Ubuntu dans votre terminal en utilisant apt-get ou snap. Cependant, vous pouvez rencontrer des dysfonctionnements en l'installant avec la commande suivante : _sudo apt-get install john -y_. Nous recommandons donc de procéder avec l'installation snap. Le format snap permet l'installation de logiciels séparés du reste du système d'exploitation grâce à des mécanismes de sécurité. Il peut toutefois échanger du contenu en suivant certaines règles précises instaurées par l'administrateur.
Snap est normalement nativement installé sur votre Ubuntu. Si toutefois ce n'était pas le cas, vous pouvez l'installer avec la commande suivante : 
```Bash
sudo apt update
sudo apt install snapd
```

Votre terminal vous affichera le message suivant validant la bonne installation du programme.

![Image 2 ](https://github.com/ThomasDominici/Projet-BVT-1/blob/main/Ressources/Screenshots%20installation/1.5.JPG)

Vous pouvez maintenant lancer l'installation de John The Ripper par snap grâce à la commande suivante : 
```Bash
sudo snap install john-the-ripper
```

Un fois l'installation terminée, votre terminal affichera le message dans la photo suivante : 

![Image 4](https://github.com/ThomasDominici/Projet-BVT-1/blob/main/Ressources/Screenshots%20installation/3.JPG)

Tapre maintenant _john_ dans votre terminal, il affiche le message suivant :

```Bash
john
```

![Image 5](https://github.com/ThomasDominici/Projet-BVT-1/blob/main/Ressources/Screenshots%20installation/4.JPG)

Nous pouvons voir la version du logiciel (ici 1.9.0).
La ligne **usage** montre que nous pouvons fournir à John un fichier contenant une liste de mots de passe ainsi que choisir l'option avec laquelle il va tenter de déchiffrer les fichiers que nous lui indiquerons.

Voici quelques exemples d'options envisageables pour John : 

1. **--single** : mode par défaut, John tente des combinaisons variables en fonction du nom de l'utilisateur.
2. **--wordlist** : l'attaque par dictionnaire. John utilise une liste de mots de passe fournis afin de craquer le mot de passe du fichier désigné.
3. **--incremental** : brut force, john teste toutes les combinaisons de caractères jsuqu'à trouver le mot de passe. Infaillible en théorie mais peut prendre du temps en fonction de la force du mot de passe du fichier sélectionné.

Nous allons maintenant créer des alias afin de pouvoir effectuer nos commandes plus rapidement : 
```Bash
sudo snap alias john-the-ripper.zip2john zip2john 
sudo snap alias john-the-ripper.keepass2john keepass2john 
```

## Difficultés rencontrées et solutions : 

### Difficultées et solutions rencontrées:  

| **Difficultées**   |     **Solutions**   |
|:-------------------|--------------------:|
| Logiciel peu efficace avec le paquet apt|  Installation du paquet avec snap|
| Capacité  de base limitée en liste de mots | Installation d'un paquet de liste supplémentaire openssl|
| Commandes peu intuitives |  Création d'alias pour les outils (zip2john et keypass2john).|
| Accéder aux dossier du serveur par la machine client|        
____

## Tests réalisés :

- Utilisation de John the ripper sur un dossier zip en mode simple sur une machine Ubuntu.
- Utilisation de John the ripper avec l'outil zip2john sur un dossier zip en mode dictionnaire sur une machine Ubuntu.
- Création d'un dossier partagé entre les deux machines virtuelles Windows Server 2022 (serveur) et Ubuntu (client).

  
# Résultats obtenus : ce qui a fonctionné  
# Améliorations possibles : suggestions d’améliorations futures  

**Pour désinstaller : sudo snap remove john-the-ripper**


