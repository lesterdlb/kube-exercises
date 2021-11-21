# answer_exercise_4

## Creación de un objeto `Deployment`

1. Creación del `Service` y `Deployment` inicial - v1.0

```
k apply -f nginx-service.yml
k apply -f nginx-deployment-v1.yml
k get pods
```

![Respuesta 4 - 1](https://user-images.githubusercontent.com/10359307/142750866-a1ea4f7f-a8a2-48b3-94cd-d5cb88d7d838.png)

2. Comando utilizado para los pods en tiempo real.

```
watch kubectl get pods -o=custom-columns="NAME:.metadata.name,VERSION:.metadata.labels.version,STATUS:.status.phase"
```

3. Desplegar el `Deployment` con la estrategia `Recreate` y con la segunda versión - v2.0

```
k apply -f nginx-deployment-v2.yml
```

![Respuesta 4 - 2](https://user-images.githubusercontent.com/10359307/142750873-80392ac6-456e-4d89-8c1e-b30a0da3d3fd.gif)

4.  Desplegar el `Deployment` con la estrategia `RollingUpdate` y con la tercera versión - v3.0

```
k apply -f nginx-deployment-v3.yml
```

![Respuesta 4 - 3](https://user-images.githubusercontent.com/10359307/142750878-ad6814fe-9373-4e8e-9c0c-8b6b7bdc473b.gif)

5. Rollback a la segunda versión - v2.0

```
k rollout undo deployment nginx-deployment
```

![Respuesta 4 - 4](https://user-images.githubusercontent.com/10359307/142750881-5a8c7127-3383-4588-9182-93a5823c28f4.png)
