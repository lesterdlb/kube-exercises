# answer_exercise_1

## Blue Green Deployment

1. Creación del `Service` y `Deployment` inicial - v1.0

```
k apply -f nginx-service.yml
k apply -f nginx-blue-version.yml
```

2. Creación del `Deployment` con la segunda version - v2.0

```
k apply -f nginx-green-version.yml
```

3. Cambiar mediante el comando `Patch` el selector del servicio de la versión v1.0 a la versión v2.0

```
k describe service nginx-service | grep Selector
k patch service nginx-service -p '{"spec":{"selector":{"version": "v2.0"}}}
k describe service nginx-service | grep Selector
```

#gif
