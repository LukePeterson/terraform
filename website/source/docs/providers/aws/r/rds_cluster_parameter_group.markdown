---
layout: "aws"
page_title: "AWS: aws_rds_cluster_parameter_group"
sidebar_current: "docs-aws-resource-rds-cluster-parameter-group"
---

# aws\_rds\_cluster\_parameter\_group

Provides an RDS DB cluster parameter group resource.

## Example Usage

```
resource "aws_rds_cluster_parameter_group" "default" {
    name = "rds-cluster-pg"
    family = "aurora5.6"
    description = "RDS default cluster parameter group"

    parameter {
      name = "character_set_server"
      value = "utf8"
    }

    parameter {
      name = "character_set_client"
      value = "utf8"
    }
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the DB cluster parameter group.
* `family` - (Required) The family of the DB cluster parameter group.
* `description` - (Required) The description of the DB cluster parameter group.
* `parameter` - (Optional) A list of DB parameters to apply.
* `tags` - (Optional) A mapping of tags to assign to the resource.

Parameter blocks support the following:

* `name` - (Required) The name of the DB parameter.
* `value` - (Required) The value of the DB parameter.
* `apply_method` - (Optional) "immediate" (default), or "pending-reboot". Some
    engines can't apply some parameters without a reboot, and you will need to
    specify "pending-reboot" here.

## Attributes Reference

The following attributes are exported:

* `id` - The db cluster parameter group name.
* `arn` - The ARN of the db cluster parameter group.


## Import

Redshift Clusters can be imported using the `name`, e.g. 

```
$ terraform import aws_rds_cluster_parameter_group.cluster_pg production-pg-1
```