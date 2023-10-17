### How does {{ datalens-short-name }} find linked objects during migration? {#related-objects-migration}

The service does it recursively across all links. This enables you to start [migration](../../datalens/workbooks-collections/migrations.md) from any object. For example, you can do it from a dashboard. {{ datalens-short-name }} will find all linked charts, datasets, and connections. Then, it will repeat the search for links for each found object. Once finished, the service will prompt you to place all found objects in a [workbook](../../datalens/workbooks-collections/index.md).