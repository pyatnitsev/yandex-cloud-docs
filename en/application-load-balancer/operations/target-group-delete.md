---
title: "Deleting a target group from an application load balancer"
description: "To delete a target group, in the management console, select the folder that hosts the target group. Select {{ alb-full-name }}. In the left-hand menu, select Target groups. Select the target group and click the select icon. In the menu that opens, select Delete. To do this with multiple groups, select the groups to delete from the list and click Delete at the bottom of the screen."
---

# Deleting an {{ alb-name }} target group

{% note warning %}

{% include [target-group-deletion-restriction](../../_includes/application-load-balancer/target-group-deletion-restriction.md) %}

{% endnote %}

To delete a [target group](../concepts/target-group.md):

{% list tabs group=instructions %}

- Management console {#console}

   1. In the [management console]({{ link-console-main }}), select the [folder](../../resource-manager/concepts/resources-hierarchy.md#folder) where the target group was created.
   1. Select **{{ ui-key.yacloud.iam.folder.dashboard.label_application-load-balancer }}**.
   1. In the left-hand panel, select ![image](../../_assets/console-icons/target.svg) **{{ ui-key.yacloud.alb.label_target-groups }}**.
   1. Select the target group and click ![image](../../_assets/console-icons/ellipsis.svg).
   1. In the menu that opens, select **{{ ui-key.yacloud.common.delete }}**.

      To do this with multiple groups, select the groups to delete from the list and click **{{ ui-key.yacloud.common.delete }}** at the bottom of the screen.
   1. In the window that opens, click **{{ ui-key.yacloud.common.delete }}**.

- CLI {#cli}

   {% include [cli-install](../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../_includes/default-catalogue.md) %}

   1. See the description of the [CLI](../../cli/) command to delete a target group:

      ```bash
      yc alb target-group delete --help
      ```

   1. Run this command:

      ```bash
      yc alb target-group delete <target_group_name_or_ID>
      ```

      To check the deletion, get a list of target groups by running the command:

      ```bash
      yc alb target-group list
      ```

- {{ TF }} {#tf}

   {% include [terraform-definition](../../_tutorials/_tutorials_includes/terraform-definition.md) %}

   {% include [terraform-install](../../_includes/terraform-install.md) %}

   1. Open the {{ TF }} configuration file and delete the fragment with the target group description.

      Sample target group description in the {{ TF }} configuration:

      ```hcl
      resource "yandex_alb_target_group" "foo" {
        name           = "<target_group_name>"

        target {
          subnet_id    = "<subnet_ID>"
          ip_address   = "<VM_1_internal_IP_address>"
        }

        target {
          subnet_id    = "<subnet_ID>"
          ip_address   = "<VM_2_internal_IP_address>"
        }

        target {
          subnet_id    = "<subnet_ID>"
          ip_address   = "<VM_3_internal_IP_address>"
        }
      }
      ```

      For more information about the `yandex_alb_target_group` resource parameters, see the [{{ TF }} provider documentation]({{ tf-provider-alb-targetgroup }}).
   1. Apply the changes:

      {% include [terraform-validate-plan-apply](../../_tutorials/_tutorials_includes/terraform-validate-plan-apply.md) %}

      You can check the target group update in the [management console]({{ link-console-main }}) or using this [CLI](../../cli/) command:

      ```bash
      yc alb target-group list
      ```

- API {#api}

   Use the [delete](../api-ref/TargetGroup/delete.md) REST API method for the [TargetGroup](../api-ref/TargetGroup/index.md) resource or the [TargetGroupService/Delete](../api-ref/grpc/target_group_service.md#Delete) gRPC API call.

{% endlist %}