# Retour au menu
- [Menu README](../README.md)
  
---
# CM2 - Adressage IP et Subnetting

---
## Table des matières

1. [Objectifs d'apprentissage](#objectifs)
2. [Rappels essentiels](#rappels)
3. [Introduction à l'adressage IP](#introduction)
4. [Structure d'une adresse IPv4](#structure-ipv4)
5. [Classes d'adresses IPv4](#classes)
6. [Adresses spéciales et réservées](#adresses-speciales)
7. [Adresses privées vs publiques](#prive-public)
8. [Masques de sous-réseau](#masques)
9. [Subnetting - Découpage en sous-réseaux](#subnetting)
10. [CIDR et notation slash](#cidr)
11. [VLSM - Masques à longueur variable](#vlsm)
12. [Introduction à IPv6](#ipv6)
13. [Exercices pratiques](#exercices)
14. [Ressources complémentaires](#ressources)

---

## Objectifs d'apprentissage {#objectifs}

À l'issue de ce cours, vous serez capable de :

- **Comprendre** la structure et le format des adresses IPv4
- **Identifier** les différentes classes d'adresses IP
- **Distinguer** adresses privées et publiques
- **Maîtriser** les masques de sous-réseau et leur notation
- **Calculer** des sous-réseaux (subnetting)
- **Utiliser** la notation CIDR
- **Appliquer** le VLSM pour optimiser l'adressage
- **Connaître** les bases d'IPv6 et comprendre la transition IPv4/IPv6

---

## Rappels essentiels {#rappels}

### Révision CM1

**Modèle OSI - Couche 3 (Réseau) :**
- Responsable du routage entre réseaux
- Utilise l'adressage logique (IP)
- Équipement principal : Routeur

**Différence MAC vs IP :**
- **Adresse MAC (Couche 2)** : physique, inscrite dans la carte réseau, locale
  - Format : `AA:BB:CC:DD:EE:FF`
  - Portée : réseau local uniquement
  
- **Adresse IP (Couche 3)** : logique, configurable, routage entre réseaux
  - Format IPv4 : `192.168.1.10`
  - Portée : mondiale (Internet)

**Protocole IP :**
- Internet Protocol
- Sans connexion (connectionless)
- Non fiable (best effort)
- La fiabilité est assurée par TCP (couche 4)

---

## Introduction à l'adressage IP {#introduction}

### Pourquoi des adresses IP ?

Les adresses IP permettent :

**Identification unique :**
- Chaque équipement sur un réseau IP doit avoir une adresse unique
- Évite les conflits et ambiguïtés

**Routage :**
- Les routeurs utilisent les adresses IP pour acheminer les paquets
- Structure hiérarchique permettant l'agrégation de routes

**Localisation logique :**
- Organisation en réseaux et sous-réseaux
- Regroupement géographique ou fonctionnel

### Deux versions d'IP

**IPv4 (Internet Protocol version 4)**
- Développé dans les années 1970-80
- Adresses sur 32 bits
- ≈ 4,3 milliards d'adresses possibles
- **Épuisement** : quasi-complet depuis 2011
- Encore majoritaire aujourd'hui

**IPv6 (Internet Protocol version 6)**
- Développé dans les années 1990
- Adresses sur 128 bits
- ≈ 3,4 × 10³⁸ adresses possibles
- Solution à l'épuisement d'IPv4
- Adoption progressive

**Ce cours se concentre principalement sur IPv4** (encore dominant), avec introduction à IPv6.

---

## Structure d'une adresse IPv4 {#structure-ipv4}

### Format binaire et décimal

Une adresse IPv4 est composée de **32 bits** organisés en **4 octets** (4 × 8 bits).

**Représentation binaire :**
```
11000000.10101000.00000001.00001010
```

**Représentation décimale pointée (dotted decimal) :**
```
192.168.1.10
```

Chaque octet peut avoir une valeur de **0 à 255** (2⁸ = 256 valeurs).

### Conversion binaire ↔ décimal

**Tableau de conversion (1 octet = 8 bits) :**

| Position bit | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|--------------|---|---|---|---|---|---|---|---|
| **Valeur décimale** | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

**Exemple 1 : Binaire → Décimal**

Octet : `11000000`
```
1×128 + 1×64 + 0×32 + 0×16 + 0×8 + 0×4 + 0×2 + 0×1
= 128 + 64 = 192
```

**Exemple 2 : Décimal → Binaire**

Nombre : 168
```
168 = 128 + 32 + 8
    = 10101000 en binaire
```

**Pratique :** Adresse IP `192.168.1.10`
```
192      = 11000000
168      = 10101000
1        = 00000001
10       = 00001010

Complet : 11000000.10101000.00000001.00001010
```

### Structure : Partie réseau + Partie hôte

Une adresse IP se compose de **deux parties** :

```
[  Partie RÉSEAU  ][  Partie HÔTE  ]
```

**Partie réseau (Network ID) :**
- Identifie le réseau auquel appartient l'équipement
- Tous les équipements du même réseau partagent cette partie
- Utilisée par les routeurs pour acheminer les paquets

**Partie hôte (Host ID) :**
- Identifie l'équipement spécifique sur ce réseau
- Unique au sein du réseau

**Exemple :**
```
Adresse : 192.168.1.10
Masque  : 255.255.255.0

Partie réseau : 192.168.1     (premiers 24 bits)
Partie hôte   : 10            (derniers 8 bits)
```

Le **masque de sous-réseau** détermine où se situe la séparation.

---

## Classes d'adresses IPv4 {#classes}

### Système de classes (Classful Addressing)

Historiquement, les adresses IPv4 étaient divisées en **classes** (A, B, C, D, E) selon les premiers bits.

**Note :** Le système de classes est **obsolète** depuis 1993 (remplacé par CIDR), mais reste utile pour comprendre la structure des adresses.

### Classe A

**Premier bit : 0**

**Plage d'adresses :** `0.0.0.0` à `127.255.255.255`

**Premier octet :** 1 à 126 (0 et 127 réservés)

**Structure :**
```
0 [  Réseau (7 bits)  ][ Hôte (24 bits) ]
```

**Masque par défaut :** `255.0.0.0` ou `/8`

**Caractéristiques :**
- **Réseaux possibles :** 2⁷ = 128 (mais 126 utilisables)
- **Hôtes par réseau :** 2²⁴ - 2 = 16 777 214
- **Usage :** Très grands réseaux (multinationales, ISP)

**Exemples :**
- `10.0.0.0/8` - Réseau privé
- `44.0.0.0/8` - Cable & Wireless

### Classe B

**Premiers bits : 10**

**Plage d'adresses :** `128.0.0.0` à `191.255.255.255`

**Premier octet :** 128 à 191

**Structure :**
```
10 [ Réseau (14 bits) ][ Hôte (16 bits) ]
```

**Masque par défaut :** `255.255.0.0` ou `/16`

**Caractéristiques :**
- **Réseaux possibles :** 2¹⁴ = 16 384
- **Hôtes par réseau :** 2¹⁶ - 2 = 65 534
- **Usage :** Moyennes/grandes organisations

**Exemples :**
- `172.16.0.0/16` - Réseau privé
- `128.10.0.0/16` - Université

### Classe C

**Premiers bits : 110**

**Plage d'adresses :** `192.0.0.0` à `223.255.255.255`

**Premier octet :** 192 à 223

**Structure :**
```
110 [ Réseau (21 bits) ][ Hôte (8 bits) ]
```

**Masque par défaut :** `255.255.255.0` ou `/24`

**Caractéristiques :**
- **Réseaux possibles :** 2²¹ = 2 097 152
- **Hôtes par réseau :** 2⁸ - 2 = 254
- **Usage :** Petites organisations, réseaux locaux

**Exemples :**
- `192.168.1.0/24` - Réseau privé (très courant)
- `200.10.50.0/24` - Petit réseau public

### Classe D (Multicast)

**Premiers bits : 1110**

**Plage d'adresses :** `224.0.0.0` à `239.255.255.255`

**Premier octet :** 224 à 239

**Usage :** Adresses de **multicast** (diffusion vers un groupe)

**Exemples :**
- `224.0.0.1` - Tous les systèmes sur le sous-réseau
- `224.0.0.2` - Tous les routeurs
- `239.255.255.250` - SSDP (UPnP)

**Note :** Pas de notion de réseau/hôte, pas attribuées aux équipements individuels.

### Classe E (Réservée)

**Premiers bits : 1111**

**Plage d'adresses :** `240.0.0.0` à `255.255.255.255`

**Premier octet :** 240 à 255

**Usage :** **Réservée** pour expérimentation et recherche

**Note :** Non utilisable dans les réseaux de production.

### Tableau récapitulatif des classes

| Classe | Premier(s) bit(s) | Plage | Masque défaut | Réseaux | Hôtes/réseau | Usage |
|--------|-------------------|-------|---------------|---------|--------------|-------|
| **A** | 0 | 1-126 | /8 | 126 | 16M | Très grands |
| **B** | 10 | 128-191 | /16 | 16K | 65K | Moyens |
| **C** | 110 | 192-223 | /24 | 2M | 254 | Petits |
| **D** | 1110 | 224-239 | - | - | - | Multicast |
| **E** | 1111 | 240-255 | - | - | - | Réservé |

### Identification rapide de la classe

**Par le premier octet :**
- 1-126 → Classe A
- 128-191 → Classe B
- 192-223 → Classe C
- 224-239 → Classe D
- 240-255 → Classe E

---

## Adresses spéciales et réservées {#adresses-speciales}

### Adresse réseau (Network Address)

**Définition :** Première adresse d'un réseau, tous les bits hôtes à 0.

**Rôle :** Identifie le réseau lui-même, non attribuable à un équipement.

**Exemple :**
```
Réseau : 192.168.1.0/24
Adresse réseau : 192.168.1.0
```

### Adresse de broadcast (Diffusion)

**Définition :** Dernière adresse d'un réseau, tous les bits hôtes à 1.

**Rôle :** Diffusion vers tous les équipements du réseau.

**Exemple :**
```
Réseau : 192.168.1.0/24
Adresse broadcast : 192.168.1.255
```

**Usage :** DHCP, ARP, découverte de services.

### Adresse de bouclage (Loopback)

**Plage :** `127.0.0.0/8` (tout le réseau 127.x.x.x)

**Adresse standard :** `127.0.0.1` (localhost)

**Rôle :** Interface virtuelle interne, test local.

**Usage :**
```bash
ping 127.0.0.1    # Teste la pile TCP/IP locale
```

### Adresse 0.0.0.0

**Significations selon le contexte :**

**Route par défaut :**
- Destination : `0.0.0.0/0` = tout le trafic
- "Attrape-tout" pour le routage

**Écoute sur toutes interfaces :**
- Serveur écoute sur `0.0.0.0` = toutes les IP de la machine

**Adresse non configurée :**
- Hôte DHCP avant obtention d'IP

### Adresse 255.255.255.255

**Broadcast limité (limited broadcast)**

**Rôle :** Diffusion sur le réseau local uniquement, non routé.

**Usage :** Requêtes DHCP initiales.

### Tableau des adresses spéciales

| Adresse/Plage | Nom | Usage |
|---------------|-----|-------|
| `0.0.0.0` | Route par défaut | Routage |
| `0.0.0.0/8` | Réseau actuel | Adressage local |
| `10.0.0.0/8` | Privé Classe A | Réseaux privés |
| `127.0.0.0/8` | Loopback | Tests locaux |
| `169.254.0.0/16` | APIPA | Auto-configuration |
| `172.16.0.0/12` | Privé Classe B | Réseaux privés |
| `192.168.0.0/16` | Privé Classe C | Réseaux privés |
| `224.0.0.0/4` | Multicast | Diffusion groupe |
| `255.255.255.255` | Broadcast limité | Diffusion locale |

---

## Adresses privées vs publiques {#prive-public}

### Adresses publiques (routables)

**Définition :** Adresses **uniques mondialement**, routables sur Internet.

**Attribution :** Gérées par les RIR (Regional Internet Registries) et ISP.

**Caractéristiques :**
- ✅ Accessibles depuis Internet
- ✅ Routées globalement
- ❌ Ressource limitée (épuisement)
- ❌ Coût (location auprès des ISP)

**Exemple :**
```
8.8.8.8           - DNS Google
142.250.185.46    - google.com
```

### Adresses privées (non routables)

**Définition :** Adresses réservées pour les **réseaux privés**, non routables sur Internet.

**Standard :** RFC 1918 (1996)

**Plages réservées :**

**Classe A privée :**
```
10.0.0.0 à 10.255.255.255
10.0.0.0/8
→ 1 réseau de classe A (16 millions d'hôtes)
```

**Classe B privée :**
```
172.16.0.0 à 172.31.255.255
172.16.0.0/12
→ 16 réseaux de classe B (65K hôtes chacun)
```

**Classe C privée :**
```
192.168.0.0 à 192.168.255.255
192.168.0.0/16
→ 256 réseaux de classe C (254 hôtes chacun)
```

**Caractéristiques :**
- ✅ Gratuites, librement utilisables
- ✅ Réutilisables dans différentes organisations
- ✅ Économise les adresses publiques
- ❌ Non accessibles directement depuis Internet
- ❌ Nécessite NAT pour accès Internet

### NAT (Network Address Translation)

**Problème :** Les adresses privées ne sont pas routables sur Internet.

**Solution :** NAT traduit les adresses privées en adresses publiques.

**Fonctionnement :**
```
Réseau interne (privé)         Internet (public)
192.168.1.10 ──────► [Routeur NAT] ──────► 203.0.113.5
192.168.1.11 ──────►  (Traduction) ──────► 203.0.113.5
192.168.1.12 ──────►                ──────► 203.0.113.5
```

**Types de NAT :**
- **SNAT (Source NAT)** : Change l'IP source (sortie Internet)
- **DNAT (Destination NAT)** : Change l'IP destination (redirection de ports)
- **PAT (Port Address Translation)** : NAT + ports (le plus courant)

**Avantages :**
- Économise les adresses IP publiques
- Sécurité (masquage des adresses internes)
- Flexibilité de l'adressage interne

**Inconvénients :**
- Complexité de configuration
- Problèmes avec certains protocoles (FTP, VoIP)
- Pas de connexion entrante directe

### APIPA (Automatic Private IP Addressing)

**Plage :** `169.254.0.0/16` (169.254.1.0 à 169.254.254.255)

**Rôle :** Auto-configuration automatique en l'absence de DHCP.

**Fonctionnement :**
1. Client demande une IP via DHCP
2. Aucune réponse du serveur DHCP
3. Client s'attribue automatiquement une IP APIPA
4. Permet communication locale uniquement (pas de routage)

**Diagnostic :**
```bash
# Windows
ipconfig
# Si IP en 169.254.x.x → Problème DHCP !

# Linux
ip addr
# Si IP en 169.254.x.x → Problème réseau
```

---

## Masques de sous-réseau {#masques}

### Rôle du masque de sous-réseau

Le **masque de sous-réseau (subnet mask)** détermine :
- Quelle partie de l'adresse IP est le **réseau**
- Quelle partie est l'**hôte**

**Analogie :** Comme un pochoir qui sépare réseau et hôte.

### Format du masque

**Représentation décimale :**
```
255.255.255.0
```

**Représentation binaire :**
```
11111111.11111111.11111111.00000000
```

**Règle :** Suite de 1 contigus suivie de 0 contigus
- **1** = partie réseau
- **0** = partie hôte

### Opération AND logique

**Pour déterminer le réseau :** Appliquer un **ET logique (AND)** entre l'IP et le masque.

**Exemple :**
```
Adresse IP  : 192.168.1.10    = 1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 1 0 1 0
                AND logique
Masque      : 255.255.255.0   = 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1 . 0 0 0 0 0 0 0 0
Réseau      : 192.168.1.0     = 1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 0 0 0 0
```

**Règle AND :**
- 1 AND 1 = 1
- 1 AND 0 = 0
- 0 AND 1 = 0
- 0 AND 0 = 0

### Masques courants

| Masque décimal | Masque binaire | CIDR | Bits réseau | Bits hôte | Hôtes |
|----------------|----------------|------|-------------|-----------|-------|
| 255.0.0.0 | /8 | 11111111.00000000... | 8 | 24 | 16 777 214 |
| 255.255.0.0 | /16 | 11111111.11111111.00000000... | 16 | 16 | 65 534 |
| 255.255.255.0 | /24 | 11111111.11111111.11111111.00000000 | 24 | 8 | 254 |
| 255.255.255.128 | /25 | ...11111111.10000000 | 25 | 7 | 126 |
| 255.255.255.192 | /26 | ...11111111.11000000 | 26 | 6 | 62 |
| 255.255.255.224 | /27 | ...11111111.11100000 | 27 | 5 | 30 |
| 255.255.255.240 | /28 | ...11111111.11110000 | 28 | 4 | 14 |
| 255.255.255.252 | /30 | ...11111111.11111100 | 30 | 2 | 2 |

### Calcul du nombre d'hôtes

**Formule :** Nombre d'hôtes utilisables = 2^n - 2

Où **n** = nombre de bits hôte

**Le "-2" s'explique par :**
- Adresse réseau (tous les bits hôtes à 0)
- Adresse broadcast (tous les bits hôtes à 1)

**Exemples :**

**/24 (255.255.255.0) :**
- 8 bits hôte → 2⁸ - 2 = 256 - 2 = **254 hôtes**

**/30 (255.255.255.252) :**
- 2 bits hôte → 2² - 2 = 4 - 2 = **2 hôtes**
- Usage : liaison point-à-point entre routeurs

### Exemple complet

**Configuration :**
```
Adresse IP : 172.16.50.100
Masque     : 255.255.255.0 (/24)
```

**Calculs :**

**Adresse réseau :**
```
172.16.50.100 AND 255.255.255.0 = 172.16.50.0
```

**Adresse broadcast :**
```
Dernier octet : tous les bits hôte à 1
= 172.16.50.255
```

**Plage d'hôtes utilisables :**
```
Première IP : 172.16.50.1
Dernière IP : 172.16.50.254
Nombre      : 254 hôtes
```

**Passerelle par défaut (conventionnelle) :**
```
Souvent : 172.16.50.1 ou 172.16.50.254
```

---

## Subnetting - Découpage en sous-réseaux {#subnetting}

### Pourquoi le subnetting ?

**Problèmes sans subnetting :**
- Gaspillage d'adresses
- Broadcast trop étendu (performance)
- Difficulté de gestion
- Sécurité réduite

**Avantages du subnetting :**
- ✅ Optimisation de l'utilisation des adresses
- ✅ Réduction du domaine de broadcast
- ✅ Organisation logique du réseau
- ✅ Amélioration de la sécurité (segmentation)
- ✅ Facilité de gestion

### Principe du subnetting

**Idée :** "Emprunter" des bits de la partie hôte pour créer des sous-réseaux.

**Exemple visuel :**
```
Avant subnetting (Classe C) :
[  Réseau (24 bits)  ][ Hôte (8 bits) ]
192.168.1             .0-255           → 1 réseau, 254 hôtes

Après subnetting (/26) :
[  Réseau (24 bits)  ][SR(2)][Hôte(6)]
192.168.1             .00    .000000   → 4 sous-réseaux, 62 hôtes chacun
```

### Méthodologie de calcul

**Étapes du subnetting :**

1. **Identifier le besoin**
   - Nombre de sous-réseaux nécessaires ?
   - Nombre d'hôtes par sous-réseau ?

2. **Calculer les bits à emprunter**
   - Pour N sous-réseaux : 2^n ≥ N
   - Pour M hôtes : 2^h - 2 ≥ M

3. **Déterminer le nouveau masque**
   - Ajouter les bits empruntés au masque d'origine

4. **Calculer les plages de sous-réseaux**
   - Adresse réseau de chaque sous-réseau
   - Première IP utilisable
   - Dernière IP utilisable
   - Adresse broadcast

### Exemple 1 : Subnetting simple

**Contexte :**
- Réseau de départ : `192.168.1.0/24`
- Besoin : 4 sous-réseaux
- Hôtes par sous-réseau : environ 50

**Étape 1 : Bits à emprunter**
```
Pour 4 sous-réseaux : 2^2 = 4 ✓
Emprunter 2 bits
```

**Étape 2 : Nouveau masque**
```
Original : /24 (255.255.255.0)
+ 2 bits : /26 (255.255.255.192)
```

**Étape 3 : Calcul des paramètres**
```
Bits hôte restants : 8 - 2 = 6
Hôtes par sous-réseau : 2^6 - 2 = 62 ✓
Incrément : 2^6 = 64
```

**Étape 4 : Les 4 sous-réseaux**

**Sous-réseau 1 :**
```
Réseau     : 192.168.1.0/26
Première IP: 192.168.1.1
Dernière IP: 192.168.1.62
Broadcast  : 192.168.1.63
```

**Sous-réseau 2 :**
```
Réseau     : 192.168.1.64/26
Première IP: 192.168.1.65
Dernière IP: 192.168.1.126
Broadcast  : 192.168.1.127
```

**Sous-réseau 3 :**
```
Réseau     : 192.168.1.128/26
Première IP: 192.168.1.129
Dernière IP: 192.168.1.190
Broadcast  : 192.168.1.191
```

**Sous-réseau 4 :**
```
Réseau     : 192.168.1.192/26
Première IP: 192.168.1.193
Dernière IP: 192.168.1.254
Broadcast  : 192.168.1.255
```

### Exemple 2 : Plus de sous-réseaux

**Contexte :**
- Réseau : `10.10.0.0/16`
- Besoin : 200 sous-réseaux
- Hôtes par sous-réseau : 100

**Étape 1 : Bits à emprunter**
```
Pour 200 sous-réseaux :
2^7 = 128 (insuffisant)
2^8 = 256 ✓
Emprunter 8 bits
```

**Étape 2 : Nouveau masque**
```
Original : /16
+ 8 bits : /24 (255.255.255.0)
```

**Étape 3 : Vérification hôtes**
```
Bits hôte : 32 - 24 = 8
Hôtes : 2^8 - 2 = 254 ✓ (suffisant pour 100)
```

**Étape 4 : Exemples de sous-réseaux**
```
10.10.0.0/24    (hôtes : .1 à .254)
10.10.1.0/24    (hôtes : .1 à .254)
10.10.2.0/24    (hôtes : .1 à .254)
...
10.10.255.0/24  (hôtes : .1 à .254)
```

Total : 256 sous-réseaux de 254 hôtes chacun

### Table de subnetting rapide

| CIDR | Masque | Sous-réseaux | Hôtes | Usage typique |
|------|--------|--------------|-------|---------------|
| /24 | 255.255.255.0 | 1 | 254 | Petit réseau |
| /25 | 255.255.255.128 | 2 | 126 | 2 départements |
| /26 | 255.255.255.192 | 4 | 62 | 4 départements |
| /27 | 255.255.255.224 | 8 | 30 | Petits groupes |
| /28 | 255.255.255.240 | 16 | 14 | Très petits groupes |
| /29 | 255.255.255.248 | 32 | 6 | Mini-réseaux |
| /30 | 255.255.255.252 | 64 | 2 | Liaison point-à-point |

---

## CIDR et notation slash {#cidr}

### Qu'est-ce que CIDR ?

**CIDR (Classless Inter-Domain Routing)**
- Introduit en 1993 (RFC 1519)
- Remplace le système de classes
- Notation plus flexible : `/n`

**Principe :** Spécifier directement le nombre de bits réseau.

### Notation CIDR

**Format :** `adresse_IP/nombre_de_bits_réseau`

**Exemples :**
```
192.168.1.0/24      → Masque 255.255.255.0 (24 bits réseau)
10.0.0.0/8          → Masque 255.0.0.0 (8 bits réseau)
172.16.50.32/27     → Masque 255.255.255.224 (27 bits réseau)
```

### Conversion CIDR ↔ Masque décimal

**CIDR → Masque :**

**Méthode :**
1. Écrire n bits à 1 suivis de (32-n) bits à 0
2. Convertir chaque octet en décimal

**Exemple : /26**
```
26 bits à 1 + 6 bits à 0
11111111.11111111.11111111.11000000
255     .255     .255     .192
```

**Masque → CIDR :**

**Méthode :** Compter le nombre de bits à 1

**Exemple : 255.255.240.0**
```
11111111.11111111.11110000.00000000
8 + 8 + 4 + 0 = 20 bits
= /20
```

### Tableau de correspondance

| CIDR | Masque décimal | Binaire dernier octet | Hôtes |
|------|----------------|----------------------|-------|
| /24 | 255.255.255.0 | 00000000 | 254 |
| /25 | 255.255.255.128 | 10000000 | 126 |
| /26 | 255.255.255.192 | 11000000 | 62 |
| /27 | 255.255.255.224 | 11100000 | 30 |
| /28 | 255.255.255.240 | 11110000 | 14 |
| /29 | 255.255.255.248 | 11111000 | 6 |
| /30 | 255.255.255.252 | 11111100 | 2 |
| /31 | 255.255.255.254 | 11111110 | 0* |
| /32 | 255.255.255.255 | 11111111 | 1 |

**/31** : usage spécial pour liaisons point-à-point (RFC 3021)  
**/32** : hôte unique (route spécifique)

### Agrégation de routes (Route Summarization)

**Principe :** Regrouper plusieurs réseaux en une seule route.

**Avantage :** Réduction de la taille des tables de routage.

**Exemple :**

**Réseaux individuels :**
```
192.168.0.0/24
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24
```

**Route agrégée :**
```
192.168.0.0/22
```

**Vérification :**
- /22 = 22 bits réseau, 10 bits hôte
- 2^10 = 1024 adresses
- Équivalent à 4 réseaux /24 (4 × 256 = 1024) ✓

---

## VLSM - Masques à longueur variable {#vlsm}

### Qu'est-ce que VLSM ?

**VLSM (Variable Length Subnet Mask)**
- Extension du subnetting
- Permet d'utiliser **différents masques** dans un même réseau principal
- Optimisation maximale de l'adressage

**Différence avec subnetting classique :**
- Subnetting : tous les sous-réseaux ont la même taille
- VLSM : sous-réseaux de tailles différentes selon les besoins

### Pourquoi VLSM ?

**Problème :**
```
Réseau : 192.168.1.0/24
Département A : 100 hôtes
Département B : 50 hôtes
Département C : 10 hôtes
Liaison routeur : 2 hôtes
```

**Avec subnetting classique (/25) :**
- 2 sous-réseaux de 126 hôtes
- Gaspillage pour départements B, C et liaison

**Avec VLSM :**
- Adapter la taille à chaque besoin
- Optimisation maximale

### Méthodologie VLSM

**Étapes :**

1. **Lister les besoins par ordre décroissant**
2. **Allouer du plus grand au plus petit**
3. **Calculer chaque sous-réseau individuellement**
4. **Vérifier qu'il n'y a pas de chevauchement**

### Exemple complet VLSM

**Contexte :**
- Réseau de base : `192.168.10.0/24`
- LAN A : 100 hôtes
- LAN B : 50 hôtes
- LAN C : 25 hôtes
- Liaison routeurs : 2 hôtes

**Étape 1 : Ordre décroissant**
```
1. LAN A : 100 hôtes
2. LAN B : 50 hôtes
3. LAN C : 25 hôtes
4. Liaison : 2 hôtes
```

**Étape 2 : Calcul des masques nécessaires**

**LAN A (100 hôtes) :**
```
2^7 - 2 = 126 hôtes ✓
Masque : /25 (128 adresses)
```

**LAN B (50 hôtes) :**
```
2^6 - 2 = 62 hôtes ✓
Masque : /26 (64 adresses)
```

**LAN C (25 hôtes) :**
```
2^5 - 2 = 30 hôtes ✓
Masque : /27 (32 adresses)
```

**Liaison (2 hôtes) :**
```
2^2 - 2 = 2 hôtes ✓
Masque : /30 (4 adresses)
```

**Étape 3 : Allocation des sous-réseaux**

**LAN A :**
```
Réseau     : 192.168.10.0/25
Plage      : 192.168.10.1 - 192.168.10.126
Broadcast  : 192.168.10.127
Adresses   : 128 (0-127)
```

**LAN B :**
```
Réseau     : 192.168.10.128/26
Plage      : 192.168.10.129 - 192.168.10.190
Broadcast  : 192.168.10.191
Adresses   : 64 (128-191)
```

**LAN C :**
```
Réseau     : 192.168.10.192/27
Plage      : 192.168.10.193 - 192.168.10.222
Broadcast  : 192.168.10.223
Adresses   : 32 (192-223)
```

**Liaison :**
```
Réseau     : 192.168.10.224/30
Plage      : 192.168.10.225 - 192.168.10.226
Broadcast  : 192.168.10.227
Adresses   : 4 (224-227)
```

**Étape 4 : Vérification**
```
Total utilisé : 128 + 64 + 32 + 4 = 228 adresses
Disponibles   : 256 adresses
Restant       : 28 adresses (pour évolution)
✓ Pas de chevauchement
```

### Avantages de VLSM

✅ **Optimisation maximale** des adresses  
✅ **Flexibilité** dans la conception réseau  
✅ **Évolutivité** plus facile  
✅ **Économie** d'espace d'adressage

### Prérequis pour VLSM

⚠️ **Protocoles de routage compatibles :**
- ✅ RIPv2, OSPF, EIGRP, BGP
- ❌ RIPv1 (ne supporte pas VLSM)

Les protocoles doivent pouvoir **transporter le masque** dans les mises à jour de routage.

---

## Introduction à IPv6 {#ipv6}

### Pourquoi IPv6 ?

**Problèmes d'IPv4 :**
- **Épuisement des adresses** : ~4,3 milliards d'adresses, insuffisant
  - Dernier bloc IANA alloué : 2011
  - Pénurie dans certaines régions
- Dépendance au NAT (complexité)
- Limitations techniques (fragmentation, sécurité)

**IPv6 résout ces problèmes :**
- ✅ Espace d'adressage quasi-illimité
- ✅ Simplification (pas de NAT nécessaire)
- ✅ Sécurité intégrée (IPsec obligatoire)
- ✅ Configuration automatique améliorée
- ✅ QoS native

### Caractéristiques d'IPv6

**Taille des adresses :** 128 bits (vs 32 bits en IPv4)

**Nombre d'adresses :**
```
2^128 ≈ 3,4 × 10^38 adresses
= 340 undécillions d'adresses
≈ 670 millions de milliards d'adresses par mm² de surface terrestre !
```

**Format :** 8 groupes de 4 chiffres hexadécimaux séparés par `:`

**Exemple :**
```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

### Notation et simplification

**Règles d'écriture :**

**1. Suppression des zéros initiaux**
```
Complet    : 2001:0db8:0000:0042:0000:8a2e:0370:7334
Simplifié  : 2001:db8:0:42:0:8a2e:370:7334
```

**2. Compression des zéros consécutifs (::)**

Remplacer **un seul** groupe de zéros consécutifs par `::`

```
Avant : 2001:0db8:0000:0000:0000:0000:0000:0001
Après : 2001:db8::1
```

⚠️ **`::` ne peut être utilisé qu'une seule fois** dans une adresse.

**Exemples :**
```
2001:0db8:0000:0000:0000:ff00:0042:8329
→ 2001:db8::ff00:42:8329

fe80:0000:0000:0000:0204:61ff:fe9d:f156
→ fe80::204:61ff:fe9d:f156

::1
→ Adresse de loopback (équivalent de 127.0.0.1)

::
→ Adresse non spécifiée (équivalent de 0.0.0.0)
```

### Types d'adresses IPv6

**Unicast :**
- Communication un-à-un (comme IPv4)
- Types : globale, link-local, unique-local

**Multicast :**
- Communication un-vers-plusieurs
- Préfixe : `ff00::/8`

**Anycast :**
- Une adresse, plusieurs destinations, la plus proche répond
- Utilisé pour optimisation (DNS, CDN)

**Note :** IPv6 n'a **pas de broadcast** (remplacé par multicast).

### Adresses spéciales IPv6

| Adresse | Notation courte | Équivalent IPv4 | Usage |
|---------|-----------------|-----------------|-------|
| Loopback | ::1/128 | 127.0.0.1 | Interface locale |
| Non spécifiée | ::/128 | 0.0.0.0 | Pas d'adresse |
| Link-local | fe80::/10 | 169.254.x.x | Communication locale |
| Unique-local | fc00::/7 | 10.x.x.x, 192.168.x.x | Privé |
| Globale | 2000::/3 | Publiques | Internet |
| Multicast | ff00::/8 | 224.x.x.x | Diffusion groupe |

### Coexistence IPv4/IPv6

**Mécanismes de transition :**

**Double pile (Dual Stack) :**
- Équipements supportent IPv4 ET IPv6 simultanément
- Approche la plus courante aujourd'hui

**Tunneling :**
- Encapsuler IPv6 dans IPv4 (ou inverse)
- Types : 6to4, 6in4, Teredo

**Traduction (NAT64) :**
- Traduire entre IPv4 et IPv6
- Permet communication entre réseaux hétérogènes

**État actuel (2025) :**
- IPv4 : encore majoritaire (~60-70%)
- IPv6 : adoption croissante (~30-40%)
- Période de transition longue (plusieurs décennies)

### Configuration IPv6

**SLAAC (Stateless Address Autoconfiguration) :**
- Configuration automatique sans serveur
- Utilise Router Advertisement
- Plus simple que DHCP

**DHCPv6 :**
- Équivalent DHCPv4
- Plus de contrôle pour l'administrateur

**Exemple d'adresse globale :**
```
Préfixe réseau (fourni par ISP) : 2001:db8:1234::/48
Sous-réseau (choisi localement)  : :5678:/64
Interface ID (auto ou manuel)    : ::1

Adresse complète : 2001:db8:1234:5678::1/64
```

---

## Exercices pratiques {#exercices}

### Exercice 1 : Conversion binaire/décimal

Convertissez les octets suivants :

**a) Binaire → Décimal**
```
1. 10110100
2. 11111000
3. 00101010
```

**b) Décimal → Binaire**
```
4. 220
5. 15
6. 192
```

**Réponses :**
```
1. 180 (128+32+16+4)
2. 248 (128+64+32+16+8)
3. 42 (32+8+2)
4. 11011100
5. 00001111
6. 11000000
```

### Exercice 2 : Identification des classes

Identifiez la classe de chaque adresse :
```
1. 10.50.100.200
2. 172.16.5.10
3. 192.168.1.1
4. 150.20.30.40
5. 225.100.50.25
```

**Réponses :**
```
1. Classe A (10.x.x.x)
2. Classe B (172.16-31.x.x - aussi privé)
3. Classe C (192.x.x.x - aussi privé)
4. Classe B (150.x.x.x)
5. Classe D (224-239 - multicast)
```

### Exercice 3 : Adresses privées ou publiques ?

```
1. 192.168.50.100
2. 8.8.8.8
3. 172.20.10.50
4. 142.250.185.46
5. 10.0.0.1
```

**Réponses :**
```
1. Privée (192.168.x.x)
2. Publique (DNS Google)
3. Privée (172.16-31.x.x)
4. Publique (Google.com)
5. Privée (10.x.x.x)
```

### Exercice 4 : Calcul avec masque

**Réseau : 172.16.100.50/24**

Déterminez :
```
a) Adresse réseau
b) Adresse broadcast
c) Première IP utilisable
d) Dernière IP utilisable
e) Nombre d'hôtes utilisables
```

**Réponses :**
```
a) 172.16.100.0
b) 172.16.100.255
c) 172.16.100.1
d) 172.16.100.254
e) 254 hôtes (2^8 - 2)
```

### Exercice 5 : Subnetting

**Réseau initial : 192.168.50.0/24**

Créez **8 sous-réseaux** de taille égale.

**Questions :**
```
a) Nouveau masque ?
b) Nombre d'hôtes par sous-réseau ?
c) Adresse réseau du 3ème sous-réseau ?
d) Plage d'hôtes du 5ème sous-réseau ?
```

**Réponses :**
```
a) /27 (255.255.255.224)
   - Pour 8 sous-réseaux : 2^3 = 8, emprunter 3 bits
   
