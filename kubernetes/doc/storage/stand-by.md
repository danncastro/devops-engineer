# Stand by

***

### <mark style="color:red;">Criando PVs</mark>

Como todo recurso no kubernetes, criamos `PVs` através de arquivos yaml. Porém precisaremos criar os volumes antes de criar os `PVs`, vamos conectar em nosso minikube e criar os volumes

```bash
$ minikube ssh
$ sudo mkdir /mnt/dados{1..3}
$ sudo sh -c "echo 'Kubernetes Storage Dados 1' > /mnt/dados1/index.html"
$ sudo sh -c "echo 'Kubernetes Storage Dados 2' > /mnt/dados2/index.html"
$ sudo sh -c "echo 'Kubernetes Storage Dados 3' > /mnt/dados3/index.html"
$ ls -lR /mnt
$ exit
```

Agora que temos nossos diretórios de dados, vamos criar nossos PersistentVolumes

```bash
$ vim pv.yml
```

```yml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv10m
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 10Mi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/dados1"
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv200m
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 200Mi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/dados2"
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv1g
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/dados3"
```

> Podemos descrever diversos recursos abrindo um novo yaml através do `---` em um mesmo arquivo

Vamos criar e listar nossos `PVs`

```bash
$ kubectl apply -f pv.yml
$ kubectl get persistentvolumes
$ kubectl get pv
```

```bash
NAME     CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
pv10m    10Mi       RWO            Retain           Available           manual                  42s
pv1g     1Gi        RWO            Retain           Available           manual                  42s
pv200m   200Mi      RWO            Retain           Available           manual                  42s
```

***

### <mark style="color:red;">Criando PVCs</mark>

Vamos criar nossos PVCs através de um arquivo yaml

```bash
$ vim pvc.yml
```

```yml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc100m
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 100Mi
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc700m
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 700Mi
```

Vamos criar e listar nossos `PVs`

```bash
$ kubectl apply -f pvc.yml
$ kubectl get persistentvolumeclaims
$ kubectl get pvc
$ kubectl get pv 
```

```bash
NAME      STATUS   VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
pvc100m   Bound    pv200m   200Mi      RWO            manual         30s
pvc700m   Bound    pv1g     1Gi        RWO            manual         30s
```

```bash
NAME     CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM             STORAGECLASS   REASON   AGE
pv10m    10Mi       RWO            Retain           Available                     manual                  10m
pv1g     1Gi        RWO            Retain           Bound       default/pvc700m   manual                  10m
pv200m   200Mi      RWO            Retain           Bound       default/pvc100m   manual                  10m
```

Podemos ver que o os `PVs` que solicitamos foram atrelados ao `PV` que satisfaz todas suas necessidades listadas, ligando o `PVC` que solicitou 100Mi ao `pv200m` e o `PVC` que solicitou 700m ao `pv1g`.

***

### <mark style="color:red;">Atrelando Pod a Volumes.</mark>

Para ligar um Pod a um volume, precisamos declara-lo no yaml de criação do pod.

```bash
$ vim webserver.yml
```

```yml
apiVersion: v1
kind: Pod
metadata:
  name: webserver
spec:
  volumes:
    - name: webdata
      persistentVolumeClaim:
        claimName: pvc100m
  containers:
    - name: webserver
      image: nginx
      ports:
        - containerPort: 80
          name: "http-server"
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: webdata
```

> Note que a configuração do Pod aponta para um `PVC` porém não especificamos o `PV`. Isso se dá porque pelo ponto de vista do Pod, um `Claim` é um volume.

Vamos executar nosso pod e verificar o volume

```bash
kubectl apply -f webserver.yml
kubectl get pods
kubectl exec -it webserver -- /bin/bash
curl localhost
exit
```

Vamos alterar nosso pod para utilizar o outro `PVC`.

```bash
kubectl detele pod/webserver
vim webserver.yml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: webserver
spec:
  volumes:
    - name: webdata
      persistentVolumeClaim:
        claimName: pvc700m
  containers:
    - name: webserver
      image: nginx
      ports:
        - containerPort: 80
          name: "http-server"
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: webdata
```

Vamos executar nosso pod e verificar o volume

```bash
kubectl apply -f webserver.yml
kubectl get pods
kubectl exec -it webserver -- /bin/bash
curl localhost
exit
```

Mais informações sobre Volumes podem ser vistas na [Documentação Oficial](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

***

### <mark style="color:red;">Destruindo o Ambiente</mark>

Agora que passamos por todos os conceitos base do kubernetes, podemos destruir nosso ambiente do minikube

```bash
minikube delete
```
