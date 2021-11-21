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

![Respueta 1 - 1](https://user-images.githubusercontent.com/10359307/142750757-36d35fb3-8481-4239-ae21-286146b3f311.png)

3. Ver las ultimas 100 líneas del log de la aplicación.

```
k logs --tail=100 nginx-pod
```

4. Obtener la ip interna del `Pod`.

```
k get pods -o wide
```

![Respueta 1 - 2y3](https://user-images.githubusercontent.com/10359307/142750766-579171db-a59c-4d3f-b3a1-0eabc0060dc4.png)

5. Comando para entrar dentro del `Pod`.

```
k exec -it nginx-pod -- sh
```

6. Ver el contenido expuesto por nginx.

```
# Realizar un port-foward para poder ver el contenido del Pod de nginx
k port-forward nginx-pod 8080:80
```

![Respueta 1 - 4y5](https://user-images.githubusercontent.com/10359307/142750773-9f707d67-9b22-4baa-859b-01ed92029779.png)

7. QoS del `Pod`

```
# El resultado es Guaranteed porque tanto el cpu como la memoria tienen límites iguales
k describe pod nginx-pod | grep QoS
```

![Respueta 1 - 6](https://user-images.githubusercontent.com/10359307/142750779-e75a8b3b-a0cb-4a79-9101-dca127837363.png)

