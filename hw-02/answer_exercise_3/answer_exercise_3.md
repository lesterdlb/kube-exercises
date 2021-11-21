# answer_exercise_3

## Creación de un objeto `Service`

1. Servicio que expone la aplicación al exterior.

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service1
spec:
  type: NodePort
  selector:
    app: nginx-server
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

```
k apply -f service1.yml
k get svc
k get endpoints nginx-service1
```

![Respuesta 3 - 1](https://user-images.githubusercontent.com/10359307/142750814-3987f76c-e3f4-413d-b339-8ec6ffbcbf83.png)

```
# Para acceder al servicio hay que utilizar la ip del clúster:
[minikube-ip]:[service-node-port]
```

2. Servicio que NO expone la aplicación al exterior.

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service2
spec:
  type: ClusterIP
  selector:
    app: nginx-server
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

```
k apply -f service2.yml
k get svc
```

![Respuesta 3 - 2](https://user-images.githubusercontent.com/10359307/142750820-f8a228a7-0efe-430e-b03a-2dde8fec9810.png)

3. Servicio que expone un puerto especifico.

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service3
spec:
  type: NodePort
  selector:
    app: nginx-server
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30001
```

```
k apply -f service3.yml
k get svc
```

![Respuesta 3 - 3](https://user-images.githubusercontent.com/10359307/142750824-e6a35740-4016-4a17-9edb-aab4fa856d92.png)

```
# Se puede acceder al servicio con el puerto especificado:
[minikube-ip]:30001
```
