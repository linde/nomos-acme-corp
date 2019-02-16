# GKE Policy Management Directory

This is the root directory for GKE Policy Management for your cluster.

* See [system/](system/README.md) for system configuration.
* See [cluster/](cluster/README.md) for cluster-scoped resources.
* See [namespaces/](namespaces/README.md) for namespace-scoped resources.


# Cluster config content

This particular cluster is the CSP Config Manager take on the kubernetes'
[Deploying WordPress and MySQL with Persistent Volumes wordpress/persistance
mysql
example](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)
example. In this, we sync a flattened yaml from the example and deploy it into a
set of namespaces configured for the cluster.

# Installation

Install this by getting and configuring the [nomos-operator](#) and applying the
[nomos instance yaml](../nomos.yaml). once the system has had a chance to notice
changes and apply the config, you will have an new wordpress installation in
each namespace below the [wp-bundle-sync.yaml](namespaces/wp-bundle-sync.yaml)
file.

# Verification

To verify this, use the
[kubectl proxy](https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/#directly-accessing-the-rest-api) as follows below. We used the proxy to demonstrate access to the services
in order to conserve resources and avoid having external access to the
unconfigured/unsecured wordpress installations.

* First, run the proxy on your console where you've been apply kubectl `$
  kubectl proxy` and leave this running or put it in the background.

* access the proxy to make sure it works. For example, try this link to see the
  [services in the acme-dev
  namespace](http://localhost:8001/api/v1/namespaces/acme-dev/services/)
  
* to see this namespaces particular wordpress installation, try the [the
  wordpress service and port for acme-dev
  namespace](http://localhost:8001/api/v1/namespaces/acme-dev/services/wordpress:80/proxy/). This
  should redirect you to the config page to pick a locale and continue setting
  up that namespaces blog.
  
  
# Next steps

Try to add a new namespace and verify it gets the wordpress resources sync'ed to
it...







