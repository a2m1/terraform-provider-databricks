---
subcategory: "Databricks SQL"
---
# databricks_sql_dashboard Resource

To manage [SQLA resources](https://docs.databricks.com/sql/get-started/concepts.html) you must have `databricks_sql_access` on your [databricks_group](group.md#databricks_sql_access) or [databricks_user](user.md#databricks_sql_access).

**Note:** documentation for this resource is a work in progress.

A dashboard may have one or more [widgets](sql_widget.md).

## Example Usage

```hcl
resource "databricks_sql_dashboard" "d1" {
  name = "My Dashboard Name"

  tags = [
    "some-tag",
    "another-tag",
  ]
}
```

Example [permission](permissions.md) to share dashboard with all users:

```hcl
resource "databricks_permissions" "d1" {
  sql_dashboard_id = databricks_sql_dashboard.d1.id

  access_control {
    group_name       = data.databricks_group.users.display_name
    permission_level = "CAN_RUN"
  }
}
```
