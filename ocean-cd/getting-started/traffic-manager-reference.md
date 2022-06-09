# Traffic Manager Reference

In the [Migrate Workload](ocean-cd/getting-started/?id=migrate-a-workload-using-the-console) procedure, you can choose a traffic manager in the RolloutSpec configuration, and Ocean CD will configure it automatically.

<img src="/ocean-cd/_media/getting-started-n10.png" width="200" />

This page shows templates for all of the traffic managers that Ocean CD supports. If you would like to use a template instead of the automatic configuration, you can use one of these.

### ALB: Instance Level

```yaml
traffic:
  canaryService: rollouts-demo-canary
  stableService: rollouts-demo-stable
  alb:
    ingress: rollouts-demo-ingress
    servicePort: 80
    rootService: rollouts-demo-root
    stickinessConfig:
      enabled: true
      durationSeconds: 3600
    annotationPrefix: string
```

### ALB: IP Level

```yaml
traffic:
  pingPong:
    pingService: rollouts-demo-canary
    pongService: rollouts-demo-stable
  alb:
    ingress: rollouts-demo-ingress
    servicePort: 80
    rootService: rollouts-demo-root
    stickinessConfig:
      enabled: true
      durationSeconds: 3600
    annotationPrefix: string    
```

### Ambassador

```yaml
traffic:
  canaryService: rollouts-demo-canary
  stableService: rollouts-demo-stable
  ambassador:
    mappings:
    - echo
```

### Istio: Host Level

```yaml
traffic:
  canaryService: rollouts-demo-canary
  stableService: rollouts-demo-stable
  istio:
    virtualServices:
      - name: rollout-vsvc
        routes:
          - primary
```

### Istio: Subset Level

```yaml
traffic:
  stableService: rollouts-demo-stable
  istio:
    virtualServices:
    - name: rollout-vsvc
      routes:
      - primary
    destinationRule:
      name: rollout-destrule
      canarySubsetName: canary
      stableSubsetName: stable
```

### NGINX

```yaml
traffic:
  canaryService: rollouts-demo-stable
  stableService: rollouts-demo-canary
  nginx:
    stableIngress: rollouts-demo-ingress-nginx
    additionalIngressAnnotations:
      canary-by-header: X-Canary
      canary-by-header-value: iwantsit   
```

### SMI

```yaml
traffic:
  canaryService: rollouts-demo-canary
  stableService: rollouts-demo-stable
  smi:
    rootService: rollouts-demo-root
```

### Without Traffic Manager

If a traffic manager is not explicitly configured, Ocean CD by default uses Kubernetes traffic methods based on replicas. You only need to add the service names for the Canary and Stable versions as shown in the template below..

```yaml
traffic:
 stableService: < >
 canaryService: < >
```

## What’s Next?
- To learn more, have a look at the [Ocean CD Public Repository](https://github.com/spotinst/spot-oceancd-releases/tree/main/examples).
- Learn about [viewing the list of rollouts](ocean-cd/tutorials/view-rollouts/) and the information provided in the [detailed rollout page](ocean-cd/tutorials/view-rollouts/detailed-rollout).