b) 30 hôtes (2^5 - 2 = 32 - 2)
   - 8 - 3 = 5 bits hôte restants
   
c) 192.168.50.64/27
   - Incrément = 32
   - SR1: .0, SR2: .32, SR3: .64
   
d) 192.168.50.129 à 192.168.50.158
   - SR5 commence à 4×32 = 128
   - Réseau: .128, Première: .129, Dernière: .158, Broadcast: .159
```

### Exercice 6 : Conversion CIDR

Convertissez :

**a) Masque → CIDR**
```
1. 255.255.252.0
2. 255.255.255.240
3. 255.224.0.0
```

**b) CIDR → Masque**
```
4. /20
5. /29
6. /13
```

**Réponses :**
```
a)
1. /22 (16 + 6 bits = 22)
2. /28 (24 + 4 bits = 28)
3. /11 (8 + 3 bits = 11)

b)
4. 255.255.240.0
5. 255.255.255.248
6. 255.248.0.0
```

### Exercice 7 : VLSM

**Réseau : 10.20.0.0/16**

Allouez des sous-réseaux pour :
```
- Département A : 500 hôtes
- Département B : 200 hôtes
- Département C : 50 hôtes
- Liaison routeurs : 2 hôtes
```

**Questions :**
```
a) Quel masque pour chaque besoin ?
b) Première allocation (Dept A) ?
c) Deuxième allocation (Dept B) ?
```

**Réponses :**
```
a) 
   Dept A: /23 (2^9-2 = 510 hôtes)
   Dept B: /24 (2^8-2 = 254 hôtes)
   Dept C: /26 (2^6-2 = 62 hôtes)
   Liaison: /30 (2^2-2 = 2 hôtes)

