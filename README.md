# Minecraft in GKE with Helm

```
gcloud config set project brownbag-294119

gcloud beta container --project "brownbag-294119" clusters create "demo1" --zone "us-central1-c" --no-enable-basic-auth --cluster-version "1.16.13-gke.401" --machine-type "e2-medium" --image-type "COS" --disk-type "pd-standard" --disk-size "100" --metadata disable-legacy-endpoints=true --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "3" --enable-stackdriver-kubernetes --enable-ip-alias --network "projects/brownbag-294119/global/networks/default" --subnetwork "projects/brownbag-294119/regions/us-central1/subnetworks/default" --default-max-pods-per-node "110" --no-enable-master-authorized-networks --addons HorizontalPodAutoscaling,HttpLoadBalancing --enable-autoupgrade --enable-autorepair --max-surge-upgrade 1 --max-unavailable-upgrade 0

gcloud container clusters get-credentials demo1 --zone=us-central1-c

curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash

git clone https://github.com/greglamb/gke-brownbag

cd gke-brownbag

helm install minecraft minecraft --debug

kubectl get svc

helm delete minecraft
```
