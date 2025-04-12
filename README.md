# gns3-filebrowser-deploy

# Déploiement automatique GNS3 Server + File Browser avec Ansible

Ce projet me permet de déployer en une seule commande un serveur GNS3 et un gestionnaire de fichiers (File Browser) sur un VPS Ubuntu 24.04 dans le cadre de mon homelab

## 🔧 Technologies
- Ansible
- GNS3 Server
- File Browser
- Systemd
- Ubuntu 24.04

## Commande de lancement
```bash
ansible-playbook -i hosts.ini deploy_gns3_filebrowser.yml
