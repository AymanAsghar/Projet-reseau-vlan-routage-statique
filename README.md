# Projet-réseau-VLAN-routage-statique

> **Projet Technique :** Conception et déploiement d'une infrastructure Cisco complète avec segmentation VLAN, EtherChannel et routage statique WAN.

![Cisco](https://img.shields.io/badge/Cisco-Packet_Tracer-049fd9?style=for-the-badge&logo=cisco)
![Status](https://img.shields.io/badge/Status-OPÉRATIONNEL-success?style=for-the-badge)
![Year](https://img.shields.io/badge/Année-2025%2F2026-blueviolet?style=for-the-badge)
![VLAN](https://img.shields.io/badge/VLAN-802.1Q-important?style=for-the-badge)
![Routage](https://img.shields.io/badge/Routage-Statique-informational?style=for-the-badge)

## 📌 Présentation du Projet
Ce projet académique consiste en la conception et mise en œuvre d'une infrastructure réseau multisites segmentée avec VLANs, EtherChannel, Router-on-a-Stick et routage statique WAN. L'objectif est de démontrer la maîtrise des technologies de commutation avancée et de routage pour assurer la disponibilité, la sécurité et la performance des données dans un environnement d'entreprise simulé.

**Étudiant :** Ayman Asghar  
**Encadrant :** Pr. KH.IAT  

---

## 🏗️ Topologie & Matériel
L'infrastructure utilise une approche modulaire hiérarchique pour séparer les services (administration, utilisateurs, serveurs) et optimiser les performances réseau.

### Inventaire des Équipements
| Matériel | Quantité | Rôle Stratégique |
| :--- | :---: | :--- |
| **Routeur Cisco** | 3+ | Routage inter-VLAN et interconnexion WAN |
| **Switch Cisco 2960** | 2+ | Commutation d'accès avec segmentation VLAN |
| **PC Clients/Serveurs** | Plusieurs | Postes utilisateurs et services segmentés |

> [!NOTE]
> La topologie complète intègre une zone LAN principale segmentée en VLANs et une connexion WAN vers des sites distants via des liaisons séries.

---

## 🛠️ Schéma d'Adressage IP
Une planification rigoureuse a été appliquée pour garantir une allocation IP cohérente, éviter les conflits et faciliter l'administration et l'évolutivité du réseau.

| Périphérique | Interface / VLAN | Adresse IP / Masque | Description |
| :--- | :--- | :--- | :--- |
| **Routeur Principal** | Fa0/0.10 | 172.18.10.1 /28 | Passerelle VLAN 10 (Administration) |
| **Routeur Principal** | Fa0/0.20 | 172.18.20.1 /28 | Passerelle VLAN 20 (Utilisateurs) |
| **Routeur Principal** | S0/0/0 | 10.0.30.1 /30 | Lien WAN vers Site B |
| **Switch de Gestion** | VLAN 60 | 172.18.60.2 /28 | IP de Management du Switch |
| **Routeur Site B** | Loopback0 | 10.0.30.129 /32 | Interface de Test Distant |

---

## 🚀 Fonctionnalités Déployées

### 1. Commutation Avancée (Switching)
- **Segmentation VLAN (IEEE 802.1Q) :** Création de plusieurs domaines de diffusion logiques pour isoler les services (ex: VLAN 10, 20, 30, 50, 60).
- **EtherChannel (LACP/PAGP) :** Agrégation de liens entre switches pour augmenter la bande passante, assurer la redondance et optimiser l'utilisation des ressources.
- **Trunking :** Configuration de ports trunk pour le transport efficace de multiples VLANs entre équipements.
- **Sécurité des Ports :** Mise en place de politiques de sécurité de base sur les ports d'accès.

### 2. Routage et Connectivité (Routing)
- **Router-on-a-Stick :** Configuration des sous-interfaces sur le routeur principal pour permettre la communication inter-VLANs.
- **Interconnexion WAN :** Établissement de liaisons point-à-point série entre sites avec encapsulation HDLC ou PPP.
- **Routage Statique :** Configuration manuelle et optimisée des tables de routage pour une convergence réseau prévisible et contrôlée entre les différents sites et réseaux.
- **Connectivité Internet (Optionnel) :** Configuration de la NAT/PAT pour l'accès sortant.

---

## 🔍 Validation du Fonctionnement (Tests)

### Test de Connectivité Inter-VLAN
Le test suivant vérifie que les hôtes de différents VLANs peuvent communiquer via le routeur (Router-on-a-Stick).

```bash
C:\> ping 172.18.20.10
Reply from 172.18.20.10: bytes=32 time<1ms TTL=128
Reply from 172.18.20.10: bytes=32 time<1ms TTL=128
Ping statistics successful.
C:\> tracert 10.0.30.129
Tracing route to 10.0.30.129 over a maximum of 30 hops:
  1    0 ms    0 ms    0 ms    172.18.10.1
  2    10 ms   9 ms    10 ms   10.0.30.1
  3    12 ms   11 ms   12 ms   10.0.30.129
Trace complete.
Switch# show etherchannel summary
Flags:  D - down        P - bundled in port-channel
        I - stand-alone s - suspended
        H - Hot-standby (LACP only)
        u - unsuitable for bundling
        U - in use        f - failed to allocate aggregator
        d - default port
Number of channel-groups in use: 1
Number of aggregators:           1
Group  Port-channel  Protocol    Ports
------+-------------+-----------+-----------------------------------------------
1      Po1(SU)         LACP        Fa0/23(P)   Fa0/24(P)
