# Дневник проекта

### Шаг 1. Подготовка репозитория

- создан публичный репозиторий https://github.com/Nelochka34/k8s-self-managed-platform
- создана структура каталогов
- добавлены readme.md, .gitignore

### Шаг 2. Развертывание инфраструктуры

- создан документ [Архитектура платформы](docs/architecture.md)
- создан документ [Inventory](infrastructure/inventory.md)

Созданы ВМ: 
```bash
yc compute instance list
+----------------------+----------+---------------+---------+----------------+-------------+
|          ID          |   NAME   |    ZONE ID    | STATUS  |  EXTERNAL IP   | INTERNAL IP |
+----------------------+----------+---------------+---------+----------------+-------------+
| epdaiubo5n77geq3h8pf | cp-1     | ru-central1-b | RUNNING | 84.252.140.51  | 10.129.0.21 |
| epdblrrfdudu8droddmg | worker-2 | ru-central1-b | RUNNING | 111.88.151.83  | 10.129.0.17 |
| epdcjchae4sltn8qnppv | cp-3     | ru-central1-b | RUNNING | 84.201.143.60  | 10.129.0.3  |
| epdmepbn47haur655uoo | worker-1 | ru-central1-b | RUNNING | 89.169.188.52  | 10.129.0.8  |
| epdotjuvdum847p6s188 | cp-2     | ru-central1-b | RUNNING | 89.169.178.122 | 10.129.0.26 |
+----------------------+----------+---------------+---------+----------------+-------------+
```
Подготовлен inventory-файл для HA-кластера:
- 3 control-plane узла;
- 3 etcd узла;
- 2 worker узла.

Проверка: 
```bash
ansible -i inventory/k8s-platform/inventory.ini all -m ping
```
Подготавливаю и настраиваю Kubespray перед установкой: 
- открыла главный конфиг: nano inventory/k8s-platform/group_vars/k8s_cluster/k8s-cluster.yml
- задала там: 
```bash
container_manager: containerd
kube_network_plugin: calico

kube_proxy_mode: iptables

kube_pods_subnet: 10.233.64.0/18
kube_service_addresses: 10.233.0.0/18
```
