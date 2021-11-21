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

#imagen1

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

#imagen2

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

#imagen3

```
# Se puede acceder al servicio con el puerto especificado:
[minikube-ip]:30001
```
