# Creating an external S3 data source

In {{ mgp-name }}, you can use [{{ objstorage-full-name }}](../../../storage/index.yaml) or other third-party S3 services as an [external data source](../../concepts/external-tables.md#pxf-data-sources) with the S3 connection type.

To get started, [create a static access key](../../../iam/operations/sa/create-access-key.md). You will need to specify its data in the source parameters.

To create an external S3 data source:

{% list tabs group=instructions %}


* API {#api}

   To add an S3 data source to a {{ mgp-name }} cluster, use the [create](../../api-ref/PXFDatasource/create.md) REST API method for the [PXFDatasource](../../api-ref/PXFDatasource/index.md) resource or the [PXFDatasourceService/Create](../../api-ref/grpc/pxf_service.md#Create) gRPC API call and provide the following in the request:

   * Cluster ID in the `clusterId` parameter. To find out the cluster ID, [get a list of clusters in the folder](../cluster-list.md#list-clusters).
   * Source name in the `name` parameter.
   * External source settings in the `s3` parameter.

{% endlist %}

## Sample REST API request {#example}

The example below shows how to create an external data source for an {{ objstorage-name }} bucket using the {{ mgp-name }} REST API. To create a source:

1. [Get an IAM token](../../../iam/operations/index.md#iam-tokens). It is used for authentication in the API.
1. Add the IAM token to the following environment variable:

   ```bash
   export IAM_TOKEN=<token>
   ```

1. Create a static access key.
1. Send a request using [cURL](https://curl.haxx.se):

   ```bash
   curl --location "https://mdb.api.cloud.yandex.net/managed-greenplum/v1/clusters/<cluster_ID>/pxf_datasources" \
        --header "Content-Type: text/plain" \
        --header "Authorization: Bearer ${IAM_TOKEN}" \
        --data "{
            \"datasource\": {
                \"name\": \"s3:csv\",
                \"s3\": {
                    \"accessKey\": \"<key_ID>\",
                    \"secretKey\": \"<secret_key>\",
                    \"endpoint\": \"{{ s3-storage-host }}\"
                }
            }
       }"
   ```

   In the request body, specify the following parameters:

   * `name`: Source name, e.g., `s3:csv`.
   * `accessKey`: Static access key ID.
   * `secretKey`: Secret key. It is part of the static key.
   * `endpoint`: {{ objstorage-name }} address.

{% include [greenplum-trademark](../../../_includes/mdb/mgp/trademark.md) %}
