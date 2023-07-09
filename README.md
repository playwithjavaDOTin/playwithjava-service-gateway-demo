# playwithjava-service-gateway-demo
**Demo For Service-Gateway**


clone all the services and make sure that all service are up and running in your system.

**Testing**

**Lets consider you want to call below API from Epployee-Service**

http://localhost:9003/employee/emp/getEmployee/1


As we have 2 running istances of **Epployee-Service** , when you are making call directly you need to mention PORT of service everytime while calling and you will be able to call API on given instance only as PORT no is given.



**Fiegn Client :**



For more info ,Please visit **https://github.com/playwithjavaDOTin/springboot-feign-client-demo** to know how **Feign** works for Loadbalancing and remote calling to remore API.

Here we will call **Employee-service API** via Feign client to enable load balancing as well.

Call to api through feign client remotely from employee-feign-service ,since eureka is enable so we can even call using service name

**http://localhost:9005/employeeRm/remote/getFeignEmployee/1**



**Service-Gateway**

Spring-cloud-service-gateway will take care of intercepting ang request in middle, adding some Headers,Auth token,redirection and routing the request.

Lets see how we can call the same above **Employee-Service API** Via **Service-Gateway**

**Have a look below for better urnderstanding.**

**8765** :: Service-Gateway port

**employee-service** :: service name of employee-service

**employee-feign-service**   ::  service name of employee-feign-service application [check in application.properties file]

**employee/emp/getEmployee/1**  :: endpoint you wanted to call from employee-service [http://localhost:9003/employee/emp/getEmployee/1  , just removehost and port]




_http://localhost:8765/employee-service/employee/emp/getEmployee/1 _  ::  direct call to eployee-service  cia service-gateway

_http://localhost:8765/employee-feign-service/employeeRm/remote/getFeignEmployee/1_   ::call to employee-service via service-gateway through FEIGN CLIENT

