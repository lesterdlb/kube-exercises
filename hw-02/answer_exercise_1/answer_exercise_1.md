# answer_exercise_1

## Creación de un objeto `Pod`

1. Archivo de configuración.

```yml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx-server
spec:
  containers:
    - name: nginx
      image: nginx:1.19.4
      resources:
        requests:
          memory: '256Mi'
          cpu: '100m'
        limits:
          memory: '256Mi'
          cpu: '100m'
      ports:
        - containerPort: 80
```

2. Crear el `Pod`.

```
k apply -f nginx-pod.yml

k get pods --show-labels
```

#imagen1

3. Ver las ultimas 100 líneas del log de la aplicación.

```
k logs --tail=100 nginx-pod
```

4. Obtener la ip interna del `Pod`.

```
k get pods -o wide
```

#imagen2y3

5. Comando para entrar dentro del `Pod`.

```
k exec -it nginx-pod -- sh
```

6. Ver el contenido expuesto por nginx.

```
# Realizar un port-foward para poder ver el contenido del Pod de nginx
k port-forward nginx-pod 8080:80
```

#imagen4y5

7. QoS del `Pod`

```
# El resultado es Guaranteed porque tanto el cpu como la memoria tienen límites iguales
k describe pod nginx-pod | grep QoS
```
