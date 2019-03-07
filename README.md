# Microservices 1.0
## Externalised Configuration

### Why?
As code moves from Developers machine to test to production. Code should remain same. 
Ease of configuration when all configurations are at one place
### How ?
Configuration Files can be either kept in SVN or Git or Vault or File System they can be segregated using profile names - Sujeet(Developer Name) / Development / Test / Production

Advantage of keeping in SVN or Git: { Version Control, Access Control}

Maintain multiple instances of Config server to avoid single point of failure

## Service Registry
### Why?
For an Enterprise class application, in production environment number of instances that would be required are not known. 
### How?
Register each Microservice to Service Registry.

For name resolution of a service, contact  Service Registry
Service Registry load balances the requests to respective instances of registered service.

Service Registry can be configured in HA for avoiding SPOF scenario

## API Gateway
### Why?
For ensuring all required policies are applied at one code base for all Microservice calls.
### How?
Routes and other policies can be configured using API Gateway
Multiple instances can be instantiated for avoiding SPOF.

## Centralised Logging
### Why?
Since there would be multiple microservices and also multiple instances of a microservice, enabling support for quick access to logs is essential.
### How?
All the streams of logs is routed to central place for accessing the logs of all microservices and their instances.

## Containerisation
### Why ?
For minimal overhead of compute and storage 
For ease of scale up and down
### How ?
Create image of each microservice
Create Network of related microservice
Expose ports of only required services 

## Implementation

Externalised Configuration : Spring Config Server : [ms-config-server](https://github.com/sujitrs/microservices1.0/tree/master/ms-config-server)

Service Registry : Eureka Server : [ms-service-registry-server](https://github.com/sujitrs/microservices1.0/tree/master/ms-service-registry-server)

API Gateway : Zuul Proxy : [ms-api-gateway](https://github.com/sujitrs/microservices1.0/tree/master/ms-api-gateway)

Centralised Logging : ELK with FluentD : td-agent and [docker-logging-fluentd](https://github.com/sujitrs/microservices1.0/tree/master/docker-logging-fluentd)

Containerisation : Docker Community: [step1 and step2](https://github.com/sujitrs/microservices1.0/tree/master/docker-compose)

Sample Edge UI : [web-noneureka-client](https://github.com/sujitrs/microservices1.0/tree/master/web-non-eureka-client)

Sample Edge UI (Eureka Client) : [web-eureka-client](https://github.com/sujitrs/microservices1.0/tree/master/web-eureka-client)

Sample Microservices : [ms-user-repo](https://github.com/sujitrs/microservices1.0/tree/master/ms-user-repo), [ms-app-repo](https://github.com/sujitrs/microservices1.0/tree/master/ms-app-repo), [ms-file-mgmnt](https://github.com/sujitrs/microservices1.0/tree/master/ms-file-mgmnt)

## Next Steps
### Security 
Between Micro-Services and Config Server/Service Registry

API Gateway Security to implement interceptors/ OAuth 2.0
### For non-Eureka Client, What if we want to control number of Zuul Server instances dynamically ?
### Kubernetes for Auto Scale
### Actuators for health of Microservices
### HA for ELK and Fluentd








