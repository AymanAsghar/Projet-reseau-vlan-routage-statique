# 🌐 Infrastructure Réseau Multisite Segmentée (Cisco)

## 📝 Présentation du Projet
Ce projet consiste en la conception et le déploiement d'une infrastructure réseau d'entreprise complète et sécurisée, réalisée sur **Cisco Packet Tracer**. L'architecture répond aux besoins modernes de segmentation, de redondance et d'interconnexion distante (WAN).

## 🚀 Fonctionnalités Techniques
* **Segmentation de Couche 2** : Mise en œuvre de VLANs pour isoler les flux (Compta, RH, Vente, Admin, Natif).
* **Haute Disponibilité** : Configuration d'un **EtherChannel (LACP)** entre les switches pour l'agrégation de liens et la tolérance aux pannes.
* **Routage Inter-VLAN** : Architecture **Router-on-a-Stick** configurée sur le routeur central (R1) via des sous-interfaces 802.1Q.
* **Interconnexion WAN** : Mise en place de **routage statique** pour lier le siège aux sites distants.
* **Sécurité & Gestion** : Configuration d'un VLAN d'administration dédié (VLAN 60) et d'un VLAN natif (VLAN 50).

## 📊 Topologie Réseau
![Topologie du réseau](./screenshots/topology.png)
*Légende : La topologie montre l'interconnexion entre le routeur R1, les switches S1/S2 liés en EtherChannel, et les postes clients.*

## 📋 Plan d'Adressage (VLSM)
| Réseau / VLAN | Nom | Plage IP | Masque | Passerelle |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN 10** | DATA_1 | 172.18.10.0/28 | .240 | 172.18.10.14 |
| **VLAN 20** | DATA_2 | 172.18.20.0/28 | .240 | 172.18.20.14 |
| **VLAN 30** | DATA_3 | 172.18.30.0/28 | .240 | 172.18.30.14 |
| **VLAN 60** | ADMIN | 172.18.60.0/28 | .240 | 172.18.60.14 |
| **Lien WAN** | R1-R3 | 10.0.30.176/30 | .252 | - |

## 🧪 Validation & Tests
Les tests suivants ont été validés avec succès (voir captures dans `/screenshots`) :
* **Connectivité Inter-VLAN** : Ping réussi entre PC1 (VLAN 10) et PC2 (VLAN 20).
* **Routage WAN** : `tracert` confirmant le passage par R1 vers les réseaux distants.
* **Vérification des Routes** : Analyse de la table de routage via `show ip route`.

## 📂 Structure du Dépôt
* `/topology` : Fichier `.pkt` (Cisco Packet Tracer).
* `/docs` : Rapport technique détaillé et guide de déploiement.
* `/screenshots` : Preuves de tests et schémas.

---
**Auteur :** Ayman Asghar  
**Encadrant :** Prof. Azeddine KHIAT  
**Année :** 2025/2026 - Université Mundiapolis
