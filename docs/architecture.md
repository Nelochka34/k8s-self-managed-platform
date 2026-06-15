# Архитектура платформы

## Описание узлов: 
- cp-1      control-plane + etcd
- cp-2      control-plane + etcd
- cp-3      control-plane + etcd
- worker-1  worker
- worker-2  worker


 ## Компоненты платформы: 
    ### Kubernetes
    - Kubespray
    - Kubernetes
    - Containerd

    ### Ingress 
    - ingress-nginx

    ### Мониторинг
    - Prometeus 
    - Grafana
    - Alertmanaget

    ### Логирование
    - Loki
    - Vector

    ### GitOps
    - ArgoCD

    ### Test application
    - Online Boutique

    ### CI/CD 
    - GitLab CI


```mermaid
graph TD

Users --> IngressNginx[ingress-nginx]

IngressNginx --> OnlineBoutique[Online Boutique]

ArgoCD --> Kubernetes[Kubernetes Cluster]

GitLabCI[GitLab CI] --> Registry[Container Registry]
Registry --> ArgoCD

Prometheus --> Grafana
Prometheus --> Alertmanager

Vector --> Loki
OnlineBoutique --> Vector
Kubernetes --> Vector

CP1[control-plane-1 + etcd]
CP2[control-plane-2 + etcd]
CP3[control-plane-3 + etcd]

W1[worker-1]
W2[worker-2]

Kubernetes --> CP1
Kubernetes --> CP2
Kubernetes --> CP3
Kubernetes --> W1
Kubernetes --> W2
```
