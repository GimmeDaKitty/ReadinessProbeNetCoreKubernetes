# ReadinessProbeNetCoreKubernetes
Example for livenes probes as contained in this article: https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/health-checks?view=aspnetcore-7.0

## How to run in kubernetes
You can test this in a real kubernetes cluster or using [KiND](https://kind.sigs.k8s.io/).

First, create the docker image of the application using the provided dockerfile.
To do so, open a command line window on the location of the docker file and type:

`docker build -t readinessprobeexample:1.0.0 .`

To deploy the containerized application on a KiND cluster:

``` 
kind create cluster
kind load docker-image readinessprobeexample:1.0.0
kubectl -f myapp.yaml
```

You can watch the pods being in state Running (liveness probe) but Not Ready (readiness probe) for a while until the readiness probe returns result OK

![image](https://github.com/GimmeDaKitty/ReadinessProbeNetCoreKubernetes/assets/46991222/a84a15f1-4b30-422d-903c-e0bb2d8c8889)

