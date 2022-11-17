# Online Shop Microservices Deployment

This is deployment manifest for Googles Online Shop Microservices Demo:
https://github.com/GoogleCloudPlatform/microservices-demo

# Microservices

| **microservice**      | **image**<br>gcr.io/google-samples/microservices-demo/ | **port** | env vars                                                                                                                                                                                |
|-----------------------|--------------------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| frontend              | frontend:v0.2.3                                        | 8080     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR<br>CURRENCY_SERVICE_ADDR<br>CART_SERVICE_ADDR<br>RECOMMENDATION_SERVICE_ADDR<br>SHIPPING_SERVICE_ADDR<br>CHECKOUT_SERVICE_ADDR <br>AD_SERVICE_ADDR |
| cartservice           | cartservice:v0.2.3                                     | 7070     | PORT<br>REDIS_ADDR                                                                                                                                                                      |
| productcatalogservice | productcatalogservice:v0.2.3                           | 3550     | PORT                                                                                                                                                                                    |
| currencyservice       | currencyservice:v0.2.3                                 | 7000     | PORT                                                                                                                                                                                    |
| paymentservice        | paymentservice:v0.2.3                                  | 50051    | PORT                                                                                                                                                                                    |
| shippingservice       | shippingservice:v0.2.3                                 | 50051    | PORT                                                                                                                                                                                    |
| emailservice          | emailservice:v0.2.3                                    | 8080     | PORT                                                                                                                                                                                    |
| checkoutservice       | checkoutservice:v0.2.3                                 | 5050     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR<br>SHIPPING_SERVICE_ADDR<br>PAYMENT_SERVICE_ADDR<br>EMAIL_SERVICE_ADDR<br>CURRENCY_SERVICE_ADDR<br>CART_SERVICE_ADDR                               |
| recommendationservice | recommendationservice:v0.2.3                           | 8080     | PORT<br>PRODUCT_CATALOG_SERVICE_ADDR                                                                                                                                                    |
| adservice             | adservice:v0.2.3                                       | 9555     | PORT                                                                                                                                                                                    |
| redis                 | redis:alpine                                           | 6379     |                                                                                                                                                                                         |

# Connection Graph

![connection graph](connection-graph.png?raw=true "Connection Graph")