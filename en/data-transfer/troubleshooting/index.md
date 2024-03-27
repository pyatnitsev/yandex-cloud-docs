# Troubleshooting in {{ data-transfer-name }}

This section describes typical problems that may arise during [transfer](../concepts/index.md#transfer) [activation](../operations/transfer.md#activate) or operation, and the relevant solutions.

* [{#T}](#overview)
* [{#T}](#common)
* [{#T}](#data-transform)
* [{#T}](#api)
* [{#T}](#network)
* [{#T}](#clickhouse)
* [{#T}](#elasticsearch)
* [{#T}](#mongodb)
* [{#T}](#mysql)
* [{#T}](#opensearch)
* [{#T}](#postgresql)
* [{#T}](#ydb)
* [{#T}](#yds)
* [{#T}](#support)

## Problems that arise when working with {{ data-transfer-name }} {#overview}
To detect a problem in time:

1. Monitor the transfer state on the **{{ ui-key.yacloud.data-transfer.label_monitoring }}** tab of the transfer management page or in [{{ monitoring-full-name }}](../../monitoring/concepts/index.md).
1. [Configure alerts](../operations/monitoring.md#monitoring-integration) in {{ monitoring-full-name }} to receive notifications about transfer failures.
1. [Request](../../support/request.md) records about your resources from {{ yandex-cloud }} service logs.
1. Use the {{ yandex-cloud }} [mobile app](/mobile-app) to track the state of transfers.

If {{ data-transfer-name }} operation was disrupted during data transfer, try to localize and analyze the problem. You may find certain solutions in this article or other sections of our documentation.

| Issue source | Issue | Solution |
|-----------------------|-------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Endpoint | Lack of network accessibility or endpoint access permissions | Check the source read operations using the following charts: [Maximum data transfer delay](../operations/monitoring.md#sinker.pusher.time.row_max_lag_sec), [Number of source events](../operations/monitoring.md#publisher.data.changeitems), and [Reads](../operations/monitoring.md#publisher.data.bytes).</br>Check the target write operations using the following charts: [Maximum data transfer delay](../operations/monitoring.md#sinker.pusher.time.row_max_lag_sec), [Number of source events](../operations/monitoring.md#publisher.data.changeitems), [Number of target events](../operations/monitoring.md#sinker.pusher.data.changeitems), and [Reads](../operations/monitoring.md#publisher.data.bytes).</br>If the data is being read and written, check the [restrictions on working with the DBMS](../operations/transfer.md).</br>Check the requirements for [preparing](../operations/prepare.md) and [configuring](../operations/index.md) the endpoint.</br>Look for a ready-made [solution to the problem](#common). |
| Endpoint or transfer | Lack of physical resources for the transfer or endpoints | If the data is being read and written, check whether there are enough physical resources on the [CPU](../operations/monitoring.md#proc.cpu%7Cproc.guarantee.cpu) and [RAM](../operations/monitoring.md#proc.ram%7Cproc.guarantee.mem) charts.</br>Check out the recommendations for DBMS diagnostics. For example, [{{ MY }}](../../managed-mysql/operations/performance-diagnostics.md), [{{ MG }}](../../managed-mongodb/operations/performance-diagnostics.md), or [{{ PG }}](../../managed-postgresql/operations/performance-diagnostics.md). |
| Data | Outdated data due to changes in the data schema | See the different data transfer scenarios in the [{{ data-transfer-name }} Tutorials](../tutorials/index.md) section. |
| Data | Outdated data due to large data volume | Increase the number of workers for [parallel copying](../concepts/sharded.md) or [replication](../operations/transfer.md#create).</br>Split the tables into several transfers. |

After solving the problem, depending on the status of the transfer, activate it or change the data transfer limits of the running transfer.

![image](../../_assets/data-transfer/restore-transfer.svg)

## General {#common}

{% include [long-time](../../_includes/data-transfer/troubles/long-time.md) %}

{% include [increment-copy](../../_includes/data-transfer/troubles/increment-copy.md) %}

{% include [duplicates](../../_includes/data-transfer/troubles/duplicates.md) %}

{% include [insufficiency-resources](../../_includes/data-transfer/troubles/insufficiency-resources.md) %}

{% include [permission-denied](../../_includes/data-transfer/troubles/permission-denied.md) %}


{% include [required-role](../../_includes/data-transfer/troubles/required-roles.md) %}


## Data transformation {#data-transform}

{% include [required-role](../../_includes/data-transfer/troubles/data-transformation/filtr-append-only-sources.md) %}

## API errors {#api}

Error example:

```text
{"code": 13, "message": "internal"}
```

**Solution**: Contact [support]({{ link-console-support }}) or your account manager and specify the `request_id`. If you are using `curl` for API calls, add the `-v` flag to facilitate error diagnostics.

## Network {#network}

{% include [common-network](../../_includes/data-transfer/troubles/network/common-network.md) %}

{% include [ip-collision](../../_includes/data-transfer/troubles/network/ip-collision.md) %}

{% include [subnet-without-nat](../../_includes/data-transfer/troubles/network/subnet-without-nat.md) %}

{% include [blocked-ip](../../_includes/data-transfer/troubles/network/blocked-ip.md) %}

{% include [transfer-error](../../_includes/data-transfer/troubles/network/transfer-error.md) %}


## {{ CH }} {#clickhouse}

{% include [no-new-tables](../../_includes/data-transfer/troubles/no-new-tables.md) %}

{% include [no-new-tables](../../_includes/data-transfer/troubles/table-names.md) %}

## {{ ES }} {#elasticsearch}

{% include [ambiguous-object-resolution-es](../../_includes/data-transfer/troubles/elastic-opensearch/ambiguous-object-resolution-es.md) %}

{% include [duplication](../../_includes/data-transfer/troubles/elastic-opensearch/duplication.md) %}

## {{ MG }} {#mongodb}

{% include [string-size](../../_includes/data-transfer/troubles/mongodb/string-size.md) %}

{% include [object-size](../../_includes/data-transfer/troubles/mongodb/object-size.md) %}

{% include [no-tables](../../_includes/data-transfer/troubles/mongodb/no-tables.md) %}

{% include [sharded](../../_includes/data-transfer/troubles/mongodb/sharded.md) %}

{% include [timeseries](../../_includes/data-transfer/troubles/mongodb/timeseries.md) %}

{% include [cluster configuration](../../_includes/data-transfer/troubles/mongodb/cluster-configuration.md) %}

## {{ MY }} {#mysql}

{% include [binlog-size](../../_includes/data-transfer/troubles/mysql/binlog-size.md) %}

{% include [no-new-tables](../../_includes/data-transfer/troubles/no-new-tables.md) %}

{% include [aws-binlog-time](../../_includes/data-transfer/troubles/mysql/aws-binlog-time.md) %}

{% include [primary-keys](../../_includes/data-transfer/troubles/primary-keys.md) %}

{% include [binlog-bytes](../../_includes/data-transfer/troubles/mysql/binlog-bytes.md) %}

{% include [drop-table-error](../../_includes/data-transfer/troubles/drop-table-error.md) %}

{% include [timezone-shift](../../_includes/data-transfer/troubles/mysql/timezone-shift.md) %}

## {{ OS }} {#opensearch}

{% include [ambiguous-object-resolution-os](../../_includes/data-transfer/troubles/elastic-opensearch/ambiguous-object-resolution-os.md) %}

{% include [duplication](../../_includes/data-transfer/troubles/elastic-opensearch/duplication.md) %}

## {{ PG }} {#postgresql}

{% include [master-trans-stop](../../_includes/data-transfer/troubles/postgresql/master-trans-stop.md) %}

{% include [conn-duration-quota](../../_includes/data-transfer/troubles/postgresql/conn-duration-quota.md) %}

{% include [view](../../_includes/data-transfer/troubles/postgresql/view.md) %}

{% include [constraint](../../_includes/data-transfer/troubles/postgresql/constraint.md) %}

{% include [schema](../../_includes/data-transfer/troubles/postgresql/schema.md) %}

{% include [low-speed](../../_includes/data-transfer/troubles/postgresql/low-speed.md) %}

{% include [successor-tables](../../_includes/data-transfer/troubles/postgresql/successor-tables.md) %}

{% include [replication-slots](../../_includes/data-transfer/troubles/postgresql/replication-slots.md) %}

{% include [no-data-transfer](../../_includes/data-transfer/troubles/postgresql/no-data-transfer.md) %}

{% include [master-change](../../_includes/data-transfer/troubles/postgresql/master-change.md) %}

{% include [inner-tables](../../_includes/data-transfer/troubles/postgresql/inner-tables.md) %}

{% include [deferrable-tables](../../_includes/data-transfer/troubles/postgresql/deferrable-constraints.md) %}

{% include [lock-replication](../../_includes/data-transfer/troubles/postgresql/lock-replication.md) %}

{% include [excessive-wal](../../_includes/data-transfer/troubles/postgresql/excessive-wal.md) %}

{% include [external-replication](../../_includes/data-transfer/troubles/postgresql/external-replication.md) %}

{% include [primary-keys](../../_includes/data-transfer/troubles/primary-keys.md) %}

{% include [drop-table-error](../../_includes/data-transfer/troubles/drop-table-error.md) %}


## {{ ydb-full-name }} {#ydb}

{% include [overloaded](../../_includes/data-transfer/troubles/overloaded.md) %}

## {{ yds-full-name }} {#yds}

{% include [overloaded](../../_includes/data-transfer/troubles/overloaded.md) %}

{% include [redirects](../../_includes/data-transfer/troubles/data-streams/data-streams-redirects.md) %}



## How to report a problem {#support}

If you followed the tips provided but the problem persists, contact [tech support]({{ link-console-support }}).

{% include [clickhouse-disclaimer](../../_includes/clickhouse-disclaimer.md) %}
