# Retour au menu
- [Menu README](../README.md)

# CM1 - Fondamentaux et Modèles Réseaux

## Table des matières

1. [Objectifs d'apprentissage](#objectifs)
2. [Introduction aux réseaux informatiques](#introduction)
3. [Types et classifications de réseaux](#types)
4. [Topologies réseau](#topologies)
5. [Supports de transmission](#supports)
6. [Le modèle OSI](#modele-osi)
7. [Le modèle TCP/IP](#modele-tcpip)
8. [Comparaison OSI vs TCP/IP](#comparaison)
9. [Encapsulation et désencapsulation](#encapsulation)
10. [Exercices d'auto-évaluation](#exercices)
11. [Ressources complémentaires](#ressources)

---

## Objectifs d'apprentissage {#objectifs}

À l'issue de ce cours, vous serez capable de :

- **Définir** ce qu'est un réseau informatique et ses composants essentiels
- **Identifier** les différents types de réseaux et leurs caractéristiques
- **Expliquer** les principales topologies réseau et leurs avantages/inconvénients
- **Décrire** les supports de transmission et leurs propriétés
- **Maîtriser** le modèle OSI et ses 7 couches
- **Comprendre** le modèle TCP/IP et son architecture en 4 couches
- **Comparer** les deux modèles de référence
- **Expliquer** les mécanismes d'encapsulation et de désencapsulation

---

## Introduction aux réseaux informatiques {#introduction}

### Qu'est-ce qu'un réseau informatique ?

Un **réseau informatique** est un ensemble d'équipements (ordinateurs, serveurs, imprimantes, smartphones, etc.) interconnectés entre eux pour permettre l'**échange de données** et le **partage de ressources**.

### Composants essentiels d'un réseau

Un réseau informatique se compose de plusieurs éléments fondamentaux :

#### 1. Les équipements terminaux (hôtes)
- **Ordinateurs** : postes de travail, serveurs
- **Périphériques** : imprimantes, scanners
- **Appareils mobiles** : smartphones, tablettes
- **Objets connectés** : IoT (Internet of Things)

#### 2. Les équipements d'interconnexion
- **Commutateurs (Switch)** : interconnectent les équipements au sein d'un même réseau local
- **Routeurs** : interconnectent différents réseaux entre eux
- **Points d'accès Wi-Fi** : permettent les connexions sans fil
- **Ponts (Bridge)** : relient deux segments de réseau

#### 3. Les supports de transmission
- **Câbles** : cuivre (Ethernet), fibre optique
- **Sans fil** : Wi-Fi, Bluetooth, 4G/5G
- **Satellite** : communications longue distance

#### 4. Les protocoles
Ensemble de règles et conventions qui régissent la communication entre équipements.

### Pourquoi des réseaux ?

Les réseaux informatiques répondent à plusieurs besoins essentiels :

**Partage de ressources :**
- Fichiers et documents
- Imprimantes et scanners
- Connexion Internet
- Applications et logiciels

**Communication :**
- Email, messagerie instantanée
- Visioconférence
- VoIP (téléphonie sur IP)

**Centralisation :**
- Stockage centralisé des données
- Gestion centralisée des utilisateurs
- Sauvegarde et sécurité

**Collaboration :**
- Travail collaboratif en temps réel
- Partage de calendriers
- Gestion de projets

---

## Types et classifications de réseaux {#types}

Les réseaux se classifient principalement selon leur **échelle géographique** et leur **étendue**.

### PAN (Personal Area Network)

**Définition :** Réseau personnel, très courte portée (quelques mètres)

**Caractéristiques :**
- Portée : 0-10 mètres
- Usage : connexion entre appareils personnels
- Technologies : Bluetooth, USB, NFC

**Exemples :**
- Connexion smartphone ↔ écouteurs Bluetooth
- Montre connectée ↔ smartphone
- Clavier/souris sans fil ↔ ordinateur

### LAN (Local Area Network)

**Définition :** Réseau local, limité à une zone géographique restreinte

**Caractéristiques :**
- Portée : 10 mètres - 1 km
- Usage : entreprise, domicile, campus
- Technologies : Ethernet (câblé), Wi-Fi (sans fil)
- Vitesse : 100 Mbps - 10 Gbps (et au-delà)
- Propriété : généralement privé

**Exemples :**
- Réseau d'une maison (box Internet + appareils)
- Réseau d'un bureau ou d'une entreprise
- Réseau d'une école ou université

**Avantages :**
- ✅ Haute vitesse de transmission
- ✅ Faible latence
- ✅ Coûts modérés
- ✅ Sécurité maîtrisable

### MAN (Metropolitan Area Network)

**Définition :** Réseau métropolitain, couvre une ville ou agglomération

**Caractéristiques :**
- Portée : 1-50 km
- Usage : interconnexion de plusieurs LAN d'une ville
- Technologies : fibre optique, liaisons micro-ondes
- Propriété : souvent opérateurs télécoms ou collectivités

**Exemples :**
- Réseau d'une université multi-sites
- Réseau municipal (hôpitaux, écoles, mairies)
- Réseau câblé TV d'une ville

### WAN (Wide Area Network)

**Définition :** Réseau étendu, couvre de grandes distances (pays, continent, monde)

**Caractéristiques :**
- Portée : illimitée (mondial)
- Usage : interconnexion de réseaux distants
- Technologies : fibre optique, satellite, lignes louées
- Propriété : opérateurs télécoms

**Exemples :**
- **Internet** : le WAN le plus connu
- Réseau d'entreprise multinationale
- Réseaux d'opérateurs télécoms

**Caractéristiques techniques :**
- Vitesse variable selon la distance
- Latence plus élevée
- Coûts importants
- Complexité de gestion

### Tableau récapitulatif

| Type    | Portée   | Zone typique    | Vitesse        | Exemple              |
|---------|----------|-----------------|----------------|----------------------|
| **PAN** | 0-10m    | Personnel       | Faible-Moyenne | Bluetooth smartphone |
| **LAN** | 10m-1km  | Bâtiment/Campus | Très élevée    | Réseau entreprise    |
| **MAN** | 1-50km   | Ville           | Élevée         | Réseau universitaire |
| **WAN** | Illimité | Pays/Monde      | Variable       | Internet             |

### Autres classifications

**Selon la propriété :**
- **Privé** : appartient à une organisation (intranet)
- **Public** : accessible à tous (Internet)

**Selon la topologie :**
- Client-serveur
- Peer-to-peer (P2P)

---

## Topologies réseau {#topologies}

La **topologie** désigne l'architecture physique ou logique d'organisation des équipements dans un réseau.

### Topologie en bus

**Description :**  
Tous les équipements sont connectés à un câble unique (le bus).

```
====|=======|=======|=======|=======|========= Bus
    |       |       |       |       |
  [PC1]   [PC2]   [PC3]   [PC4]   [PC5]

```

**Avantages :**
- ✅ Simple à mettre en œuvre
- ✅ Coût faible (peu de câbles)
- ✅ Facilité d'ajout d'équipements

**Inconvénients :**
- ❌ Rupture du bus = panne totale
- ❌ Difficile de localiser les pannes
- ❌ Performance dégradée avec nombreux équipements
- ❌ Collisions fréquentes

**Usage :** Obsolète aujourd'hui, utilisé dans les anciens réseaux Ethernet 10Base2.

### Topologie en étoile

**Description :**  
Tous les équipements sont connectés à un point central (switch, hub).

```
        [PC2]
          |
[PC1]---[Switch]---[PC3]
          |
        [PC4]
```

**Avantages :**
- ✅ Panne d'un équipement = autres non affectés
- ✅ Facilité de dépannage (isolation)
- ✅ Facilité d'ajout/retrait d'équipements
- ✅ Performance maintenue

**Inconvénients :**
- ❌ Panne du point central = panne totale
- ❌ Coût plus élevé (plus de câbles)
- ❌ Dépendance au switch central

**Usage :** **Topologie la plus utilisée** dans les LAN modernes (Ethernet avec switch).

### Topologie en anneau

**Description :**  
Les équipements sont connectés en boucle fermée, les données circulent dans un sens.

```
[PC1]---[PC2]
  |       |
[PC4]---[PC3]
```

**Avantages :**
- ✅ Pas de collisions (jeton passant)
- ✅ Performance prévisible
- ✅ Équitable (chaque station a accès)

**Inconvénients :**
- ❌ Rupture d'un lien = panne totale (sauf double anneau)
- ❌ Difficulté d'ajout/retrait
- ❌ Plus complexe à gérer

**Usage :** Token Ring (IBM), FDDI. Rare aujourd'hui.

### Topologie linéaire

**Description :**
Les équipements sont connectés les uns à la suite des autres, formant une ligne droite.
Les données circulent d’un poste à l’autre jusqu’à atteindre leur destination.

```
 [PC1]---[PC2]---[PC3]---[PC4]
```

**Avantages :**
- ✅ Installation simple et économique
- ✅ Facile à comprendre et à mettre en œuvre
- ✅ Moins de câblage qu’une étoile

**Inconvénients :**
- ❌ Rupture d’un câble = réseau partiellement ou totalement coupé
- ❌ Performances limitées avec beaucoup de stations
- ❌ Difficile à dépanner et à étendre

**Usage :** Utilisée dans les premiers réseaux Ethernet coaxiaux (10Base2, 10Base5).
Aujourd’hui, remplacée par la topologie en étoile.

### Topologie maillée

**Description :**  
Chaque équipement est connecté à plusieurs (voire tous) les autres.

**Maillage complet :**
```
[PC1]---[PC2]
  |  \ /  |
  |   X   |
  |  / \  |
[PC3]---[PC4]
```

**Maillage partiel :**  
Seulement certains liens multiples (compromis coût/redondance).

**Avantages :**
- ✅ Très haute disponibilité
- ✅ Redondance maximale
- ✅ Pas de point unique de défaillance
- ✅ Équilibrage de charge possible

**Inconvénients :**
- ❌ Coût très élevé (nombreux câbles/interfaces)
- ❌ Complexité de configuration
- ❌ Difficile à maintenir

**Usage :** Réseaux critiques (datacenters, backbones Internet), réseaux sans fil mesh.

### Topologie hybride

**Description :**  
Combinaison de plusieurs topologies (la plus courante en pratique).

**Exemple : Étoile étendue (hiérarchique)**
```
            [Routeur]
               |
        [Switch Core]
         /    |    \
  [Switch1][Switch2][Switch3]
    /  \      /  \     /  \
  [PC] [PC] [PC] [PC] [PC] [PC]
```

**Avantages :**
- ✅ Flexibilité maximale
- ✅ Optimisation coût/performance
- ✅ Évolutivité

**Usage :** Quasi-totalité des réseaux d'entreprise modernes.

### Tableau comparatif

| Topologie   | Fiabilité   | Coût     | Complexité | Usage actuel      |
|-------------|-------------|----------|------------|-------------------|
| **Bus**     | Faible      | Faible   | Faible     | Obsolète          |
| **Étoile**  | Moyenne     | Moyen    | Faible     | Très courant      |
| **Anneau**  | Moyenne     | Moyen    | Moyenne    | Rare              |
| **Maillée** | Très élevée | Élevé    | Élevée     | Réseaux critiques |
| **Hybride** | Variable    | Variable | Variable   | Standard          |

---

## Supports de transmission {#supports}

Les supports de transmission sont les **médias physiques** permettant la circulation des données.

### Câbles à paires torsadées (cuivre)

**Description :**  
Câbles contenant plusieurs paires de fils de cuivre torsadés ensemble pour réduire les interférences.

**Types principaux :**
- **UTP (Unshielded Twisted Pair)** : non blindé, le plus courant
- **STP (Shielded Twisted Pair)** : Chaque paire de fils est blindée individuellement, Bonne protection
- **FTP (Foiled Twisted Pair)** : Une feuille métallique entoure toutes les paires torsadées, Bonne protection contre les interférences, flexible
- **S/FTP (Shielded Fioled Twisted Pais)**: Blindage individuel des paires et un blindage global, Protection maximale contre les interférences, Coûteux et peu flexible

**Catégories Ethernet :**

| Catégorie     | Bande passante | Vitesse max | Usage           |
|---------------|----------------|-------------|-----------------|
| **Cat 5**     | 100 MHz        | 100 Mbps    | Obsolète        |
| **Cat 5e**    | 100 MHz        | 1 Gbps      | Minimum actuel  |
| **Cat 6**     | 250 MHz        | 1-10 Gbps   | Standard actuel |
| **Cat 6a**    | 500 MHz        | 10 Gbps     | Professionnel   |
| **Cat 7**     | 600 MHz        | 10 Gbps     | Datacenter      |
| **Cat 8**     | 2000 MHz       | 40 Gbps     | Datacenter      |

**Connecteurs :** RJ45 (8P8C)

**Sertissage :** l’art de relier le connecteur au bout du câble

**Disposition des fils pour le sertissage:**

```
 1 : blanc-orange
 2 : orange
 3 : blanc-vert
 4 : bleu
 5 : blanc-bleu
 6 : vert
 7 : blanc-marron
 8 : marron
```

**Transmission :** 1 et 2
**Réception :** 3 et 6

**Les Types de câbles sertis:**
- **Les câbles droits :** ordre des fils est identique dans chaque connecteur RJ45
```
   _                _
 1  |              |  1
 2  |              |  2
 3  |              |  3
 4  |==============|  4
 5  |              |  5
 6  |              |  6
 7  |              |  7
 8 _|              |_ 8

```

- **Les câbles crooisés :** l'ordre des fils n'est pas identique dans chaque connecteur RJ45
```
   _                _
 1  |              |  3
 2  |              |  6
 3  |              |  1
 4  |==============|  4
 5  |              |  5
 6  |              |  2
 7  |              |  7
 8 _|              |_ 8

```
Aujourd’hui on n’utilise plus que des câbles droits car les cartes réseaux savent différencier facilement la Transmission de la Réception.

**Avantages :**
- ✅ Coût faible
- ✅ Facile à installer
- ✅ Alimentation PoE possible
- ✅ Standard bien établi

**Inconvénients :**
- ❌ Distance limitée (100m pour Ethernet)
- ❌ Sensible aux interférences électromagnétiques
- ❌ Bande passante limitée
- ❌ Vulnérable aux écoutes

**Portée typique :** 100 mètres (Ethernet)

### Fibre optique

**Description :**  
Câble utilisant la lumière pour transmettre les données à travers des fils de verre ou plastique.

**Principe :** Réflexion totale interne de la lumière dans le cœur de la fibre.

**Types de fibres :**

**1. Fibre monomode (Single Mode - SMF)**
- Cœur très fin (8-10 µm)
- Un seul mode de propagation
- Longue distance (jusqu'à 100+ km)
- Laser comme source lumineuse
- Coût plus élevé
- Usage : backbones, WAN, interconnexions longue distance

**2. Fibre multimode (Multi Mode - MMF)**
- Cœur plus large (50-62,5 µm)
- Plusieurs modes de propagation
- Distance moyenne (jusqu'à 2 km)
- LED comme source lumineuse
- Coût inférieur
- Usage : LAN, datacenters

**Connecteurs courants :**
- LC (Lucent Connector) : compact, le plus utilisé
- SC (Subscriber Connector) : carré
- ST (Straight Tip) : bayonnette

**Avantages :**
- ✅ Très haute bande passante (Tbps)
- ✅ Très longue distance
- ✅ Immunité aux interférences électromagnétiques
- ✅ Sécurité (difficile à intercepter)
- ✅ Faible atténuation
- ✅ Légère et compacte

**Inconvénients :**
- ❌ Coût plus élevé (équipements et installation)
- ❌ Installation plus délicate
- ❌ Nécessite des compétences spécifiques
- ❌ Fragile (rayon de courbure à respecter)

**Portée :** 2 km (multimode) à 100+ km (monomode)

### Sans fil (Wireless)

**Technologies principales :**

**1. Wi-Fi (IEEE 802.11)**
- Fréquences : 2,4 GHz, 5 GHz, 6 GHz (Wi-Fi 6E)
- Portée : 30-100 mètres en intérieur
- Vitesse : 54 Mbps (802.11g) à 9,6 Gbps (Wi-Fi 6)
- Usage : LAN sans fil

**2. Bluetooth**
- Fréquence : 2,4 GHz
- Portée : 10-100 mètres
- Vitesse : jusqu'à 3 Mbps
- Usage : PAN, périphériques

**3. Réseaux cellulaires (4G/5G)**
- Fréquences variables (700 MHz - 39 GHz)
- Portée : plusieurs kilomètres
- Vitesse : 100 Mbps (4G) à 10 Gbps (5G)
- Usage : WAN mobile

**Avantages :**
- ✅ Mobilité totale
- ✅ Pas de câblage
- ✅ Installation rapide
- ✅ Flexibilité

**Inconvénients :**
- ❌ Bande passante partagée
- ❌ Sécurité plus difficile
- ❌ Interférences possibles
- ❌ Portée limitée
- ❌ Moins stable que filaire

### Comparaison des supports

| Support        | Débit max  | Distance max | Coût | Sécurité | Usage          |
|----------------|------------|--------------|------|----------|----------------|
| **Cuivre UTP** | 10 Gbps    | 100m         | €    | Moyenne  | LAN standard   |
| **Fibre MM**   | 100 Gbps   | 2 km         | €€   | Élevée   | LAN/Datacenter |
| **Fibre SM**   | 100+ Gbps  | 100+ km      | €€€  | Élevée   | WAN/Backbone   |
| **Wi-Fi**      | 10 Gbps    | 100m         | €    | Faible   | LAN mobile     |

---

## Le modèle OSI {#modele-osi}

### Introduction au modèle OSI

Le modèle **OSI (Open Systems Interconnection)** est un modèle de référence développé par l'**ISO (International Organization for Standardization)** dans les années 1980.

**Objectifs :**
- Standardiser les communications réseau
- Permettre l'interopérabilité entre systèmes hétérogènes
- Faciliter la conception et le dépannage
- Décomposer la complexité en couches indépendantes

**Principe fondamental :** Séparation des fonctions en **7 couches** empilées, chaque couche fournissant des services à la couche supérieure.

### Les 7 couches du modèle OSI

```
┌─────────────────────────────────┐
│  7. APPLICATION                 │  ← Proche de l'utilisateur
├─────────────────────────────────┤
│  6. PRÉSENTATION                │
├─────────────────────────────────┤
│  5. SESSION                     │
├─────────────────────────────────┤
│  4. TRANSPORT                   │
├─────────────────────────────────┤
│  3. RÉSEAU                      │
├─────────────────────────────────┤
│  2. LIAISON DE DONNÉES          │
├─────────────────────────────────┤
│  1. PHYSIQUE                    │  ← Proche du matériel
└─────────────────────────────────┘
```

**Mnémotechnique :** *"Apprentissage Par Surprise, Toujours Réussir, Lors Des Pratiques"*

### Couche 1 : Physique (Physical)

**Rôle :** Transmission des **bits** sur le support physique.

**Fonctions :**
- Conversion des données en signaux électriques, optiques ou radio
- Définition des caractéristiques du support (tensions, fréquences)
- Codage des bits (Manchester, NRZ, etc.)
- Synchronisation des horloges

**Unité de données :** Bit

**Équipements :**
- Câbles (cuivre, fibre)
- Connecteurs (RJ45, LC)
- Répéteurs
- Hubs (concentrateurs)
- Cartes réseau (interface physique)

**Exemples de standards :**
- Ethernet : 10Base-T, 100Base-TX, 1000Base-T
- Fibre : 1000Base-LX, 10GBase-SR
- Wi-Fi : IEEE 802.11 (couches 1 et 2)

### Couche 2 : Liaison de données (Data Link)

**Rôle :** Transmission **fiable** des trames entre deux équipements **directement connectés**.

**Fonctions :**
- Formation des trames (framing)
- Adressage physique (adresses MAC)
- Contrôle d'accès au support (MAC - Medium Access Control)
- Détection et correction d'erreurs (CRC)
- Contrôle de flux

**Unité de données :** Trame (Frame)

**Sous-couches :**
- **LLC (Logical Link Control)** : interface avec couche 3
- **MAC (Media Access Control)** : accès au support

**Équipements :**
- Switch (commutateur)
- Pont (bridge)
- Carte réseau (adresse MAC)

**Adresse MAC :**
Une adresse MAC (Media Access Control) est un identifiant unique attribué à chaque carte réseau. Elle permet d’identifier un appareil de manière unique sur un réseau local (LAN).
C’est une chaîne de 48 bits (6 octets) généralement représentée sous forme hexadécimale :
```
AA:BB:CC:DD:EE:FF
```
- **Unique au monde (théoriquement)**: chaque carte réseau devrait avoir une adresse MAC unique.
- **Structure**:
  - **Première moitié (OUI – Organizationally Unique Identifier)** : identifie le constructeur de la carte réseau.
  - **Seconde moitié (NIC – Network Interface Controller)** : correspond à un numéro de série unique attribué par le fabricant.

**Exemples de protocoles :**
- Ethernet (IEEE 802.3)
- Wi-Fi (IEEE 802.11)
- PPP (Point-to-Point Protocol)

### Couche 3 : Réseau (Network)

**Rôle :** **Routage** des paquets entre réseaux différents, adressage logique.

**Fonctions :**
- Adressage logique (IP)
- Routage (choix du meilleur chemin)
- Fragmentation et réassemblage des paquets
- Gestion de la congestion

**Unité de données :** Paquet (Packet)

**Équipements :**
- Routeur
- Switch de niveau 3 (Layer 3 switch)

**Protocoles principaux :**
- **IP (Internet Protocol)** : IPv4, IPv6
- **ICMP** : messages de contrôle (ping)
- **ARP** : résolution adresse IP → MAC
- Protocoles de routage : RIP, OSPF, BGP

**Adresse IP :**
- IPv4 : 32 bits (ex: 192.168.1.10)
- IPv6 : 128 bits (ex: 2001:0db8::1)
- Adressage logique, hiérarchique
- Permet le routage entre réseaux

### Couche 4 : Transport (Transport)

**Rôle :** Communication **de bout en bout** entre applications, fiabilité.

**Fonctions :**
- Segmentation et réassemblage des données
- Contrôle de flux
- Contrôle d'erreur de bout en bout
- Multiplexage (plusieurs applications simultanées)
- Numérotation de port (identification des applications)

**Unité de données :** Segment (TCP) ou Datagramme (UDP)

**Équipements :** Aucun équipement spécifique (logique dans les hôtes)

**Protocoles principaux :**

**TCP (Transmission Control Protocol)**
- **Orienté connexion** (établissement de session)
- **Fiable** : accusés de réception, retransmission
- **Ordonné** : séquencement des segments
- **Contrôle de flux et de congestion**
- Usage : HTTP, FTP, SSH, Email

**UDP (User Datagram Protocol)**
- **Sans connexion**
- **Non fiable** : pas d'accusé de réception
- **Rapide et léger**
- Usage : DNS, streaming vidéo, VoIP, jeux en ligne

**Ports :**
- Numéros de 0 à 65535
- 0-1023 : ports bien connus (HTTP=80, HTTPS=443, SSH=22)
- 1024-49151 : ports enregistrés
- 49152-65535 : ports dynamiques/privés

### Couche 5 : Session (Session)

**Rôle :** Gestion des **sessions** de communication entre applications.

**Fonctions :**
- Établissement, maintien et fermeture des sessions
- Synchronisation des dialogues
- Gestion des jetons (tour de parole)
- Points de reprise en cas d'interruption

**Unité de données :** Données

**Protocoles :**
- NetBIOS
- RPC (Remote Procedure Call)
- SQL sessions

**Note :** Cette couche est souvent intégrée dans les couches 4 ou 7 dans les implémentations modernes.

### Couche 6 : Présentation (Presentation)

**Rôle :** **Format et représentation** des données.

**Fonctions :**
- Traduction entre formats de données
- Chiffrement et déchiffrement
- Compression et décompression
- Conversion de caractères (ASCII, Unicode)

**Unité de données :** Données

**Exemples :**
- Chiffrement : SSL/TLS
- Formats : JPEG, GIF, PNG, MPEG
- Encodage : ASCII, EBCDIC, Unicode

**Note :** Comme la couche 5, souvent intégrée dans la couche 7.

### Couche 7 : Application (Application)

**Rôle :** Interface entre l'utilisateur et le réseau, **services réseau**.

**Fonctions :**
- Services réseau pour les applications utilisateur
- Interface utilisateur
- Accès aux ressources réseau

**Unité de données :** Données

**Protocoles courants :**
- **HTTP/HTTPS** : Web (ports 80/443)
- **FTP** : transfert de fichiers (port 21)
- **SMTP** : envoi d'emails (port 25)
- **POP3/IMAP** : réception d'emails (ports 110/143)
- **DNS** : résolution de noms (port 53)
- **SSH** : accès distant sécurisé (port 22)
- **Telnet** : accès distant non sécurisé (port 23)
- **DHCP** : attribution automatique d'IP (ports 67/68)

**Distinction importante :**
- Couche Application ≠ Applications logicielles
- C'est le **protocole** utilisé par l'application
- Ex : Firefox utilise le protocole HTTP (couche 7)

### Tableau récapitulatif OSI

| Couche | Nom          | Rôle principal   | Unité   | Équipement  | Protocoles      |
|--------|--------------|------------------|---------|-------------|-----------------|
| **7**  | Application  | Services réseau  | Données | -           | HTTP, FTP, DNS  |
| **6**  | Présentation | Format données   | Données | -           | SSL/TLS, JPEG   |
| **5**  | Session      | Gestion sessions | Données | -           | NetBIOS, RPC    |
| **4**  | Transport    | Bout en bout     | Segment | -           | TCP, UDP        |
| **3**  | Réseau       | Routage          | Paquet  | Routeur     | IP, ICMP        |
| **2**  | Liaison      | Trame locale     | Trame   | Switch      | Ethernet, Wi-Fi |
| **1**  | Physique     | Bits             | Bit     | Hub, Câbles | 10Base-T, Fibre |

---

## 🌐 Le modèle TCP/IP {#modele-tcpip}

### Introduction au modèle TCP/IP

Le modèle **TCP/IP (Transmission Control Protocol/Internet Protocol)** est le modèle utilisé par **Internet** et la plupart des réseaux modernes.

**Historique :**
- Développé par le **DoD (Department of Defense)** américain dans les années 1970
- Plus ancien que le modèle OSI (1970s vs 1980s)
- Approche **pragmatique** basée sur l'implémentation réelle
- Standard de facto d'Internet

**Différence avec OSI :**
- OSI : modèle théorique de référence
- TCP/IP : suite de protocoles réellement implémentée

### Architecture en 4 couches

Le modèle TCP/IP comprend **4 couches** (parfois décrit en 5 couches) :

```
┌─────────────────────────────────┐
│  4. APPLICATION                 │  ← Correspond OSI 5-6-7
├─────────────────────────────────┤
│  3. TRANSPORT                   │  ← Correspond OSI 4
├─────────────────────────────────┤
│  2. INTERNET                    │  ← Correspond OSI 3
├─────────────────────────────────┤
│  1. ACCÈS RÉSEAU                │  ← Correspond OSI 1-2
└─────────────────────────────────┘
```

### Couche 1 : Accès réseau (Network Access / Link)

**Rôle :** Transmission des données sur le réseau physique local.

**Correspondance OSI :** Couches 1 (Physique) + 2 (Liaison)

**Fonctions :**
- Interfaçage avec le matériel réseau
- Formation de trames
- Adressage physique (MAC)
- Accès au support de transmission

**Protocoles :**
- Ethernet
- Wi-Fi (802.11)
- PPP
- ARP (souvent classé ici, interface entre liaison et réseau)

**Caractéristique :** Cette couche n'est pas spécifiée en détail dans TCP/IP, elle utilise les technologies existantes.

### Couche 2 : Internet (Internet / Network)

**Rôle :** **Routage** des paquets à travers les réseaux interconnectés.

**Correspondance OSI :** Couche 3 (Réseau)

**Protocole principal :** **IP (Internet Protocol)**

**Fonctions :**
- Adressage logique (adresses IP)
- Routage des paquets
- Fragmentation
- Encapsulation

**Protocoles de cette couche :**
- **IPv4** : version 4 du protocole IP
- **IPv6** : version 6 du protocole IP
- **ICMP** : messages de contrôle et d'erreur (ping, traceroute)
- **IGMP** : gestion du multicast
- **ARP** : résolution IP → MAC (parfois classé en couche 1)

**IP (Internet Protocol) :**
- Protocole **non fiable** (best effort)
- **Sans connexion**
- Pas de garantie de livraison
- La fiabilité est gérée par les couches supérieures (TCP)

### Couche 3 : Transport (Transport)

**Rôle :** Communication **de bout en bout** entre applications.

**Correspondance OSI :** Couche 4 (Transport)

**Protocoles principaux :**

**TCP (Transmission Control Protocol)**
- Fiable, orienté connexion
- Utilisé pour : Web (HTTP), Email, FTP, SSH

**UDP (User Datagram Protocol)**
- Non fiable, sans connexion
- Utilisé pour : DNS, Streaming, VoIP, DHCP

**Fonctions :**
- Multiplexage par numéros de port
- Contrôle de flux (TCP)
- Contrôle d'erreur (TCP)
- Segmentation et réassemblage

### Couche 4 : Application (Application)

**Rôle :** **Services** et **protocoles applicatifs** pour les utilisateurs.

**Correspondance OSI :** Couches 5 (Session) + 6 (Présentation) + 7 (Application)

**Caractéristique :** Regroupe tout ce qui concerne les applications et leurs protocoles.

**Protocoles courants :**
- **HTTP/HTTPS** : navigation Web
- **FTP/SFTP** : transfert de fichiers
- **SMTP/POP3/IMAP** : emails
- **DNS** : résolution de noms de domaine
- **DHCP** : configuration automatique IP
- **SSH** : connexion à distance sécurisée
- **Telnet** : connexion à distance non sécurisée
- **SNMP** : gestion réseau

**Différence avec OSI :**
- TCP/IP ne sépare pas présentation et session
- Approche plus simple et pragmatique
- Les fonctions de session et présentation sont intégrées dans les protocoles applicatifs

---

## ⚖️ Comparaison OSI vs TCP/IP {#comparaison}

### Correspondance des couches

```
OSI (7 couches)              TCP/IP (4 couches)
┌─────────────────┐          ┌─────────────────┐
│  7. Application │ ┐        │                 │
├─────────────────┤ │        │  4. Application │
│ 6. Présentation │ ├───────→│                 │
├─────────────────┤ │        │                 │
│   5. Session    │ ┘        └─────────────────┘
├─────────────────┤           ┌─────────────────┐
│  4. Transport   │ ─────────→│  3. Transport   │
├─────────────────┤           └─────────────────┘
│   3. Réseau     │ ─────────→┌─────────────────┐
├─────────────────┤           │   2. Internet   │
│ 2. Liaison      │ ┐         └─────────────────┘
├─────────────────┤ ├────────→┌─────────────────┐
│   1. Physique   │ ┘         │ 1. Accès Réseau │
└─────────────────┘           └─────────────────┘
```

### Comparaison détaillée

| Aspect                 | Modèle OSI                  | Modèle TCP/IP           |
|------------------------|-----------------------------|-------------------------|
| **Nombre de couches**  | 7                           | 4                       |
| **Type**               | Modèle théorique            | Suite de protocoles     |
| **Développement**      | ISO (1980s)                 | DARPA/DoD (1970s)       |
| **Usage**              | Référence pédagogique       | Implémentation réelle   |
| **Flexibilité**        | Rigide, bien défini         | Plus flexible           |
| **Séparation**         | Claire entre couches        | Moins stricte           |
| **Adoption**           | Référence universelle       | Standard Internet       |
| **Protocoles**         | Indépendant des protocoles  | Protocoles spécifiques  |

### Avantages du modèle OSI

✅ **Pédagogique** : structure claire pour l'enseignement  
✅ **Séparation nette** : chaque couche a un rôle bien défini  
✅ **Dépannage** : facilite l'identification des problèmes  
✅ **Universalité** : applicable à tous types de réseaux  
✅ **Standardisation** : référence pour la conception de protocoles

### Avantages du modèle TCP/IP

✅ **Pragmatique** : basé sur l'implémentation réelle  
✅ **Simplicité** : moins de couches, plus simple  
✅ **Adoption mondiale** : standard d'Internet  
✅ **Flexibilité** : adapté aux besoins réels  
✅ **Prouvé** : décennies d'utilisation réussie

### Pourquoi deux modèles ?

**Dans la pratique :**
- On utilise les **protocoles TCP/IP** (HTTP, TCP, IP, Ethernet)
- On utilise le **vocabulaire OSI** (couche 2, couche 3, etc.)
- OSI sert de **référence conceptuelle**
- TCP/IP est l'**implémentation concrète**

**Exemple concret :**
- On dit "problème de couche 2" (vocabulaire OSI)
- Mais on configure TCP/IP et Ethernet (protocoles TCP/IP)

### Modèle hybride (5 couches)

Dans l'enseignement moderne, on utilise souvent un **modèle hybride** combinant le meilleur des deux :

```
┌─────────────────┐
│  5. Application │  ← HTTP, FTP, DNS, etc.
├─────────────────┤
│  4. Transport   │  ← TCP, UDP
├─────────────────┤
│   3. Réseau     │  ← IP, ICMP
├─────────────────┤
│  2. Liaison     │  ← Ethernet, Wi-Fi
├─────────────────┤
│  1. Physique    │  ← Câbles, signaux
└─────────────────┘
```

Ce modèle est pratique car il :
- Garde la structure claire d'OSI pour les couches basses
- Simplifie les couches hautes comme TCP/IP
- Correspond à l'implémentation réelle

---

## Encapsulation et désencapsulation {#encapsulation}

### Principe de l'encapsulation

**Encapsulation** : processus d'ajout d'en-têtes (headers) à chaque couche lors de l'envoi de données.

Chaque couche :
1. Reçoit les données de la couche supérieure
2. Ajoute son propre en-tête (et parfois un trailer)
3. Transmet à la couche inférieure

**Métaphore :** Comme une poupée russe ou un envoi postal avec plusieurs enveloppes.

### Processus d'encapsulation (envoi)

```
APPLICATION         (Couche 7)       [        Données        ]

     ↓                   ↓                       ↓

PRESENTATION        (Couche 6)       [        Données        ]

     ↓                   ↓                       ↓

SESSION             (Couche 5)       [        Données        ]

     ↓                   ↓                       ↓

TRANSPORT           (Couche 4)       [En-tête TCP/UDP][Données]                         ←   SEGMENT
  
     ↓                   ↓                       ↓

RÉSEAU              (Couche 3)       [En-tête IP][En-tête TCP][Données]                 ←   PAQUET

     ↓                   ↓                       ↓

LIAISON             (Couche 2)       [En-tête Ethernet][En-tête IP][TCP][Données][FCS] ←   TRAME
   
     ↓                   ↓                       ↓

PHYSIQUE            (Couche 1)        01010101000111100011010010010001011010101...     ←    BITS

    ↓
 
Support physique
```

### Unités de données par couche

| Couche | Nom OSI             | Unité de données (PDU)  | Nom commun                                 |
|--------|---------------------|-------------------------|--------------------------------------------|
| 7-5    | Application-Session | Données                 | Données                                    |
| 4      | Transport           | TPDU                    |  **Segment** (TCP) ou **Datagramme** (UDP) |
| 3      | Réseau              | Paquet                  | **Paquet**                                 |
| 2      | Liaison             | Trame                   | **Trame** (Frame)                          |
| 1      | Physique            | -                       | **Bits**                                   |

### Détail des en-têtes

**En-tête Ethernet (Couche 2) :**
```
[MAC Destination][MAC Source][Type][Payload][FCS]
     6 octets      6 octets   2o    46-1500o  4o
```

**En-tête IP (Couche 3) :**
```
[Version][IHL][ToS][Longueur totale][ID][Flags][TTL][Protocole][Checksum]
[IP Source][IP Destination][Options][Payload]
```
- **IP Source** : adresse IP de l'émetteur (4 octets en IPv4)
- **IP Destination** : adresse IP du destinataire (4 octets)
- **TTL (Time To Live)** : nombre de sauts max (évite les boucles)
- **Protocole** : indique la couche supérieure (6=TCP, 17=UDP)

**En-tête TCP (Couche 4) :**
```
[Port Source][Port Dest][Numéro séquence][Numéro ACK][Flags]
[Checksum][Urgent Pointer][Options][Payload]
```
- **Port Source/Dest** : identification des applications (2 octets chacun)
- **Numéro de séquence** : ordre des segments
- **Flags** : SYN, ACK, FIN, RST, PSH, URG

### Désencapsulation (réception)

Processus **inverse** lors de la réception :

```
Support physique
    ↓
PHYSIQUE (Couche 1)
    ↓ Conversion bits → trame
LIAISON (Couche 2)
    ↓ Retire en-tête Ethernet, vérifie MAC
RÉSEAU (Couche 3)
    ↓ Retire en-tête IP, vérifie IP destination
TRANSPORT (Couche 4)
    ↓ Retire en-tête TCP/UDP, vérifie port
APPLICATION (Couche 7)
    ↓
[        Données        ] ← Application reçoit les données
```

À chaque couche :
1. Vérification de l'en-tête
2. Traitement approprié
3. Retrait de l'en-tête
4. Transmission à la couche supérieure

### Exemple concret : Requête HTTP

**Scénario :** Vous accédez à `http://example.com`

**Encapsulation (votre PC → serveur) :**

```
Couche 7 (Application) : Requête HTTP
    GET / HTTP/1.1
    Host: example.com
    ↓
Couche 4 (Transport) : Ajout en-tête TCP
    Port source: 52341 (aléatoire)
    Port destination: 80 (HTTP)
    ↓
Couche 3 (Réseau) : Ajout en-tête IP
    IP source: 192.168.1.100 (votre PC)
    IP destination: 93.184.216.34 (serveur)
    ↓
Couche 2 (Liaison) : Ajout en-tête Ethernet
    MAC source: AA:BB:CC:DD:EE:FF (votre PC)
    MAC destination: 11:22:33:44:55:66 (routeur)
    ↓
Couche 1 (Physique) : Bits sur le câble
```

**Désencapsulation (serveur) :**
- Couche 1 : Réception des bits
- Couche 2 : Vérification MAC destination = serveur
- Couche 3 : Vérification IP destination = serveur
- Couche 4 : Vérification port 80 = serveur HTTP
- Couche 7 : Traitement de la requête HTTP

### Importance de l'encapsulation

**Indépendance des couches :**
- Chaque couche peut évoluer indépendamment
- Exemple : passage d'Ethernet à Wi-Fi transparent pour IP

**Multiplexage :**
- Plusieurs protocoles peuvent coexister
- IP peut transporter TCP, UDP, ICMP...

**Sécurité :**
- Possibilité de chiffrer à chaque couche
- VPN : chiffrement couche 2 ou 3
- TLS : chiffrement couche 4-5

---

## Exercices d'auto-évaluation {#exercices}

### Exercice 1 : Classification des réseaux

Classez les réseaux suivants (PAN, LAN, MAN, WAN) :
1. Réseau Bluetooth entre smartphone et montre
2. Réseau d'une université avec 3 campus dans la même ville
3. Connexion entre le siège parisien et la filiale new-yorkaise
4. Réseau Wi-Fi d'un café
5. Internet

### Exercice 2 : Topologies réseau

Pour chaque situation, proposez la topologie la plus adaptée :
1. Réseau d'un datacenter critique nécessitant une très haute disponibilité
2. Réseau d'un petit bureau de 10 postes
3. Réseau d'une entreprise multi-sites avec hiérarchie

### Exercice 3 : Supports de transmission

Quel support choisir pour :
1. Connexion entre deux bâtiments distants de 500m sans interférence EM
2. Connexion bureau standard, 50m, 1 Gbps
3. Backbone entre datacenters distants de 80 km

### Exercice 4 : Modèle OSI - Attribution des couches

Pour chaque élément, indiquez la couche OSI :
1. Adresse MAC
2. Routeur
3. Protocole HTTP
4. Câble Ethernet
5. Port TCP 443
6. Adresse IP

### Exercice 5 : Protocoles et couches

Associez les protocoles aux couches OSI correctes :
- TCP, Ethernet, DNS, IP, HTTP, ICMP, FTP, ARP

### Exercice 6 : Encapsulation

Dans quel ordre les en-têtes sont-ils ajoutés lors de l'envoi d'un email ?
- En-tête IP, En-tête SMTP, En-tête TCP, En-tête Ethernet

### Exercice 7 : TCP vs UDP

Pour chaque application, indiquez si TCP ou UDP est plus approprié :
1. Téléchargement de fichier
2. Streaming vidéo en direct
3. Navigation web
4. Jeu en ligne (FPS)
5. Requête DNS

### Exercice 8 : Dépannage par couches

Un utilisateur ne peut pas accéder à Internet. Dans quel ordre testeriez-vous les couches OSI ?

### Exercice 9 : Adresse MAC

1. Trouver l’adresse (ou les) MAC de votre PC  selon votre système d’exploitation
>> Tips: Windows (ipconfig /all) Linux/macOS (ifconfig) ou (ip link show)

2. Séparez les trois premiers octets (OUI) et les trois derniers (NIC).
3. Recherchez le fabricant associé à votre OUI sur ce site : https://macvendors.com

### Exercice 10 : Compléments 

1. À quel niveau du modèle OSI agit l’adresse MAC ?
2. Que se passe-t-il si deux machines ont la même adresse MAC ?
3. Peut-on modifier une adresse MAC ? Si oui, pourquoi le ferait-on ?
4. Quelle est la différence entre adresse MAC et adresse IP ?


---

## 📚 Ressources complémentaires {#ressources}

### Livres recommandés

1. **Pujolle, Guy** - *Les Réseaux - Édition 2024-2026* (Eyrolles)
   - Référence française complète et actualisée

2. **Dordoigne, José** - *Réseaux informatiques - Notions fondamentales* (ENI)
   - Approche pédagogique claire pour débutants

3. **Kurose & Ross** - *Computer Networking: A Top-Down Approach* (Pearson)
   - Référence internationale, approche top-down

### Ressources en ligne

**Cours et tutoriels :**
- Cisco Networking Academy (netacad.com)
- Cours en ligne sur Coursera, edX
- YouTube : chaînes spécialisées réseaux

**Standards et RFC :**
- RFC Editor (rfc-editor.org)
- IEEE Standards (standards.ieee.org)

**Outils pratiques :**
- Packet Tracer : simulateur réseau Cisco
- Wireshark : analyseur de protocoles
- GNS3 : émulateur réseau

### Pour aller plus loin

**Après ce cours :**
- Approfondissement des protocoles (TCP/IP détaillé)
- Sécurité des réseaux
- Administration réseau avancée
- Réseaux sans fil (Wi-Fi, 5G)
- Cloud et virtualisation réseau

**Certifications :**
- CompTIA Network+
- Cisco CCNA
- Juniper JNCIA

---

## 📝 Notes importantes

### À retenir absolument

✅ **7 couches OSI** : Physique, Liaison, Réseau, Transport, Session, Présentation, Application

✅ **4 couches TCP/IP** : Accès Réseau, Internet, Transport, Application

✅ **Unités de données** : Bit → Trame → Paquet → Segment → Données

✅ **Équipements clés** :
- Switch (couche 2)
- Routeur (couche 3)

✅ **Protocoles essentiels** :
- Couche 2 : Ethernet
- Couche 3 : IP, ICMP
- Couche 4 : TCP (fiable), UDP (rapide)
- Couche 7 : HTTP, DNS, FTP

✅ **Encapsulation** : Ajout d'en-têtes couche par couche (émission)

✅ **Désencapsulation** : Retrait d'en-têtes couche par couche (réception)

---

## Correction des exercices d'auto-évaluation {#corrige_exercices}

### Exercice 1 : Classification des réseaux

1. PAN (courte portée, personnel)
2. MAN (échelle métropolitaine)
3. WAN (intercontinental)
4. LAN (local, un seul site)
5. WAN (mondial)

### Exercice 2 : Topologies réseau

1. Maillée (redondance maximale)
2. Étoile (simple, économique)
3. Hybride/Hiérarchique (flexibilité)

### Exercice 3 : Supports de transmission

1. Fibre multimode (distance, immunité EM)
2. Câble Cat 6 (coût, suffisant)
3. Fibre monomode (longue distance, haut débit)

### Exercice 4 : Modèle OSI - Attribution des couches

1. Couche 2 (Liaison)
2. Couche 3 (Réseau)
3. Couche 7 (Application)
4. Couche 1 (Physique)
5. Couche 4 (Transport)
6. Couche 3 (Réseau)

### Exercice 5 : Protocoles et couches

- Couche 2 : Ethernet, ARP
- Couche 3 : IP, ICMP
- Couche 4 : TCP
- Couche 7 : DNS, HTTP, FTP

### Exercice 6 : Encapsulation

En-tête SMTP (C7) → TCP (C4) → IP (C3) → Ethernet (C2)

### Exercice 7 : TCP vs UDP

1. TCP (fiabilité cruciale)
2. UDP (temps réel prioritaire)
3. TCP (intégrité des pages)
4. UDP (faible latence)
5. UDP (requête simple et rapide)

### Exercice 8 : Dépannage par couches

1. **Couche 1** : Câble branché ? LED de la carte réseau ?
2. **Couche 2** : Adresse MAC visible ? Switch fonctionne ?
3. **Couche 3** : Adresse IP configurée ? Ping de la passerelle ?
4. **Couche 4** : Ports ouverts ? Firewall ?
5. **Couche 7** : DNS fonctionne ? Navigateur correct ?

### Exercice 9 : Adresse MAC

1. Trouver l’adresse MAC
Exemples de sortie :

Windows :
```
Carte réseau sans fil Wi-Fi :
   Adresse physique. . . . . . . . . : 78-1A-04-5F-9D-3B
```

Linux :
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 08:00:27:6B:2A:9F  txqueuelen 1000  (Ethernet)
```

Adresse MAC trouvée : 78-1A-04-5F-9D-3B (exemple)

2. Analyse de la structure

| Partie                                       | Octets   | Signification                             | Exemple    |
| -------------------------------------------- | -------- | ----------------------------------------- | ---------- |
| **OUI (Organizationally Unique Identifier)** | 3 octets | Identifie le constructeur                 | `78-1A-04` |
| **NIC (Network Interface Controller)**       | 3 octets | Identifie la carte unique du constructeur | `5F-9D-3B` |

3. Fabricant
Vérification sur macvendors.com :
OUI 78:1A:04 → Dell Inc.
Conclusion : Cette carte réseau a été fabriquée par Dell.

### Exercice 10 : Compléments 

| Question                                                            | Réponse attendue                                                                                                                                                                                     |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. À quel niveau du modèle OSI agit l’adresse MAC ?**             | Couche **Liaison de données (couche 2)**                                                                                                                                                             |
| **2. Que se passe-t-il si deux machines ont la même adresse MAC ?** | Conflit d’adressage : les trames risquent d’être perdues ou mal dirigées. Le switch ne sait plus sur quel port envoyer.                                                                              |
| **3. Peut-on modifier une adresse MAC ? Si oui, pourquoi ?**        | Oui, via une commande système (ex. `macchanger` sous Linux). Souvent fait pour :<br>• contourner un filtrage MAC<br>• préserver la vie privée<br>• tester la sécurité d’un réseau                    |
| **4. Quelle est la différence entre adresse MAC et adresse IP ?**   | • MAC = identifiant **physique**, local, fixe (couche 2)<br>• IP = identifiant **logique**, routable, modifiable (couche 3)<br>Les deux sont nécessaires pour transmettre des données sur un réseau. |

------

## 🔄 Prochaine session

**CM2 : Adressage IP et Subnetting**
- Structure des adresses IPv4
- Classes d'adresses
- Masques de sous-réseau
- Introduction à IPv6
- Calculs de subnetting

---

*Document rédigé pour le module TI305 - Architecture Réseaux*  
*Dernière mise à jour : Octobre 2025*
