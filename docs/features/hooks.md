# Hooks

Hooks will post comment on that event. All hooks are described below:

| Hook | Description | 
|:----|:----|
| `when_add_or_update_only`  | When there are no destroys.  | 
| `when_destroy`  |  When there are destroys. |
| `when_no_changes` | When there are no changes. | 
| `when_plan_error` | When there are errors in plans |


## Configurable Actions

You can either add a label or post comments. Details will be describe in the next section.

## How to configure

Configure under `terraform.(fmt|plan|apply)` as below:

```yaml
...
terraform:
    ...
    plan:
        template: |
            ...
        when_add_or_update_only:
            label: "terraform/changes"
        when_destroy:
            label: "terraform/destroy"
            template: |
                ## :warning: WARNING: Resource Deletion will happen :warning:
                This plan contains **resource deletion**. Please check the plan result very carefully!
        when_no_changes:
            label: "terraform/no-changes"
        when_plan_error:
            label: "terraform/error"
```

In most common cases, platform teams wants to alert the developers if there are destroys. It will help feedback developers for unexpected changes.
