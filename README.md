## create a new cluster using kind

    kind create cluster

## Clone the github repo

https://github.com/UmarFarooqkadri/helm-deployment

Update image if required [here](https://github.com/UmarFarooqkadri/helm-deployment/blob/main/nginx-deployment-chart/values.yaml#L10 "here")

Add service account details [here](https://github.com/UmarFarooqkadri/helm-deployment/blob/main/nginx-deployment-chart/values.yaml#L32 "here")


Update service type [here](https://github.com/UmarFarooqkadri/helm-deployment/blob/main/nginx-deployment-chart/values.yaml#L55 "here")

## Install the chart

    helm install helm-nginx nginx-deployment-chart --values nginx-deployment-chart/values.yaml

## Export the Node Port

     export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services helm-nginx-nginx-deployment-chart)

##  Export the Node IP
     export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")

## Export URL

  echo http://$NODE_IP:$NODE_PORT

  Now try to open the url in browser. Since this is a kind cluster you will need to port forward to make is accessible.
  
  Ref: https://opensource.com/article/20/5/helm-charts