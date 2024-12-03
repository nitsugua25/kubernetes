# Exo1

## Lancer le pod

```shell
# nom du fichier .yaml
kubectl apply -f www_pod.yaml
```

## Lister le pod 

```shell
kubectl get all 
# or 
kubectl get pod
```

## Lancement d'un shell dans le pod 

Dans le terminal avant d'être dans le shell du pod
```shell
# nom du pod obtenue via la commande du dessus
kubectl exec -it www -- /bin/bash
# ou alors /bin/sh si bash marche pas
```

Dans le shell du pod 
```shell
nginx -v
```
Une fois que vous avez la version
```shell
exit
```

## Port forward le port du pod 

```shell
# Reprendre le nom du pod choisir un port pour l'ext et prendre le port du pod
kubectl port-forward www 9999:80 
# on peut rajouter "&" pour le faire tourner en background
```
Puis pour vérifier soit aller a 
localhost:9999
-------------------------
Soit utiliser 
```shell
curl localhost:9999
```


## Supprimer le pod 

```shell
kubectl delete pod www
```
