# Créer un module personnalisé Ansible  

## Créer un module personnalisé 

### Étape 1 : Créer la structure de répertoire  

```
mkdir -p custom_module/library
cd custom_module/library
```

### Étape 2 : Écrire le module personnalisé
Nom du fichier : hello_module.py

```
#!/usr/bin/python

from ansible.module_utils.basic import AnsibleModule

def main():
    # Définition des arguments acceptés par le module
    module_args = dict(
        name=dict(type='str', required=True)
    )

    # Initialisation du module
    module = AnsibleModule(
        argument_spec=module_args
    )

    # Récupération du nom passé en paramètre
    name = module.params['name']

    # Message de retour
    result = dict(
        changed=False,
        message=f"Hello, {name}!"
    )

    # Fin de l'exécution avec succès
    module.exit_json(**result)

if __name__ == '__main__':
    main()

```

N’oubliez pas de rendre ce fichier exécutable :

```
chmod +x hello_module.py

```
### Créer le playbook pour tester le module
Fichier : test_module.yml

```
---
- name: Test du module personnalisé Ansible
  hosts: localhost
  tasks:
    - name: Exécuter le module hello_module
      hello_module:
        name: "Ansible User"

```

### Lancer le playbook

Ajoutez le répertoire library au chemin de recherche des modules :

```
ANSIBLE_LIBRARY=./library ansible-playbook test_module.yml
```

### Validation
Vérifiez que la sortie contient :

```
TASK [Exécuter le module hello_module]
ok: [localhost] => {
    "changed": false,
    "message": "Hello, Ansible User!"
}
