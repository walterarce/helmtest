# helmtest 
## Test de como subir un repo que me baje previamente localmente en la maquina describo los pasos
0.en mi maquina previamente he creado una carpeta my-helm-repo
y antes de generar el pull --untar ejecute el siguiente codigo desde el repo stable
1.
'''
 helm repo add nginx https://helm.nginx.com/stable
'''
2.luego realice el pull
'''powershell
$ cd ./my-helm-repo
$ helm pull --untar nginx/nginx-ingress
'''
3.En el archivo de values, lo que hice fue modificar las replicas por 3
'''yaml
controller:
  kind: deployment
...
## The number of replicas of the Ingress controller deployment.
replicaCount: 3
...
'''
4.desde la carpeta origen ejecute el siguiente comando 

'''
C:\Users\walte\Documents\dev\my-helm-repo> helm package .\nginx-ingress\
''' 

Luego genere un indice de ese paquete

$ helm repo index .
Una vez que tuve en paquete el cambio borre la carpeta

Luego de subir todo lo que tengo en esa carpeta al git hub
ejecuto lo siguiente

$ helm repo add my-repo https://raw.githubusercontent.com/<YOUR_GITHUB_USERNAME>/my-helm-repo/master
$ helm repo update


walte@DESKTOP-QIN9U2Q MINGW64 ~/Documents/dev/my-helm-repo (master)
$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "my-repo" chart repository
...Successfully got an update from the "nginx" chart repository
...Successfully got an update from the "stable" chart repository
Update Complete. ⎈Happy Helming!⎈

