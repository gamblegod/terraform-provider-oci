---
layout: "oci"
page_title: "OCI: oci_core_cpes"
sidebar_current: "docs-oci-datasource-core-cpes"
description: |-
  Provides a list of Cpes
---

# Data Source: oci_core_cpes
The `oci_core_cpes` data source allows access to the list of OCI cpes

Lists the Customer-Premises Equipment objects (CPEs) in the specified compartment.


## Example Usage

```hcl
data "oci_core_cpes" "test_cpes" {
	#Required
	compartment_id = "${var.compartment_id}"
}
```

## Argument Reference

The following arguments are supported:

* `compartment_id` - (Required) The OCID of the compartment.


## Attributes Reference

The following attributes are exported:

* `cpes` - The list of cpes.

### Cpe Reference

The following attributes are exported:

* `compartment_id` - The OCID of the compartment containing the CPE.
* `defined_tags` - Defined tags for this resource. Each key is predefined and scoped to a namespace. For more information, see [Resource Tags](https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm).  Example: `{"Operations.CostCenter": "42"}` 
* `display_name` - A user-friendly name. Does not have to be unique, and it's changeable. Avoid entering confidential information. 
* `freeform_tags` - Free-form tags for this resource. Each tag is a simple key-value pair with no predefined name, type, or namespace. For more information, see [Resource Tags](https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm).  Example: `{"Department": "Finance"}` 
* `id` - The CPE's Oracle ID (OCID).
* `ip_address` - The public IP address of the on-premises router.
* `time_created` - The date and time the CPE was created, in the format defined by RFC3339.  Example: `2016-08-25T21:10:29.600Z` 

