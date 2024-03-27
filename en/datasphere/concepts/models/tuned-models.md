---
title: "What fine-tuned foundation models in {{ ml-platform-full-name }} are"
---

# Fine-tuned foundation models

{{ ml-platform-full-name }} allows you to tune [foundation models](./foundation-models.md) on your own examples to make them more tailored to the specifics of your tasks. Tuning is based on the Fine-tuning method. You can send requests to a fine-tuned model through the {{ ml-platform-name }} Playground interface or through the API using code.

{% note info %}

Foundation model tuning is at the [Preview](../../../overview/concepts/launch-stages.md) stage.

{% endnote %}

## Information about fine-tuned foundation models as a resource {#info}

The following information is stored about each fine-tuned model:

* Name and description.
* Status.
* Foundation model.
* Learning rate.
* Name of the user who tuned the model.
* Data required for tuning.
* Model tuning date in [UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) format, e.g., `Nov 2, 2023, 17:39`.

To get information about models tuned in a project:

1. {% include [find project](../../../_includes/datasphere/ui-find-project.md) %}
1. In the list of available project resources, select **{{ ui-key.yc-ui-datasphere.common.models }}**.
1. In the **{{ ui-key.yc-ui-datasphere.common.projects-resources }}** tab, select **{{ ui-key.yc-ui-datasphere.common.tuned-foundation-models }}**.

## Visibility scope of fine-tuned foundation models {#scope}

A fine-tuned model is a project resource. A community administrator can share fine-tuned models with other community projects by granting access to them in the **{{ ui-key.yc-ui-datasphere.common.access }}** tab on the model viewing page.

#### See also {#see-also}

* [{{ yagpt-full-name }} model tuning](../../tutorials/yagpt-tuning.md)
* [Foundation models](foundation-models.md)