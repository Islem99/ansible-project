# ansible-project

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

Pour sécuriser le nom d'utilisateur et le mot de passe de votre compte Docker Hub vous pouvez les mettre dans un fichier .env puis chiffrer ce fichier en utilisant Ansible-vault. Voici comment procéder :

1- Créez le fichier .env : Commencez par créer un nouveau fichier .env où vous stockerez le nom d'utilisateur et le mot de passe de votre compte Docker Hub.  `touch .env`.

2- Ajoutez les variables d'environnement : Dans le fichier .env, ajoutez les variables d'environnement contenant le nom d'utilisateur et le mot de passe de votre compte Docker Hub. Par exemple : 
  ```
   docker_username =my_docker_username
   docker_password=my_docker_password
  ```
3- Chiffrez le fichier .env avec Ansible Vault : Utilisez Ansible Vault pour chiffrer le fichier .env contenant les variables d'environnement sensibles. Exécutez la commande suivante pour chiffrer le fichier .env : `ansible-vault encrypt .env` Vous serez invité à saisir le mot de passe pour chiffrer le fichier.

4- Dans vos playbooks, vous pouvez accéder aux variables d'environnement chiffrées en utilisant:

```
vars_files:
    - .env

```

5- Vous devez augmenter les zones de mémoire virtuelle maximale pour vous pouvez lancer tous les conteneurs.


## Lancement de Ansible

Pour lancer Ansible, nous pouvons utiliser la commande ansible-playbook suivi du nom du playbook que vous souhaitez exécute

`ansible-playbook my_playbook.yml`

 
