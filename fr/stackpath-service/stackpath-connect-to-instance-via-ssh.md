---
title: "Service de StackPath : Se connecter aux VM et aux conteneurs"
slug: stackpath-se-connecter-aux-vm-et-conteneurs
---

## Se connecter à une VM

Une machine virtuelle d'une charge de travail StackPath peut être atteinte en utilisant un client SSH standard.

### Conditions préalables

1. Vous devez avoir la contrepartie de la clé privée de la clé publique qui a été utilisée lors de la création de la machine virtuelle. La clé privée a été générée avec la clé publique et est généralement un fichier qui commence par la chaîne `----- BEGIN RSA PRIVATE KEY -----`.
1. Il doit y avoir une règle de réseau entrant dans *Politiques de réseau* pour cette charge de travail, autorisant le trafic TCP provenant de l'adresse IP à partir de laquelle vous vous connectez, sur le port 22.
1. Vous devez connaître le nom d'utilisateur par défaut du système d'exploitation exécuté sur la machine virtuelle. Voir *Liste des noms d'utilisateur par défaut* ci-dessous.

### Identifier l'adresse IP

1. Accédez à l'environnement StackPath contenant la charge de travail souhaitée.
1. Cliquez sur la charge de travail pour voir ses détails.  L'écran *Détails* apparaîtra.
1. Cliquez sur l'élément *Instances* à gauche. Une liste des instances déployées dans la charge de travail s'affiche.
1. Identifiez l'instance souhaitée et notez son adresse IP publique dans la liste. Cliquer directement sur l'adresse IP la copiera dans votre presse-papiers.
![IP publique de la VM](../../assets/sp-connect-instance-public-ip-fr.png)
1. Vous êtes maintenant prêt à vous connecter à l'instance. La procédure est différente lors de l'utilisation d'un client de ligne de commande Unix standard (cela inclut macOS) par rapport à un client Windows SSH.

#### Client SSH de ligne de commande Unix standard (y compris macOS)

1. Commencez par ouvrir une fenêtre de terminal.
1. La clé privée doit être présente dans votre répertoire `~/.ssh`. Le fichier contenant la clé privée doit avoir les autorisations `0644`. Pour définir les autorisations correctes, utilisez la commande `chmod 644 <nom-du-fichier>`.
1. La forme générale d'utilisation d'une clé privée pour se connecter à un hôte distant via SSH est: `ssh -i <fichier-de-la-clé> nom-d'utilisateur@IP`. La clé doit être spécifiée avec un chemin si la clé ne se trouve pas dans le répertoire de travail actuel. Par exemple, si vous vous connectez à une instance Ubuntu à 151.139.189.1 et que le fichier de clé est dans `~/.ssh/ma.clé`, utilisez la commande suivante :
   ```
   ssh -i ~/.ssh/ma.clé ubuntu@151.139.189.1
   ```
1. Vous devriez maintenant être connecté à la machine virtuelle et voir une invite de commande. Si les privilèges root sont requis, utilisez la commande `sudo -i` pour obtenir un shell root.

#### Client SSH Windows

Il s'agit d'une procédure générique pour l'utilisation d'un client Windows SSH. Il peut être nécessaire de convertir d'abord la clé privée, puis d'installer la clé dans le client. Consultez le manuel de l'utilisateur de votre client SSH pour connaître la procédure exacte.

1. Ouvrez une nouvelle connexion dans votre client SSH.
1. Sélectionnez **SSH** comme type de connexion.
1. Entrez l'adresse IP de la VM dans le champ **Nom d'hôte** (ou **Adresse IP**).
1. Entrez le nom d'utilisateur par défaut dans le champ **Nom d'utilisateur** ou **Connexion en tant que**.
1. À ce stade, vous devrez fournir la clé privée ou l'avoir déjà installée, comme mentionné dans la note ci-dessus. Consultez le manuel d'utilisation de votre client SSH.
1. Cliquez sur **Se connecter** ou **Ouvrir**.
1. Vous devriez maintenant être connecté à la VM et voir une fenêtre avec une invite de commande. Si les privilèges root sont requis, utilisez la commande `sudo -i` pour obtenir un shell root.

### Liste des noms d'utilisateur par défaut

| Type de système d'exploitation | Nom d'utilisateur par défaut |
| --- | --- |
| CentOS | centos |
| Debian | debian |
| Ubuntu | ubuntu |

## Connexion à un conteneur

Un conteneur dans une charge de travail StackPath peut être atteint à l'aide d'un client SSH standard pour se connecter au proxy d'accès distant StackPath.

### Activer la gestion à distance

La gestion à distance doit être activée pour la charge de travail souhaitée. Si la gestion à distance est déjà activée, passez à la section suivante, *Se connecter à la console*.

1. Accédez à l'environnement StackPath contenant la charge de travail souhaitée.
1. Cliquez sur la charge de travail pour voir ses détails. L'écran *Détails* apparaîtra.
1. Cliquez sur l'élément *Réglages* à gauche. L'écran *Réglages* apparaîtra.
1. Recherchez le paramètre *Gestion à distance*. Déplacez le curseur sur la position activée, si ce n'est déjà fait.
![Activer la gestion à distance](../../assets/sp-connect-enable-remote-mgt-fr.png)

### Se connecter à la console

1. Accédez à l'environnement StackPath contenant la charge de travail souhaitée.
1. Cliquez sur la charge de travail pour voir ses détails. L'écran *Détails* apparaîtra.
1. Cliquez sur l'élément *Instances* à gauche. Une liste des instances déployées dans la charge de travail s'affiche.
1. Identifiez l'instance souhaitée et cliquez sur le menu à trois points à l'extrême droite de la ligne.
1. Cliquez sur *Accéder à la console*.
1. La boîte de dialogue *Accéder à la console* apparaîtra et la commande `/bin/bash` sera pré-remplie dans le champ de texte **Commande à exécuter**. Cliquez sur *Valider*.
1. Une notification apparaîtra, avec deux éléments importants, une commande SSH et un mot de passe.
    - Cliquez sur les icônes du presse-papiers à droite de chaque élément pour copier la commande SSH et le mot de passe dans votre presse-papiers.
    - La commande SSH est destinée à être exécutée à partir d'une ligne de commande Unix, comme dans l'application Terminal du MacOS ou du Linux.
    - Les utilisateurs Windows peuvent utiliser leur client SSH préféré pour Windows. Utilisez le numéro de port et le nom d'hôte de la commande, avec `/bin/bash` comme commande à distance à exécuter.
1. Une fois que vous avez exécuté la commande SSH et entré le mot de passe (ou configuré votre client Windows SSH et ouvert la connexion), vous aurez une invite de commande dans le conteneur cible.
