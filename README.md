Déploiement de 4 Instances de Nginx


Ce ReadMe fournit les instructions nécessaires pour préparer votre environnement et déployer l'application NGINX sur Kubernetes à l'aide de Minikube.

Prérequis
Avant de commencer, assurez-vous d'avoir installé Docker sur votre machine en utilisant la commande suivante:

Installation Docker
sudo apt install docker.io

Installation de Kubernetes
kubectl

# Téléchargez kubectl
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

# Donnez les permissions d'exécution à kubectl
chmod +x kubectl

# Déplacez kubectl dans un répertoire dans votre PATH
sudo mv kubectl /usr/local/bin/

Installation Minikube
# Installez Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

# Donnez les permissions d'exécution à Minikube
chmod +x minikube-linux-amd64

# Déplacez Minikube dans un répertoire dans votre PATH
sudo mv minikube-linux-amd64 /usr/local/bin/minikube

Configuration Minikube

# Démarrer Minikube (avec deux processeurs)
minikube start

En cas de problème de permission, ajoutez votre utilisateur au groupe docker:
# Ajoutez votre utilisateur au groupe docker
sudo usermod -aG docker $USER

# Redémarrez votre session ou exécutez la commande suivante pour appliquer les modifications immédiatement
newgrp docker


Déploiement de NGINX sur Kubernetes
# Clonez le repository
git clone <URL_DU_REPO>
cd <REP_DU_PROJET>

# Exécutez le script de déploiement
sudo chmod +x scripts/deploy.sh
./scripts/deploy.sh

Après le déploiement, vous pouvez accéder au service NGINX à l'aide de la commande:
minikube service nginx-service --url

Cela fournira l'URL à laquelle le service NGINX est accessible.
