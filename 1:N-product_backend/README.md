# 3Scale Reverse Proxy

## Scenario 1
### *1 Product with N Backend*
![1 Product N Backends](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/3scale-proxy.drawio.png?raw=true)

1. Add the Backend if you don't have one
   1. Product -> Integration -> Backends
    ![Backends](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/backends.png?raw=true)
2. Add URL_REWRITING Policy
   1. Product -> Integration -> Policies -> Add Policy -> URL Rewriting
    ![Policies](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/policies.png?raw=true)
3. Setup the New Policy Adding the Commands and Click on Update Policy button.
    ![Policies](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/url_rewriting.png?raw=true)   
4. Update Policy Chain
5. Go to Configuration and Promote the API.
6. Test the proxy using the path listuser it will be redirect to /save.
   ```
    $ curl "https://scenario1-3scale-apicast-staging.apps.cluster-36b7.36b7.example.opentlc.com:443/listuser?user_key=<user_key>"
   ```
   Output
   ```
        {
        "method": "GET",
        "path": "/save",
        "args": "user_key=6fe3f45df43a304d93d478478b6d56d3",
        "body": "",
        .......
        }
   ```
7. Test the proxy using the path saveproduct it will be redirect to /product.
   ```
    $ curl "https://scenario1-3scale-apicast-staging.apps.cluster-36b7.36b7.example.opentlc.com:443/saveproduct?user_key=<user_key>"
   ```
    Output
   ```
        {
        "method": "GET",
        "path": "/product",
        "args": "user_key=6fe3f45df43a304d93d478478b6d56d3",
        "body": ""
        ......
        }
   ```




