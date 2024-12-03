# Commande Kubernetes 
## *Pod start*

Pour déployer un pod:
```sh
kubectl apply -f nom.yml
```
## *Port Forward*

### *Initalisé le port forwarding*

**_Sans --address (par défaut)_**

kubectl port-forward hello-pod 9090:80
- Écoute uniquement sur localhost (127.0.0.1)
- Accessible uniquement depuis la machine locale

**Avec --address 0.0.0.0**
kubectl port-forward --address 0.0.0.0 hello-pod 9090:80
- Écoute sur toutes les interfaces
- Accessible depuis le réseau local
- Uniquement en développement
  

```sh
kubectl port-forward [Choix_adresse] [nom_pod] [port_ext]:[port_pod] [&] 
# Le & sert a le faire tourner un background
kubectl port-forward --address 0.0.0.0 hello-pod 9090:80 
```
### *Coupé le port forwarding*

Si il est pas en bg faire ctrl+c

Si il est en bg

```sh
# 1. Trouver le processus kubectl qui fait le port-forward
netstat -ano | findstr :[port]

# 2. Voir les processus kubectl
tasklist | findstr kubectl

# 3. Tuer le processus (deux méthodes)
# Méthode 1 - Par PID (remplacer XXXX par le PID trouvé)
taskkill /PID XXXX /F

# Méthode 2 - Tous les processus kubectl
taskkill /F /IM "kubectl.exe" /T
```