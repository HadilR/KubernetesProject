# Déploiement de Nginx avec Kubernetes

Ce guide vous aidera à déployer Nginx sur Kubernetes en utilisant Minikube. Assurez-vous de suivre les étapes ci-dessous pour installer Docker, Kubernetes, et Minikube, puis déployez Nginx avec les fichiers de configuration fournis.

## Prérequis

Avant de commencer, assurez-vous d'avoir Docker installé sur votre machine. Si ce n'est pas le cas, vous pouvez l'installer en utilisant la commande suivante :

```bash
sudo apt-get update
sudo apt-get install docker.io
```

##Installation de Kubernetes et Minikube
### install kubernetes :
- Téléchargez kubectl
```bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
```

- Donnez les permissions d'exécution à kubectl
```bash
chmod +x kubectl
```

- Déplacez kubectl dans un répertoire dans votre PATH
```bash
sudo mv kubectl /usr/local/bin/
```

### Installez Minikube
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

- Donnez les permissions d'exécution à Minikube
```bash
chmod +x minikube-linux-amd64
```

- Déplacez Minikube dans un répertoire dans votre PATH
```bash
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```

## Démarrage de Minikube
```bash
minikube start 
```

### probleme permission:
- Ajoutez votre utilisateur au groupe docker
```bash
sudo usermod -aG docker $USER
```

- Redémarrez votre session ou exécutez la commande suivante pour appliquer les modifications immédiatement
```bash
newgrp docker
```

##Déploiement de Nginx
- Copiez les fichiers de configuration fournis :
```bash
nginx-inst-dep.yaml
nginx-service.yaml
script-nginx.sh
```

- Rendez le script de déploiement exécutable :
```bash
sudo chmod +x scripts-nginx.sh
```

## Accès au service Nginx
- Pour obtenir l'URL du service Nginx déployé, utilisez la commande :
```bash
minikube service nginx-service --url
```

## Conclusion
- Vous avez maintenant déployé avec succès Nginx sur Kubernetes à l'aide de Minikube. 
