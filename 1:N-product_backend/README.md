# 3Scale Reverse Proxy

## Scenario 2
### *1 Product with N Backend*
![1 Product N Backends](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/3scale-proxy.drawio.png?raw=true)

1. Add the Backend if you don't have one, but here we have to set a different path for each backend.
   1. Product -> Integration -> Backends
    ![Backends](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:N-product_backend/image/backends.png?raw=true)
2. Add URL_REWRITING Policy
   1. Product -> Integration -> Policies -> Add Policy -> URL Rewriting
    ![Policies](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:1product_backend/image/policies.png?raw=true)
3. Setup the New Policy Adding two Commands and Click on Update Policy button.
    ![Policies](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:1product_backend/image/policy1.png?raw=true)
    ![Policies](https://github.com/rafamqrs/3scale-apicast-policies/blob/main/1:1product_backend/image/policy2.png?raw=true)
4. Update Policy Chain
5. Go to Configuration and Promote the API.
6. Test the proxy using the path user it will be redirect to /saveuser in echo-api.
   ```
    $ curl "https://api-3scale-apicast-staging.apps.cluster-36b7.36b7.example.opentlc.com:443/user? user_key=<user_id>"
   ```
   Output
   ```
        {
            "method": "GET",
            "path": "/saveuser",
            "args": "user_key=b9ae38258de1df083b9ea180d094785c",
            "body": "",
            .......
        }
   ```
7. Test the proxy using the path saveproduct it will be redirect to /api/expenses.
   ```
    $ curl "https://scenario1-3scale-apicast-staging.apps.cluster-36b7.36b7.example.opentlc.com:443/client?user_key=<user_key>"
   ```
    Output
   ```
        [
            {
                "id":1,
                "amount":150.50,
                "name":"Groceries",
                "paymentMethod":"CASH"
            }
        ......
        ]
   ```




