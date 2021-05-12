---
title: "Service de StackPath:  Gérer les charges de travail"
slug: stackpath-gerer-les-charges-de-travail
---


<!-- General note:  UI changes have been made for hiding the optional attributes as well as for displaying the Anycast IP.  I need to go back and update the articles for these changes, both languages. -->

Pour créer, modifier ou supprimer une charge de travail StackPath, un compte avec le rôle *Utilisateur* doit être membre de l'environnement qui contient la charge de travail et avoir également le rôle d'environnement *Éditeur* ou *Propriétaire* attribué. Un compte doté du rôle *Administrateur* ou supérieur peut créer, modifier ou supprimer des charges de travail dans n'importe quel environnement.

Pour accéder aux charges de travail, accédez à votre environnement StackPath et cliquez sur l'onglet **Charges de travail**.

### Ajouter une charge de travail

#### Attributs de base

1. Dans l'onglet **Charges de travail**, cliquez sur le bouton *Ajouter une charge de travail*.
1. Entrez un nom pour la charge de travail.
1. Sélectionnez le type de charge de travail :
    - Machine virtuelle (VM)
    - Conteneur

#### Sélectionnez une image

1. Si le type de charge de travail est **Machine Virtuelle** (**VM**), sélectionnez une image du système d'exploitation dans la liste contextuelle intitulée **Image de système d'exploitation**.
1. Si le type de charge de travail est **Conteneur**, entrez dans la zone de texte intitulée **image OS** l'URL d'où l'image du conteneur doit être extraite. Le format de l'URL doit être `URL/imageename:étiquette`, où *étiquette* indique la version à extraire. Si l'*étiquette* est omis, `default` est utilisé. Si des informations d'identification sont requises pour l'emplacement distant, cochez la case *Ajouter des informations d'identification d'extraction d'image*. Les champs pour les informations d'identification apparaîtront.

#### Variables d'environnement et réseau

1. Si le type de charge de travail est **Conteneur**, des variables d'environnement peuvent être définies et rendues accessibles au conteneur. Ces valeurs sont définies lors de l'exécution ou pendant le déploiement et sont présentées dans le conteneur en tant que variables d'environnement standard. <!-- The SP// docs seem to indicate that environment variables are available to both containers and to instances.  Also, how can multiple variables be defined in the Web UI? -->
   - **Clé et valeur de variable d'environnement** : les paires valeur / clé sont mises à disposition de toutes les instances.
   - **Clé et valeur de variable d'environnement secrètes** : identiques aux variables d'environnement, mais peuvent être utilisées pour stocker les informations d'identification en toute sécurité.
1. Sélectionnez le VPC à utiliser pour déployer la charge de travail.
   - Pour le moment, les charges de travail sont créées uniquement dans le VPC par défaut.
1. Si une adresse IP Anycast est souhaitée, cochez la case *Ajouter une adresse IP Anycast*.
1. Si les ports publics dont l'application aura besoin sont connus, ils peuvent être spécifiés en cochant la case *Ajouter des ports publics* et en remplissant les champs qui apparaissent. StackPath créera les politiques de réseau en votre nom au moment du déploiement. Ceux-ci peuvent être modifiés à tout moment après le déploiement de la charge de travail.

#### Configuration de démarrage initiale

1. Si le type de charge de travail est **VM**, au moins une clé publique doit être spécifiée dans le champ intitulé *Clé(s) SSH de premier démarrage*. La ou les clés seront automatiquement installées pour le compte d'utilisateur par défaut dans les machines virtuelles créées pour cette charge de travail.
    - Lors de la connexion aux VM via SSH, spécifiez la clé privée qui correspond à la clé publique collée ici. Pour trouver les noms d'utilisateur par défaut utilisés par StackPath, consultez [Add Users to a Virtual Machine](https://support.stackpath.com/hc/en-us/articles/360025308732-Add-Users-to-a-Virtual-Machine) (*en anglais*). La connexion par mot de passe n'est pas prise en charge.
1. Si le type de charge de travail est **Conteneur**, le champ de texte intitulé **Commandes** peut être utilisé pour spécifier les commandes à exécuter au démarrage du conteneur.  <!-- Docs say that multiple commands can be given, how are they separated, semi-colon? Comma-separated?  The API docs seem to indicate an array. -->

#### Options de calcul et de stockage

1. Sélectionnez l'offre de calcul et de mémoire à allouer pour la charge de travail dans le menu contextuel intitulé *Spec*. L'offre sera uniforme pour toutes les VM ou conteneurs déployés dans tous les PoP pour cette charge de travail.
1. Un volume de stockage supplémentaire peut être attaché à chaque instance ou conteneur:
    - Entrez un chemin (tel que `/data`) dans le champ intitulé *Chemin de montage*. Au moment du déploiement, StackPath créera un disque et le chemin spécifié sera utilisé comme point de montage à l'intérieur de la machine virtuelle ou du conteneur.
    - Entrez la taille souhaitée pour le volume persistant à l'aide de la boîte de texte intitulée *Taille*.
    - Si votre administrateur a activé plusieurs volumes persistants, un bouton intitulé *Ajouter* apparaîtra dans cette section. En cliquant sur ce bouton, un autre ensemble de boîtes de texte apparaîtra, dans lequel vous pourrez spécifier des volumes supplémentaires. Les chemins de montage **doivent être** uniques.

