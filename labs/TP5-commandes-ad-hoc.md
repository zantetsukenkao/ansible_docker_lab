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

Commandes à tester
1. Récupérer la version du noyau Linux
Exécutez la commande suivante pour afficher la version du noyau sur tous les nœuds :

bash
Copy
ansible all -i inventory -m command -a "uname -r"
2. Afficher l'utilisation de la mémoire
Utilisez cette commande pour afficher l'utilisation de la mémoire sur tous les nœuds :

bash
Copy
ansible all -i inventory -m command -a "free -m"
3. Installer Nginx
Installez le paquet nginx sur tous les nœuds :

bash
Copy
ansible all -i inventory -b -m apt -a "name=nginx state=present"
4. Redémarrer Nginx
Redémarrez le service nginx sur tous les nœuds :

bash
Copy
ansible all -i inventory -b -m service -a "name=nginx state=restarted"
5. Créer un fichier sur les nœuds cibles
Créez un fichier nommé /tmp/testfile.txt sur tous les nœuds :

bash
Copy
ansible all -i inventory -m file -a "path=/tmp/testfile.txt state=touch"
6. Modifier les permissions d'un fichier
Modifiez les permissions du fichier /tmp/testfile.txt pour le rendre accessible en lecture et écriture à tous les utilisateurs :

bash
Copy
ansible all -i inventory -m file -a "path=/tmp/testfile.txt mode='0666'"
7. Afficher l'espace disque disponible
Affichez l'espace disque disponible sur tous les nœuds :

bash
Copy
ansible all -i inventory -m command -a "df -h"
8. Afficher la mémoire disponible
Affichez la mémoire disponible sur tous les nœuds :

bash
Copy
ansible all -i inventory -m command -a "free -m"
9. Afficher la charge système
Affichez la charge système sur tous les nœuds :

bash
Copy
ansible all -i inventory -m command -a "uptime"
10. Copier un fichier local vers les nœuds distants
Copiez un fichier local nommé config.conf vers le répertoire /etc/myapp/ sur tous les nœuds :

bash
Copy
ansible all -i inventory -m copy -a "src=./config.conf dest=/etc/myapp/config.conf"
11. Supprimer un fichier ou un répertoire
Supprimez le fichier /tmp/testfile.txt sur tous les nœuds :

bash
Copy
ansible all -i inventory -m file -a "path=/tmp/testfile.txt state=absent"
