# 🌐 Projet Réseau Segmenté avec VLANs et Routage Statique

## 📌 Description
Ce projet consiste à concevoir et implémenter une infrastructure réseau **segmentée par VLANs**, avec **routage inter-VLAN**, **EtherChannel**, et **routage statique WAN**, en utilisant **Cisco Packet Tracer**.

Il a été réalisé dans le cadre du module **Réseaux Informatiques** à l’**Université Mundiapolis** (1ère année Génie Informatique).

---

## 🎯 Objectifs du projet
- Mettre en œuvre une **segmentation logique** du réseau à l’aide des VLANs  
- Configurer le **routage inter-VLAN (Router-on-a-Stick)**  
- Assurer la **redondance et l’agrégation de liens** avec EtherChannel (LACP)  
- Interconnecter plusieurs sites via un **WAN avec routage statique**  
- Tester et valider la **connectivité de bout en bout**  
- Appliquer les **bonnes pratiques réseau** (VLAN de gestion, VLAN natif sécurisé)

---

## 🏗️ Architecture du réseau

### 🔹 Site principal
- 2 switches de couche 2 (S1 & S2)
- 1 routeur central (R1)
- EtherChannel entre S1 et S2
- Routage inter-VLAN via Router-on-a-Stick

### 🔹 Sites distants
- Routeur R2 et R3
- Liaisons WAN série point à point
- Routage statique

---

## 🧩 VLANs configurés

| VLAN | Nom           | Réseau           | Passerelle |
|-----:|---------------|------------------|------------|
| 10   | IT            | 172.18.10.0/24   | 172.18.10.1 |
| 20   | Ventes        | 172.18.20.0/24   | 172.18.20.1 |
| 30   | Ingénierie    | 172.18.30.0/24   | 172.18.30.1 |
| 50   | Natif         | 172.18.50.0/24   | 172.18.50.1 |
| 60   | Gestion       | 172.18.60.0/24   | 172.18.60.1 |

---

## 🌍 Adressage WAN

| Liaison     | Réseau          | R1             | Routeur distant |
|------------|-----------------|----------------|-----------------|
| R1 ↔ R2    | 10.0.30.176/30  | 10.0.30.178    | 10.0.30.177 |
| R1 ↔ R3    | 10.0.30.184/30  | 10.0.30.185    | 10.0.30.186 |

---

## ⚙️ Technologies utilisées
- Cisco Packet Tracer  
- VLANs & Trunking 802.1Q  
- Router-on-a-Stick  
- EtherChannel (LACP)  
- Routage statique  
- ICMP (ping, traceroute)

---

## 🧪 Tests effectués
- ✅ Communication inter-VLAN  
- ✅ Connectivité WAN entre sites  
- ✅ Connectivité bidirectionnelle  
- ✅ Accès au VLAN de gestion  
- ✅ Vérification des tables de routage  

---

## 🚧 Difficultés rencontrées
- Problème de **VLAN natif non cohérent**
- Interfaces en **shutdown administratif**
- Erreur de **next-hop dans une route statique**
- Délais ARP spécifiques à Packet Tracer

➡️ Tous les problèmes ont été identifiés et corrigés méthodiquement.

---

## 📁 Contenu du dépôt

---

## 📚 Améliorations possibles
- Implémentation de **OSPF**
- Mise en place de **ACLs**
- Redondance de couche 3 (HSRP)
- Support **IPv6**
- Qualité de Service (QoS)

---

## 👤 Auteur
**Ayman Asghar**  
Étudiant – 1ère année Génie Informatique  
Université Mundiapolis  
Année universitaire : 2025 / 2026  

---

## 📎 Références
- Cisco Networking Academy  
- Documentation Cisco IOS  
- Support de cours – Réseaux Informatiques

