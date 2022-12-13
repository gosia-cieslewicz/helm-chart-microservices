# Online Shop Microservices Deployment

This is deployment manifest for Googles Online Shop Microservices Demo:
https://github.com/GoogleCloudPlatform/microservices-demo

# Microservices

| **microservice**      | **image**<br>gcr.io/google-samples/microservices-demo/ | **port** | env vars                                                                                                                                                                                                                       |
|-----------------------|--------------------------------------------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| frontend              | frontend:v0.4.1                                        | 8080     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR<br>CURRENCY_SERVICE_ADDR<br>CART_SERVICE_ADDR<br>RECOMMENDATION_SERVICE_ADDR<br>SHIPPING_SERVICE_ADDR<br>CHECKOUT_SERVICE_ADDR <br>AD_SERVICE_ADDR<br>DISABLE_TRACING<br>DISABLE_PROFILER |
| cartservice           | cartservice:v0.4.1                                     | 7070     | PORT<br>REDIS_ADDR                                                                                                                                                                                                             |
| productcatalogservice | productcatalogservice:v0.4.1                           | 3550     | PORT<br>DISABLE_STATS<br>DISABLE_TRACING<br>DISABLE_PROFILER                                                                                                                                                                   |
| currencyservice       | currencyservice:v0.4.1                                 | 7000     | PORT<br>DISABLE_TRACING<br>DISABLE_PROFILER<br>DISABLE_DEBUGGER                                                                                                                                                                |
| paymentservice        | paymentservice:v0.4.1                                  | 50051    | PORT<br>DISABLE_TRACING<br>DISABLE_PROFILER<br>DISABLE_DEBUGGER                                                                                                                                                                |
| shippingservice       | shippingservice:v0.4.1                                 | 50051    | PORT<br>DISABLE_STATS<br>DISABLE_TRACING<br>DISABLE_PROFILER                                                                                                                                                                   |
| emailservice          | emailservice:v0.4.1                                    | 8080     | PORT<br>DISABLE_TRACING<br>DISABLE_PROFILER                                                                                                                                                                                    |
| checkoutservice       | checkoutservice:v0.4.1                                 | 5050     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR<br>SHIPPING_SERVICE_ADDR<br>PAYMENT_SERVICE_ADDR<br>EMAIL_SERVICE_ADDR<br>CURRENCY_SERVICE_ADDR<br>CART_SERVICE_ADDR<br>DISABLE_STATS<br>DISABLE_TRACING<br>DISABLE_PROFILER              |
| recommendationservice | recommendationservice:v0.4.1                           | 8080     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR<br>DISABLE_TRACING<br>DISABLE_PROFILER<br>DISABLE_DEBUGGER                                                                                                                                |
| adservice             | adservice:v0.4.1                                       | 9555     | PORT<br>DISABLE_STATS<br>DISABLE_TRACING                                                                                                                                                                                        |
| redis                 | redis:alpine                                           | 6379     |                                                                                                                                                                                                                                |

# Connection Graph

![connection graph](connection-graph.png?raw=true "Connection Graph")

# Local setup for testing locally with Minikube

1. Install minikube (will also install kubectl):

`brew install minikube`

2. Start minikube cluster with docker driver

`minikube start --driver docker`

## Start app using Kubernetes Manifest file

3. Create microservices namespace:

`kubectl create ns microservices`

4. Apply config file:

`kubectl apply -f config.yaml -n microservices`

5. Forward port to access browser at: http://localhost:8080/

`kubectl port-forward deployment/frontend 8080`

6. Stop all components:

`kubectl delete -f config.yaml -n microservices`

## Or start app using Helm Chart

3. Install helm:

`brew install helm`

4. Install helmfile:

`brew install helmfile`

5. Sync the cluster with desired state of the app declared in helmfile:

`helmfile sync`

6. Forward port to access browser at: http://localhost:8080/

`kubectl port-forward deployment/frontend 8080`

7. Stop all helm releases:

`helmfile destroy`
