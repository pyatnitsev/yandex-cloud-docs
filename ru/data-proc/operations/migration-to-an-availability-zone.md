# Миграция кластера {{ dataproc-name }} в другую зону доступности

Подкластеры каждого кластера {{ dataproc-name }} находятся в одной [облачной сети](../../vpc/concepts/network.md#network) и одной [зоне доступности](../../overview/concepts/geo-scope.md). Подкластеры можно перенести из одной зоны в другую — так производится миграция кластера.

{% note info %}

Перенести в другую зону доступности можно только [легковесные кластеры](../concepts/index.md#light-weight-clusters). Миграция кластеров с сервисом HDFS и кластеров {{ metastore-full-name }} пока недоступна. Кластеры с HDFS или кластеры {{ metastore-name }} из зоны доступности `{{ region-id }}-c` техническая поддержка перенесет вручную, предупредив об этом их владельцев.

{% endnote %}

Чтобы перенести подкластеры {{ dataproc-name }} в другую зону доступности:

1. Убедитесь, что в вашей сети [настроены группы безопасности](cluster-create.md#change-security-groups).
1. [Создайте подсеть](../../vpc/operations/subnet-create.md) в зоне доступности, в которую вы переносите подкластеры.
1. [Настройте NAT-шлюз и привяжите таблицу маршрутизации](../../vpc/operations/create-nat-gateway.md) к новой подсети.
1. [Создайте кластер](cluster-create.md#create) в нужной зоне доступности.
1. [Удалите кластер](cluster-delete.md) в первоначальной зоне.

{% include [zone-d-host-restrictions](../../_includes/mdb/ru-central1-d-broadwell.md) %}