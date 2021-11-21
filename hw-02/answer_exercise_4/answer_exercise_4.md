# answer_exercise_4

## Creación de un objeto `Deployment`

1. Creación del `Service` y `Deployment` inicial - v1.0

```
k apply -f nginx-service.yml
k apply -f nginx-deployment-v1.yml
k get pods
```

#imagen1

2. Comando utilizado para los pods en tiempo real.

```
watch kubectl get pods -o=custom-columns="NAME:.metadata.name,VERSION:.metadata.labels.version,STATUS:.status.phase"
```

3. Desplegar el `Deployment` con la estrategia `Recreate` y con la segunda versión - v2.0

```
k apply -f nginx-deployment-v2.yml
```

#gif1

4.  Desplegar el `Deployment` con la estrategia `RollingUpdate` y con la tercera versión - v3.0

```
k apply -f nginx-deployment-v3.yml
```

#gif2

5. Rollback a la segunda versión - v2.0

```
k rollout undo deployment nginx-deployment
```

#imagen4
