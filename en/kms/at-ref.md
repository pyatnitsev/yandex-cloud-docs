# {{ at-full-name }} event reference

{{ at-name }} supports tracking of [management (control plane) events](../audit-trails/concepts/format.md) and [data (data plane) events](../audit-trails/concepts/format-data-plane.md) for {{ kms-full-name }}.

The general view of the `event_type` field value is as follows:

```text
{{ at-event-prefix }}.audit.kms.<event_name>
```

## Management event reference {#control-plane-events}

{% include [kms-events](../_includes/audit-trails/events/kms-events.md) %}

## Data event reference {#data-plane-events}

{% include [kms-events-dp](../_includes/audit-trails/events/kms-events-dp.md) %}