# Avalon

### Un PC Windows 10/11 x64. Plusieurs bureaux indépendants.

Avalon transforme un hôte Windows 10/11 x64 en plusieurs instances de bureau accessibles indépendamment. Chaque instance peut disposer de sa propre session Windows, d’un affichage virtuel, de ses entrées, de son audio, de ses applications, de ses jeux et de sa connexion Moonlight.

**Un hôte. Plusieurs instances.**

[English](README.md)

[Journal de développement et retours](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bugs et demandes](https://github.com/AvalonStream/AvalonStream/issues)

---

## Qu’est-ce qu’Avalon ?

Avalon est une plateforme de streaming de bureau multisession pour Windows 10/11 x64. Au lieu de réserver tout le PC à un seul bureau interactif, plusieurs instances Windows indépendantes peuvent fonctionner en parallèle sur le même hôte sans nécessiter une machine virtuelle complète par utilisateur.

---

## Fonctions principales

- Plusieurs instances Windows indépendantes sur un seul hôte
- Un contexte de streaming dédié pour chaque instance
- Affichage virtuel, résolution et fréquence de rafraîchissement par instance
- Chemins clavier, souris et audio de session indépendants
- Avalon maintient le cycle de vie des sessions sans laisser un client RDP externe connecté
- Création, appairage, état et diagnostic depuis le Web
- Moonlight reste le client sur téléphones, tablettes, téléviseurs et PC

---

## Fonctionnement

Créez une instance, choisissez ses paramètres d’affichage et associez un client. Avalon prépare la session Windows, l’affichage virtuel, le contexte de streaming et le cycle de vie ; vous vous connectez ensuite avec Moonlight.

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Conçu pour Moonlight

Avalon modifie le côté hôte sans remplacer le client que vous connaissez déjà. Moonlight reste utilisable sous Windows, Linux, macOS, Android, iOS/iPadOS, Android TV et sur les autres appareils pris en charge.

---

## Cas d’usage typiques

- Jeu à domicile : plusieurs personnes utilisent des instances différentes en même temps
- Comptes multiples et charges multi-instance
- Plusieurs postes distants sur un seul PC puissant
- Tests, automatisation et environnements de compatibilité
- Homelab et informatique distante auto-hébergée

---

## Modèle d’isolation

Avalon fournit une isolation au niveau des sessions Windows, et non une isolation complète de machine virtuelle. Les bureaux, applications, affichages, entrées et flux audio sont séparés, mais Windows, le noyau, le CPU, le GPU et le matériel physique de l’hôte sont partagés. Avalon ne constitue donc pas une frontière de sécurité équivalente à une VM.

---

## Plateforme et performances

Avalon cible Windows 10 et Windows 11 en 64 bits. La résolution, la fréquence, les codecs, le HDR et le nombre d’instances simultanées dépendent du GPU, des pilotes, de l’encodeur, du réseau et du matériel client.

---

## État du projet

Avalon est actuellement en phase Alpha. L’interface, la compatibilité et les composants bas niveau continuent d’évoluer ; des changements incompatibles et des cas limites matériels peuvent donc survenir.

---

## Développement et retours

Ce README constitue la présentation stable du produit. Les avancées en temps réel et les consignes de retour sont maintenues séparément dans le journal de développement.

- [Journal de développement et retours](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bugs et demandes](https://github.com/AvalonStream/AvalonStream/issues)

**Un hôte. Plusieurs instances.**