b) Dept A: 10.20.0.0/23
   Plage: 10.20.0.1 - 10.20.1.254

c) Dept B: 10.20.2.0/24
   Plage: 10.20.2.1 - 10.20.2.254
```

### Exercice 8 : IPv6

Simplifiez les adresses suivantes :
```
1. 2001:0db8:0000:0000:0000:0000:0000:0001
2. fe80:0000:0000:0000:0204:61ff:fe9d:f156
3. 2001:0db8:0001:0000:0000:0ab9:c0a8:0102
```

**Réponses :**
```
1. 2001:db8::1
2. fe80::204:61ff:fe9d:f156
3. 2001:db8:1::ab9:c0a8:102
```

---

## 📚 Ressources complémentaires {#ressources}

### Outils en ligne

**Calculateurs de sous-réseaux :**
- ipcalc.org
- subnet-calculator.com
- subnetipv4.com

**Visualisation :**
- VLSM Subnet Calculator
- IPv6 Subnet Calculator

**Entraînement :**
- subnettingpractice.com
- subnetting.org/exercises

### Commandes utiles

**Windows :**
```powershell
ipconfig                  # Afficher configuration IP
ipconfig /all             # Configuration détaillée
ping <IP>                 # Tester connectivité
tracert <IP>              # Tracer la route
```

**Linux :**
```bash
ip addr                   # Afficher adresses IP
ip route                  # Afficher table de routage
ping <IP>                 # Tester connectivité
traceroute <IP>           # Tracer la route
```

### Lecture recommandée

**Pour approfondir :**
- RFC 791 : Internet Protocol (IPv4)
- RFC 950 : Internet Standard Subnetting Procedure
- RFC 1918 : Address Allocation for Private Internets
- RFC 4632 : Classless Inter-domain Routing (CIDR)
- RFC 8200 : Internet Protocol, Version 6 (IPv6)

---

## 📝 Points clés à retenir

✅ **IPv4** : 32 bits, 4 octets, notation décimale pointée

✅ **Classes** (obsolètes mais utiles) :
- A: /8 (1-126)
- B: /16 (128-191)
- C: /24 (192-223)

✅ **Privé** : 10.x.x.x, 172.16-31.x.x, 192.168.x.x

✅ **Masque** : Sépare réseau et hôte, notation /n (CIDR)

✅ **Subnetting** : Diviser un réseau en sous-réseaux
- Formule hôtes : 2^n - 2

✅ **VLSM** : Sous-réseaux de tailles différentes, optimisation

✅ **IPv6** : 128 bits, notation hexadécimale, quasi-illimité

---

## 🔄 Préparation pour la suite

**CM3 : Routage**
- Tables de routage
- Routage statique vs dynamique
- Protocoles de routage (RIP, OSPF)

**TP3 : Subnetting pratique**
- Exercices de calcul
- Configuration réelle
- Vérification de connectivité

---

*Document rédigé pour le module TI305 - Architecture Réseaux*  
*Dernière mise à jour : Octobre 2025*
