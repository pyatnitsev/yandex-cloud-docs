# Creating an external Hive data source

In {{ mgp-name }}, as an [external data source](../../concepts/external-tables.md#pxf-data-sources) with the Hive connection type, you can use a Hive DBMS as part of [{{ dataproc-full-name }}](../../../data-proc/index.yaml) or other third-party Hive services.

To create an external Hive data source:

{% list tabs group=instructions %}


* API {#api}

   To add a Hive data source to a {{ mgp-name }} cluster, use the [create](../../api-ref/PXFDatasource/create.md) REST API method for the [PXFDatasource](../../api-ref/PXFDatasource/index.md) resource or the [PXFDatasourceService/Create](../../api-ref/grpc/pxf_service.md#Create) gRPC API call and provide the following in the request:

   * Cluster ID in the `clusterId` parameter. To find out the cluster ID, [get a list of clusters in the folder](../cluster-list.md#list-clusters).
   * Source name in the `name` parameter.
   * External source settings in the `hive` parameter.

{% endlist %}

## Sample REST API request {#example}

The example below shows how to create an external Hive data source using the {{ mgp-name }} REST API. To create a source:

1. [Get an IAM token](../../../iam/operations/index.md#iam-tokens). It is used for authentication in the API.
1. Add the IAM token to the following environment variable:

   ```bash
   export IAM_TOKEN=<token>
   ```

1. Send a request using [cURL](https://curl.haxx.se):

   ```bash
   curl --location "https://mdb.api.cloud.yandex.net/managed-greenplum/v1/clusters/<cluster_ID>/pxf_datasources" \
       --header "Content-Type: text/plain" \
       --header "Authorization: Bearer ${IAM_TOKEN}" \
       --data "{
           \"datasource\": {
               \"name\": \"hive:text\",
               \"hive\": {
                   \"kerberos\": {
                       \"enable\": true
                   }
               }
           }
       }"
   ```

   In the request body, specify the following parameters:

   * `name`: Source name, e.g., `hive:text`.
   * `enable`: Enabling the [Kerberos](https://ru.wikipedia.org/wiki/Kerberos) protocol for client and server authentication (optional).

{% include [greenplum-trademark](../../../_includes/mdb/mgp/trademark.md) %}