#### Nom du déploiement et emplacements cibles

1. Entrez un nom pour décrire le déploiement dans le champ intitulé *Nom du déploiement*.
1. L'emplacement périphérique cible (ou les emplacements) pour le déploiement de la charge de travail est spécifié dans le champ intitulé *PoPs de déploiement*. Cliquez sur le menu et la liste des PoP disponibles apparaîtra. Cliquer sur un PoP ajoutera une balise au champ. Pour supprimer un PoP sélectionné, cliquez sur le "X" à droite de la balise, et la charge de travail ne sera pas déployée là-bas.

#### Mise à l'échelle de la charge de travail

1. Sélectionnez le nombre de VM ou de conteneurs à déployer dans chaque PoP à l'aide du curseur intitulé *Instances par PoP*.
1. La mise à l'échelle automatique peut également être utilisée à la place d'un nombre statique de VM ou de conteneurs. Cochez la case *Activer la mise à l'échelle automatique* et sélectionnez les valeurs souhaitées pour les critères pour déclencher la mise à l'échelle automatique à l'aide des trois curseurs qui apparaissent :
   - *Utilisation CPU*: StackPath surveillera l'utilisation du processeur de chaque instance ou conteneur. Lorsque l'utilisation dépasse le seuil spécifié, une nouvelle machine virtuelle ou un nouveau conteneur est déployé pour absorber la charge accrue. Lorsque l'utilisation du processeur tombe à 10% en dessous de ce seuil ou moins, StackPath réduit les instances après 5 minutes après le dernier événement de mise à l'échelle automatique.
   - *Min d'instances par PoP* : le nombre minimum de VM ou de conteneurs à avoir déployé à tout moment.
   - *Max d'instances par PoP* : le nombre maximal de VM ou de conteneurs à déployer lors de la mise à l'échelle.

Une fois toutes les options sélectionnées, cliquez sur *Valider*. L'onglet **Charges de travail** apparaîtra et la nouvelle charge de travail sera répertoriée dans l'état **Actif**.

### Répertorier les charges de travail existantes

Toutes les charges de travail sont répertoriées dans l'onglet **Charges de travail**. Cliquez sur une entrée pour afficher la page *Détails de la charge de travail*, qui répertorie les attributs de la charge de travail sélectionnée.

Cliquez sur l'élément **Instances** pour afficher la page *Instances*, où toutes les VM ou conteneurs pour la charge de travail sont répertoriés. Voir [Stackpath: Gérer les instances](stackpath-working-with-instances.md).

Cliquez sur l'élément **Politiques de réseau** pour afficher la page *Politiques de réseau*, où apparaissent toutes les règles entrantes et sortantes pour cette charge de travail. Voir [Stackpath: Politiques de réseau](stackpath-network-policies.md).

### Modifier une charge de travail

Modifiez une charge de travail à partir de l'onglet **Charges de travail** en trouvant la charge de travail souhaitée et en cliquant sur le menu à trois points *Action* sur le côté droit de l'entrée et en cliquant sur *Modifier*, ou à partir de la page *Détails de la charge de travail* en cliquant sur dans le menu *Action* à trois points en haut à droite de la page.

Certains attributs ne peuvent pas être modifiés après le déploiement. Le nom de la charge de travail et du déploiement peut être modifié, ainsi que la spécification de l'offre de calcul. Les PoP de déploiement, les instances par PoP et les règles de mise à l'échelle automatique peuvent être modifiés.

Une fois les modifications terminées, cliquez sur *Valider* pour sauvegarder. Lors de l'ajout d'un PoP de déploiement ou de la modification du nombre d'instances, quelques minutes peuvent être nécessaires pour que le nouvel emplacement périphérique soit répertorié et que les VM et les conteneurs apparaissent.

### Supprimer une charge de travail

La suppression d'une charge de travail détruira toutes les instances, les conteneurs, les stratégies réseau et le stockage persistant. Cette action **ne peut pas être** annulée.

1. Dans l'onglet **Charges de travail**, recherchez la charge de travail souhaitée et cliquez sur le menu *Action* à trois points sur le côté droit de l'entrée. Une charge de travail peut également être supprimée de sa page *Détails de la charge de travail* en cliquant sur le menu *Action* à trois points en haut à droite de la page, puis en cliquant sur *Supprimer*.
1. Une boîte de dialogue apparaîtra, vous demandant de confirmer la suppression de la charge de travail. Cliquez sur *Valider*.
1. La charge de travail passera à l'état **Désactivé**. Une fois la charge de travail supprimée, elle disparaîtra de l'onglet **Charges de travail**.

### Liens externes

[Add Users to a Virtual Machine](https://support.stackpath.com/hc/en-us/articles/360025308732-Add-Users-to-a-Virtual-Machine)
