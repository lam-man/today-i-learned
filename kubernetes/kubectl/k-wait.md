# kubectl wait

There are many scenarios we want to check certain conditions on the resources of a k8s cluster. For example, some script can only proceed after certain pods get started and `status.phase` is running. It could be the oppsite that we need to wait until certain resources got deleted. It turns out `kubectl wait` is a great fit for many scenarios like above. This notes is a brief introduction on the usage of `kubectl wait`.

