## Build

```
$ oc process -f redis-build.yml | oc -n hdhclr-tools apply -f -
```

Do a build.

## Dev

```
$ oc -n hdhclr-tools tag redis-ha:latest redis-ha:dev
$ oc process -f redis-master-deploy.yml --param-file=redis-dev.param | oc -n hdhclr-dev apply -f -
```

Wait for pod with two containers to come up.

```
$ oc process -f redis-sentinel-deploy.yml --param-file=redis-dev.param | oc -n hdhclr-dev apply -f -
$ oc process -f redis-slave-deploy.yml --param-file=redis-dev.param | oc -n hdhclr-dev apply -f -
```

Wait for all pods to come up. Scale down master pod.

## Test

```
$ oc -n hdhclr-tools tag redis-ha:latest redis-ha:test
$ oc process -f redis-master-deploy.yml --param-file=redis-test.param | oc -n hdhclr-test apply -f -
```

Wait for pod with two containers to come up.

```
$ oc process -f redis-sentinel-deploy.yml --param-file=redis-test.param | oc -n hdhclr-test apply -f -
$ oc process -f redis-slave-deploy.yml --param-file=redis-test.param | oc -n hdhclr-test apply -f -
```

Wait for all pods to come up. Scale down master pod.

## Prod

```
$ oc -n hdhclr-tools tag redis-ha:latest redis-ha:prod
$ oc process -f redis-master-deploy.yml --param-file=redis-prod.param | oc -n hdhclr-prod apply -f -
```

Wait for pod with two containers to come up.

```
$ oc process -f redis-sentinel-deploy.yml --param-file=redis-prod.param | oc -n hdhclr-prod apply -f -
$ oc process -f redis-slave-deploy.yml --param-file=redis-prod.param | oc -n hdhclr-prod apply -f -
```

Wait for all pods to come up. Scale down master pod.
