## Kubernetes

## Howto connect to K8S dashboard in your local Docker Engine

1. Docker -> Settings -> Kubernetes -> Enable Kubernetes [Apply]
2. Open a command prompt and enter `kubectl describe secret`
3. Copy token
4. `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.4.0/aio/deploy/recommended.yaml`
5. `kubectl proxy`
6. `Goto [Kubernetes Dashboard Login](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login)
7. Choose Token in Kubernetes dashboard and paste in token

--------------------------------------------------------------------------------------------------------------

### Kubernetes log, User "system:serviceaccount:default:default" cannot get services in the namespace

#### create a file rbac.yaml

**DO NOT USE THIS IN PRODUCTION SETTINGS**

```bash
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: rbac
subjects:
  - kind: ServiceAccount
    # Reference to upper's `metadata.name`
    name: default
    # Reference to upper's `metadata.namespace`
    namespace: default
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
```

### Apply

```bash
kubectl apply -f rbac.yaml
```

### Delete

```bash
kubectl delete -f rbac.yaml
```

--------------------------------------------------------------------------------------------------------------

### Kubectl Commands

#### View raw content of K8S config file

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl config view --raw`                                                                     | view raw content of K8S config file                          |

#### Switch context

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl config use-context <cluster-name>`                                                     | set context to specified cluster                             |

#### Nodes

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl get nodes`                                                                             | get nodes                                                    |

#### Pods

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl get pods`                                                                              | get pods                                                     |
|`kubectl get pods --all-namespaces`                                                             | get all pods in all namespaces                               |

#### Deployments

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl apply -f deployment.yaml`                                                              | deploy to kubernetes cluster                                 |
|`kubectl get deployments`                                                                       | get deployments of a kubernetes cluster                      |
|`kubectl delete deployment <deployment-name>`                                                   | delete a deployment by name                                  |

#### Services

| Command                                                                                        | Action                                                       |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|`kubectl get services`                                                                          | get services in a kubernetes cluster                         |
|`kubectl delete svc <service-name>`                                                             | delete a service by name                                     |
|`kubectl get pods`                                                                              | get pods                                                     |