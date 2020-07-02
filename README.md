Python modules to install:
jmespath
openshift
PyYAML

https://docs.ansible.com/ansible/latest/modules/k8s_info_module.html

So far the main playbook, roks_cluster_config.yml, does the following:

- creates some convenience console links on the Application menu
- Installs the latest version of the [IBM Cloud Operator](https://github.com/IBM/cloud-operators)
- Creates a configmap for the IBM Cloud Operator to find the "management" namespace
- Diables the tiles in the Developer Catalog
- Installs the latest version of the Red Hat Service Mesh (including dependent operators)
- Configures the [Service Mesh Control plane](https://docs.openshift.com/container-platform/4.3/service_mesh/service_mesh_install/customizing-installation-ossm.html)
- Creates links for Istio components (Jaeger, Kiali, Grafana) on the Application menu
- Enables [Kubernetes API audit logging](https://cloud.ibm.com/docs/containers?topic=containers-health#webhook_logdna) to LogDNA
- Enables cluster logging with log forwarding to an external server


The playbook is mostly independent of the cluster environment.  It only runs locally using authentication previously established by logging in the `oc` CLI.  It does have one dependent variable configured in the playbook. There is a URL for a cluster-specific dashboard in SysDig; there is no way to look it up inside the cluster or derive it from information inside the cluster.

