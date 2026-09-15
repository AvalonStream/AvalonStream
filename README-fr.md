<div align="center">

# Avalon

### Un PC Windows 10/11 x64. Plusieurs bureaux indépendants.

Transformez une seule machine Windows 10/11 x64 en plusieurs instances de bureau accessibles indépendamment, chacune avec son propre affichage, ses entrées, son audio, ses applications et sa connexion de streaming à distance.

**Un hôte. Plusieurs instances.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Qu’est-ce qu’Avalon ?

Avalon est une plateforme de streaming de bureau multisession pour Windows 10/11 x64.

Au lieu de limiter un PC à un seul bureau interactif, Avalon permet à une même machine d’héberger plusieurs instances Windows indépendantes simultanément.

Chaque instance peut disposer de ses propres éléments :

- session de bureau Windows
- écran virtuel
- résolution et fréquence de rafraîchissement
- flux d’entrée
- flux audio
- applications et jeux
- connexion distante via Moonlight

Un PC puissant peut ainsi se comporter davantage comme plusieurs ordinateurs accessibles à distance, sans devoir exécuter une machine virtuelle complète pour chaque utilisateur.

---

## À quoi cela ressemble-t-il concrètement ?

Imaginons un PC Windows 10/11 x64 exécutant trois instances Avalon :

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Chaque client se connecte à son propre bureau Windows.

Les instances fonctionnent côte à côte sans partager le même bureau, le même pointeur de souris, la même sortie audio ni la même session d’application.

---

## Pourquoi Avalon ?

Les outils traditionnels de bureau à distance sont généralement conçus autour d’un utilisateur contrôlant un seul bureau.

Les machines virtuelles assurent une forte isolation, mais elles ajoutent aussi des systèmes d’exploitation supplémentaires, une consommation mémoire plus élevée, davantage de stockage, une configuration GPU plus complexe et un coût d’administration supérieur.

Avalon adopte une autre approche.

Il combine les sessions Windows, les écrans virtuels, des processus de streaming indépendants et une gestion centralisée du cycle de vie afin que plusieurs bureaux interactifs puissent coexister sur un même hôte Windows 10/11 x64.

La complexité reste dans Avalon. Pour l’utilisateur, le parcours est simple :

```text
Créer une instance
        ↓
Configurer l’affichage et l’appairage
        ↓
Ouvrir Moonlight
        ↓
Se connecter
```

---

## Capacités principales

### Plusieurs instances indépendantes

Exécutez plusieurs sessions de bureau Windows sur le même hôte au même moment.

Chaque instance se comporte comme son propre environnement de bureau interactif.

### Streaming indépendant

Chaque instance possède son propre contexte de streaming et peut être rejointe indépendamment à l’aide d’un client Moonlight.

Un téléviseur peut être connecté à une instance tandis qu’une tablette ou un autre ordinateur se connecte simultanément à une autre.

### Affichage indépendant

Chaque instance peut utiliser sa propre configuration d’écran virtuel, notamment sa résolution et sa fréquence de rafraîchissement.

Avalon gère l’environnement d’affichage sans nécessiter un moniteur physique pour chaque instance.

### Entrées indépendantes

Les entrées clavier et souris sont dirigées vers la session Windows concernée au lieu d’être partagées entre toutes les instances.

À mesure que la pile d’entrée évolue, Avalon est conçu pour progresser vers une isolation des périphériques toujours plus complète par instance.

### Audio indépendant

Chaque instance utilise son propre chemin audio de session Windows. Des utilisateurs différents peuvent donc écouter des applications ou des jeux différents sans que les flux audio soient simplement mélangés entre les instances.

### Gestion du cycle de vie des sessions

Avalon crée et maintient lui-même les sessions.

Il n’est pas nécessaire de laisser un client RDP externe connecté en permanence uniquement pour conserver une instance active.

### Administration Web

Toutes les instances sont administrées depuis une interface Web unique.

Les opérations courantes comprennent :

- créer et supprimer des instances
- démarrer et arrêter des instances
- configurer la résolution et la fréquence de rafraîchissement
- appairer les clients Moonlight
- vérifier l’état des connexions
- consulter les diagnostics
- gérer les paramètres du système hôte

L’utilisation quotidienne ne nécessite pas de ligne de commande.

---

## Conçu pour Moonlight

Avalon conserve l’expérience de streaming Moonlight que vous connaissez déjà.

