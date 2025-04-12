# gns3-filebrowser-deploy

Ce projet permet de déployer automatiquement un serveur GNS3 et/ou File Browser sur un VPS Ubuntu 24.04 à l'aide d'Ansible. Il est organisé en rôles pour un déploiement modulable.

---

## 🌐 Fonctionnalités

- Installation de GNS3 Server avec service systemd
- Installation de File Browser avec service systemd
- Gestion des ports personnalisables (3080 pour GNS3, 8080 pour File Browser)
- Lancement automatique au démarrage
- Sélection du composant à installer via variables Ansible

---

##  Arborescence du projet

```bash
ansible-gns3-filebrowser/
├── deploy_gns3_filebrowser.yml      # Playbook principal
├── hosts.ini                        # Inventaire Ansible
├── README.md                        # Ce fichier de présentation
├── roles/
│   ├── gns3/
│   │   └── tasks/
│   │       └── main.yml             # Tâches pour GNS3 Server
│   └── filebrowser/
│   │   └── tasks/
│   │       └── main.yml             # Tâches pour File Browser
│   └── nginx/
│       └── tasks/
│           └── main.yml            # Tâches pour nginx
└── .gitignore                       # Pour exclure fichiers sensibles
```

---

## 🚀 Lancer le déploiement

```bash
ansible-playbook -i hosts.ini deploy_gns3_filebrowser.yml
```

### 🔀 Lancer uniquement GNS3 Server
```bash
ansible-playbook -i hosts.ini deploy_gns3_filebrowser.yml -e "gns3_install=true"
```

### 🔀 Lancer uniquement File Browser
```bash
ansible-playbook -i hosts.ini deploy_gns3_filebrowser.yml -e "filebrowser_install=true"
```

### 🔀 Lancer l'installation de NGINX avec reverse proxy -> file browser
```bash
ansible-playbook -i hosts.ini deploy_gns3_filebrowser.yml -e "nginx_install=true"
```

---

## ⚙ Variables personnalisables

Les variables sont définies dans le playbook principal :

```yaml
gns3_port: 3080
filebrowser_port: 8080
filebrowser_dir: /root/dossier_fileBrowser
```

---

##  Exemple de hosts.ini

```ini
[gns3]
192.0.2.10 ansible_user=root
```

---

## 🧠 Créateur

Projet conçu par moi pour déployer une stack réseau auto-hébergée, portable et propre.  
Compatible avec Hetzner, Proxmox ou tout VPS Ubuntu 24.04.

