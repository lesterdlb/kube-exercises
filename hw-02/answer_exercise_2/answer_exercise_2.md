# answer_exercise_2

## Creación de un objeto `ReplicaSet`

1. Archivo de configuración.

```yml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replica
  labels:
    app: nginx-server
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx-server
  template:
    metadata:
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

2. Crear el objeto `ReplicaSet`.

```
k apply -f nginx-replica.yml
k get pods --show-labels
k get rs -o wide
```

#imagen1

3. Escalar el número de réplicas a 10.

```
k scale --replicas=10 rs nginx-replica
k get pods --show-labels
```

imagen2

4. Si necesito tener una réplica en cada uno de los nodos de Kubernetes,
   ¿qué objeto se adaptaría mejor?

El objeto `DaemonSet`, ya que este garantiza que todos o algunos nodos tengan una copia de un pod.
