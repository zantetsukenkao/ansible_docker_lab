# Exercice : Tester des commandes ad hoc Ansible

---

## Objectif
Cet exercice consiste à tester plusieurs commandes ad hoc Ansible pour interagir avec des nœuds distants. Vous allez utiliser des commandes pour récupérer des informations système, installer et redémarrer un service, gérer des fichiers, et bien plus encore.

---

## Prérequis
1. Un fichier d'inventaire Ansible (`inventory`) configuré avec les nœuds cibles.
2. Un accès SSH aux nœuds cibles.
3. Ansible installé sur votre machine locale.

Exemple de fichier `inventory` :
```ini
[servers]
server1 ansible_host=192.168.1.10
server2 ansible_host=192.168.1.11
