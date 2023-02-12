# Helm Lab1

1- Add bitnami helm chart repository in the controlplane node.

```helm repo add bitnami https://charts.bitnami.com/bitnami```

![add repo](./images-results/add-repo.png)

2- Deploy the Apache application on the cluster using the apache from the bitnami repository. Set the release Name to: amaze-surf

``` helm install amaze-surf bitnami/apache ```

![install apache](./images-results/install-apache.png)

![install apache2](./images-results/install-apache-2.png)

3- Uninstall the apache chart release  from the cluster

``` helm uninstall amaze-surf ```

![uninstall apache](./images-results/uninstall-apache.png)

4- install specfic version of nginx 1.22.0, then update it to specfic 1.23.1, then rollback

```bash
helm search repo nginx --versions
#then search for app version 1.22.0 and get the chart version
helm install my-nginx bitnami/nginx --version 12.0.6
#to update
helm upgrade my-nginx bitnami/nginx --version 13.2.10
#and to rollback
helm rollback my-nginx
# and to roll back to a specific revision
helm rollback my-nginx [#Revision]
```

![search repo](./images-results/search-repo.png)

![install nginx](./images-results/install-nginx-specific-version.png)

![upgrade nginx](./images-results/upgrade-nginx.png)

![rollback apache](./images-results/rollback-nginx.png)