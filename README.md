# Custom Resource Definition and Custom Resource syncing example

this example has CRDs from the
[spark-on-k8s-operator](https://github.com/GoogleCloudPlatform/spark-on-k8s-operator)
and instantiates a resource with it, ie the sparkperator, and finally has a job
that gets created in its own namespace, the `acme-datascience-job1`.

in order for this to work, i needed a lot of CPU, so rather than starting the
default node instances, i bumped up the CPUs on them.

