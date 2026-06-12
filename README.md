# Infrastructure de Sécurité Réseau Multi-Couches sous Ubuntu 24.04

## Présentation

Ce projet a pour objectif la mise en place d'une architecture de sécurité réseau reposant sur le principe de la défense en profondeur (Defense in Depth).

L'infrastructure a été réalisée et testée sous Ubuntu 24.04 et s'appuie sur quatre couches de sécurité complémentaires :

* WireGuard : chiffrement des communications réseau
* UFW : filtrage des connexions entrantes et sortantes
* nftables : contrôle avancé du trafic et limitation comportementale
* Pi-hole : filtrage DNS et blocage des domaines malveillants

L'objectif est de démontrer comment plusieurs mécanismes de sécurité peuvent être combinés afin de réduire la surface d'attaque tout en conservant une architecture simple à maintenir.

---

## Architecture

### Couche 1 : WireGuard VPN

Mise en place d'un tunnel VPN chiffré entre un client Ubuntu et un serveur WireGuard.

Fonctionnalités :

* Chiffrement des communications
* Authentification par clés publiques/privées
* Configuration sécurisée des permissions
* Démarrage automatique au boot
* Validation de la connectivité du tunnel

---

### Couche 2 : Pare-feu UFW

Ajout d'une politique de filtrage restrictive.

Règles principales :

* Blocage par défaut des connexions entrantes
* Autorisation du trafic sortant
* Autorisation explicite :

  * SSH (22/TCP)
  * WireGuard (51820/UDP)

Fonctionnalités :

* Journalisation des événements
* Analyse des connexions bloquées
* Procédures de dépannage documentées

---

### Couche 3 : nftables

Ajout d'un contrôle comportemental avancé.

Fonctionnalités :

* Filtrage stateful
* Analyse des flux réseau
* Monitoring du trafic
* Compteurs de paquets
* Limitation des tentatives de connexion SSH
* Persistance des règles après redémarrage

Exemple :

* Limitation à 5 nouvelles connexions SSH par minute

---

### Couche 4 : Pi-hole

Mise en place d'un serveur DNS filtrant local.

Fonctionnalités :

* Blocage des publicités
* Blocage des trackers
* Protection contre le phishing
* Protection contre certains domaines malveillants
* Journalisation centralisée des requêtes DNS

Listes utilisées :

* Steven Black Hosts
* AdAway
* MalwareDomainList
* Phishing Army
* URLHaus

---

## Technologies utilisées

* Ubuntu 24.04 LTS
* WireGuard
* UFW
* nftables
* Pi-hole
* systemd
* Linux Networking

---

## Résultats obtenus

* Tunnel VPN fonctionnel
* Chiffrement des communications
* Réduction de la surface d'exposition réseau
* Limitation des tentatives de connexion abusives
* Blocage des domaines publicitaires et malveillants
* Architecture stable et persistante après redémarrage

---

## Limites du projet

Cette infrastructure améliore significativement la sécurité du système mais ne protège pas contre :

* Les vulnérabilités applicatives
* Les attaques physiques
* Les compromissions locales
* Les failles zero-day
* Les erreurs humaines

La sécurité repose sur une approche multicouche où chaque composant complète les autres.

---

## Documentation complète

La documentation détaillée du projet est disponible dans :

![Infrastructure de Sécurité Réseau(loic lemasson).pdf](https://github.com/user-attachments/files/28878618/Infrastructure.de.Securite.Reseau.loic.lemasson.pdf)


---

## Auteur

Loïc Lemasson

Projet réalisé dans un objectif de montée en compétences en administration système, réseau et cybersécurité.

Licence : CC BY-NC-SA 4.0
