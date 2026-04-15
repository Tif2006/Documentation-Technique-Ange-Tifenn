# 🐳 Installation de Grafana avec Docker

![image.png](image.png)

## 📋 Prérequis

Avant de commencer nous devons avoir installé :

- **Docker**
- **Docker Compose**

On peut vérifier les versions installées avec la commande:

```bash
sudo docker --version
sudo docker compose version
```

---

### Étape 1 — Création du dossier

On va créer un dossier et se mettre dans ce dossier avec la commande suivante :

```bash
mkdir grafana-docker && cd grafana-docker
```

![image.png](image%201.png)

### Étape 2 — Création du fichier docker-compose.yml

On exécute la commande pour se mettre dans notre fichier yml

```bash
sudo nano docker-compose.yml
```

Ensuite on entre dans le fichier les commandes :

```yaml
version: '3.8'

services:
  grafana:
    image: grafana/grafana:latest
    container_name: grafana
    restart: unless-stopped
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin
      - GF_USERS_ALLOW_SIGN_UP=false
    volumes:
      - grafana_data:/var/lib/grafana
      - ./provisioning:/etc/grafana/provisioning

volumes:
  grafana_data:
```

![image.png](image%202.png)

### Étape 3 — Lancement de Grafana

On lance notre conatainer

```bash
sudo docker compose up -d
```

![image.png](image%203.png)

### Étape 4 — Vérification que le conteneur tourne

On lance la commande suivante :

```bash
sudo docker compose ps

```

---

## Étape 5 — Première connexion

1. On accède à l’interface en tapant: [**http://<notre_addresse_IP>:3000**](http://localhost:3000)

![image.png](image%204.png)

1. Les identifiants par défaut sont :
    - **Login** : `admin`
    - **Mot de passe** : `admin`

![image.png](image%205.png)

1. Grafana nous demandera de changer le mot de passe à la première connexion

![image.png](image%206.png)

Et voilà on accède à l’interface

![image.png](image%207.png)

---

<aside>
🤠

**Documentation technique rédigée par :** Ange-Tifenn Agbahoungba

</aside>