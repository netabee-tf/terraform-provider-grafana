---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_organization Resource - terraform-provider-grafana"
subcategory: "Grafana OSS"
description: |-
  Official documentation https://grafana.com/docs/grafana/latest/administration/organization-management/HTTP API https://grafana.com/docs/grafana/latest/developers/http_api/org/
  This resource represents an instance-scoped resource and uses Grafana's admin APIs.
  It does not work with API tokens or service accounts which are org-scoped.
  You must use basic auth.
---

# grafana_organization (Resource)

* [Official documentation](https://grafana.com/docs/grafana/latest/administration/organization-management/)
* [HTTP API](https://grafana.com/docs/grafana/latest/developers/http_api/org/)

This resource represents an instance-scoped resource and uses Grafana's admin APIs.
It does not work with API tokens or service accounts which are org-scoped. 
You must use basic auth.

## Example Usage

```terraform
resource "grafana_organization" "test" {
  name         = "Test Organization"
  admin_user   = "admin"
  create_users = true
  admins = [
    "admin@example.com"
  ]
  editors = [
    "editor-01@example.com",
    "editor-02@example.com"
  ]
  viewers = [
    "viewer-01@example.com",
    "viewer-02@example.com"
  ]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) The display name for the Grafana organization created.

### Optional

- `admin_user` (String) The login name of the configured default admin user for the Grafana
installation. If unset, this value defaults to admin, the Grafana default.
Grafana adds the default admin user to all organizations automatically upon
creation, and this parameter keeps Terraform from removing it from
organizations.
 Defaults to `admin`.
- `admins` (Set of String) A list of email addresses corresponding to users who should be given admin
access to the organization. Note: users specified here must already exist in
Grafana unless 'create_users' is set to true.
- `create_users` (Boolean) Whether or not to create Grafana users specified in the organization's
membership if they don't already exist in Grafana. If unspecified, this
parameter defaults to true, creating placeholder users with the name, login,
and email set to the email of the user, and a random password. Setting this
option to false will cause an error to be thrown for any users that do not
already exist in Grafana.
 Defaults to `true`.
- `editors` (Set of String) A list of email addresses corresponding to users who should be given editor
access to the organization. Note: users specified here must already exist in
Grafana unless 'create_users' is set to true.
- `viewers` (Set of String) A list of email addresses corresponding to users who should be given viewer
access to the organization. Note: users specified here must already exist in
Grafana unless 'create_users' is set to true.

### Read-Only

- `id` (String) The ID of this resource.
- `org_id` (Number) The organization id assigned to this organization by Grafana.

## Import

Import is supported using the following syntax:

```shell
terraform import grafana_organization.org_name {{org_id}}
```
