# {{ at-full-name }} event reference

{{ at-name }} supports tracking of management (control plane) events for {{ yq-full-name }}. For more information, see [{#T}](../audit-trails/concepts/format.md).

The general view of the `event_type` field value is as follows:

```text
{{ at-event-prefix }}.audit.yq.<event_name>
```

{% include [yq-events](../_includes/audit-trails/events/yq-events.md) %}