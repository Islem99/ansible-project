# projet-Ansible

## Les prérequis

- L'infrastructure (instance EC2) crée et gérée par Terraform
- Ouvrir Visual Studio pour écrire les playbook necéssaire à la configuration de l'instance EC2.

## Les objectifs de projet Ansible

Ansible est un outil d'automatisation et de gestion de configuration qui permet aux administrateurs système de déployer et de gérer des infrastructuresen utilisant des "Playbooks" (fichiers YAML) qui décrivent l'état souhaité du système et les tâches à effectuer pour l'atteindre.

Dans notre projet le playbook a pour objectif:

 1) Installer Docker et Docker-compose
 2) Copier un fichier Docker-compose au serveur EC2
 3) Lancement des conteneurs en utilisant la commande docker-compose
 
 

Pour générer une paire de clés SSH (clé publique et clé privée), nous poucons z utiliser la commande ssh-keygen. 

`ssh-keygen -t rsa -f ~/.ssh/ma_cle`  -t pour spécifier le type de clé (par défaut RSA), et l'option -f pour indiquer le nom du fichier où la clé sera enregistrée.



## Lancement Ansible

Pour lancer Ansible, nous pouvons utiliser la commande ansible-playbook suivi du nom du playbook que vous souhaitez exécute

`ansible-playbook my_playbook.yml`

 