Vous pouvez continuer à utiliser Moonlight sur des appareils tels que :

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- les téléviseurs intelligents et appareils de streaming compatibles Moonlight

Avalon modifie l’organisation côté hôte, sans imposer l’apprentissage d’un tout nouveau client de streaming.

---

## Cas d’usage

### Jeu à domicile

Transformez un seul PC gaming en plusieurs environnements de jeu indépendants pour différentes personnes d’un même foyer.

Une personne peut jouer sur la télévision du salon tandis qu’une autre se connecte à une autre instance depuis une console portable ou un ordinateur portable.

### Plusieurs comptes et plusieurs instances

Exécutez différentes applications, différents comptes ou différentes sessions de jeu dans des environnements Windows séparés sur la même machine.

### Poste de travail distant

Utilisez un ordinateur de bureau puissant comme plusieurs espaces de travail distants accessibles indépendamment.

### Tests et développement

Maintenez plusieurs sessions Windows pour les tests logiciels, l’automatisation, la validation de compatibilité ou des environnements utilisateurs isolés.

### Homelab et auto-hébergement

Utilisez une machine Windows performante comme hôte de calcul distant multi-utilisateur géré de façon centralisée.

---

## Comment fonctionne Avalon ?

Avalon coordonne en interne plusieurs couches du système :

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

Un utilisateur normal n’a pas besoin de comprendre ces détails d’implémentation.

Vous créez une instance ; Avalon prépare la session, l’affichage, l’environnement de streaming et son cycle de vie ; vous vous connectez ensuite.

---

## Modèle d’isolation

Avalon fournit une **isolation au niveau des sessions Windows**.

Chaque instance possède sa propre session Windows, son bureau, ses applications, son affichage, son chemin d’entrée et son chemin audio.

Cependant, les instances Avalon **ne sont pas des machines virtuelles complètes**.

Elles partagent toujours :

- la même installation Windows de l’hôte
- le même noyau
- le même processeur physique
- le même GPU physique
- les mêmes ressources matérielles de l’hôte

Avalon ne doit donc pas être considéré comme une frontière de sécurité équivalente à une VM.

Son objectif est un streaming multi-utilisateur et multi-bureau efficace, et non une virtualisation matérielle complète.

---

## État actuel

Avalon est actuellement en phase **Alpha**.

L’architecture, l’interface d’administration, la couche de compatibilité et la pile de périphériques continuent d’évoluer.

Pendant cette phase, il faut s’attendre notamment à :

- des changements incompatibles
- une compatibilité matérielle encore incomplète
- des changements d’interface
- des cas limites liés aux pilotes et aux sessions
- des fonctions dont le comportement peut encore évoluer avant une version stable

Avalon n’est pas encore destiné à une infrastructure critique de production.

Les tests, les journaux, les rapports de bugs reproductibles et les retours d’usage réels sont particulièrement précieux à ce stade.

---

## Plateforme

Cible actuelle :

```text
Windows 10 x64 / Windows 11 x64
```

Avalon est conçu spécifiquement autour du modèle de bureau, de sessions et de graphiques de Windows.

La prise en charge d’autres systèmes d’exploitation hôtes n’est pas actuellement un objectif principal du projet.

---

## Performances

Les performances réelles du streaming dépendent de nombreux facteurs, notamment :

- GPU
- prise en charge de l’encodeur
- pilote graphique
- résolution
- fréquence de rafraîchissement
- codec
- qualité du réseau
- capacité de décodage du client
- nombre d’instances simultanées

Avalon ne garantit pas une résolution, une fréquence de rafraîchissement, un mode HDR ou un nombre précis d’instances simultanées sur tous les systèmes.

La documentation de compatibilité deviendra plus détaillée à mesure que les tests s’étendront.

---

## Philosophie du projet

Avalon repose sur une idée simple :

> Un PC puissant ne devrait pas être constamment limité à un écran, un bureau et un utilisateur.

L’hôte peut être une seule machine. Les expériences qui y fonctionnent n’ont pas besoin d’être uniques.

---

## Développement

Ce README est maintenu comme présentation stable du produit Avalon.

Pour les mises à jour de développement en temps réel et les messages du projet, consultez [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Pour signaler un bug, poser une question ou proposer une fonctionnalité, utilisez [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Un hôte. Plusieurs instances.**

</div>
