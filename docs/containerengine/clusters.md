# oci_containerengine_cluster

## Cluster Resource

### Cluster Reference

The following attributes are exported:

* `available_kubernetes_upgrades` - Available Kubernetes versions to which the clusters masters may be upgraded.
* `compartment_id` - The OCID of the compartment in which the cluster exists.
* `endpoints` - Endpoints served up by the cluster masters.
	* `kubernetes` - The Kubernetes API server endpoint.
* `id` - The OCID of the cluster.
* `kubernetes_version` - The version of Kubernetes running on the cluster masters.
* `lifecycle_details` - Details about the state of the cluster masters.
* `metadata` - Metadata about the cluster.
	* `created_by_user_id` - The user who created the cluster.
	* `created_by_work_request_id` - The OCID of the work request which created the cluster.
	* `deleted_by_user_id` - The user who deleted the cluster.
	* `deleted_by_work_request_id` - The OCID of the work request which deleted the cluster.
	* `time_created` - The time the cluster was created.
	* `time_deleted` - The time the cluster was deleted.
	* `time_updated` - The time the cluster was updated.
	* `updated_by_user_id` - The user who updated the cluster.
	* `updated_by_work_request_id` - The OCID of the work request which updated the cluster.
* `name` - The name of the cluster.
* `options` - Optional attributes for the cluster.
	* `add_ons` - Configurable cluster add-ons
		* `is_kubernetes_dashboard_enabled` - Whether or not to enable the Kubernetes Dashboard add-on.
		* `is_tiller_enabled` - Whether or not to enable the Tiller add-on.
	* `kubernetes_network_config` - Network configuration for Kubernetes.
		* `pods_cidr` - The CIDR block for Kubernetes pods.
		* `services_cidr` - The CIDR block for Kubernetes services.
	* `service_lb_subnet_ids` - The OCIDs of the subnets used for Kubernetes services load balancers.
* `state` - The state of the cluster masters.
* `vcn_id` - The OCID of the virtual cloud network (VCN) in which the cluster exists.



### Create Operation
Create a new cluster.

The following arguments are supported:

* `compartment_id` - (Required) The OCID of the compartment in which to create the cluster.
* `kubernetes_version` - (Required) The version of Kubernetes to install into the cluster masters.
* `name` - (Required) The name of the cluster. Avoid entering confidential information.
* `options` - (Optional) Optional attributes for the cluster.
	* `add_ons` - (Optional) Configurable cluster add-ons
		* `is_kubernetes_dashboard_enabled` - (Optional) Whether or not to enable the Kubernetes Dashboard add-on.
		* `is_tiller_enabled` - (Optional) Whether or not to enable the Tiller add-on.
	* `kubernetes_network_config` - (Optional) Network configuration for Kubernetes.
		* `pods_cidr` - (Optional) The CIDR block for Kubernetes pods.
		* `services_cidr` - (Optional) The CIDR block for Kubernetes services.
	* `service_lb_subnet_ids` - (Optional) The OCIDs of the subnets used for Kubernetes services load balancers.
* `vcn_id` - (Required) The OCID of the virtual cloud network (VCN) in which to create the cluster.


### Update Operation
Update the details of a cluster.

The following arguments support updates:
* `kubernetes_version` - The version of Kubernetes to install into the cluster masters.
* `name` - The name of the cluster. Avoid entering confidential information.


** IMPORTANT **
Any change to a property that does not support update will force the destruction and recreation of the resource with the new property values

### Example Usage

```hcl
resource "oci_containerengine_cluster" "test_cluster" {
	#Required
	compartment_id = "${var.compartment_id}"
	kubernetes_version = "${var.cluster_kubernetes_version}"
	name = "${var.cluster_name}"
	vcn_id = "${oci_containerengine_vcn.test_vcn.id}"

	#Optional
	options {

		#Optional
		add_ons {

			#Optional
			is_kubernetes_dashboard_enabled = "${var.cluster_options_add_ons_is_kubernetes_dashboard_enabled}"
			is_tiller_enabled = "${var.cluster_options_add_ons_is_tiller_enabled}"
		}
		kubernetes_network_config {

			#Optional
			pods_cidr = "${var.cluster_options_kubernetes_network_config_pods_cidr}"
			services_cidr = "${var.cluster_options_kubernetes_network_config_services_cidr}"
		}
		service_lb_subnet_ids = "${var.cluster_options_service_lb_subnet_ids}"
	}
}
```

# oci_containerengine_clusters

## Cluster DataSource

Gets a list of clusters.

### List Operation
List all the cluster objects in a compartment.
The following arguments are supported:

* `compartment_id` - (Required) The OCID of the compartment.
* `name` - (Optional) The name to filter on.
* `state` - (Optional) A cluster lifecycle state to filter on. Can have multiple parameters of this name.


The following attributes are exported:

* `clusters` - The list of clusters.

### Example Usage

```hcl
data "oci_containerengine_clusters" "test_clusters" {
	#Required
	compartment_id = "${var.compartment_id}"

	#Optional
	name = "${var.cluster_name}"
	state = "${var.cluster_state}"
}
```