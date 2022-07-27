# Deploying-Petclinic

Petclinic requires two services to be deployed, an javascript frontend in angular and the backend rest api in java.

- [Angular Frontend](https://github.com/spring-petclinic/spring-petclinic-angular)
- [Spring REST API](https://github.com/spring-petclinic/spring-petclinic-rest)

The original design of the application is to run on a workstation machine and be accessed on localhost

In order to run it in a cloud environment you will need alter the rest api environment variables for the angular service.

The environment variables are retrieved in the angular code in `spring-petclinic-angular/src/environments/{environment.ts, environment.prod.ts}`

- `REST_API_URL=http://server:port/apipath`
- `production=true/false`

## Cloud Deployment

It would be preferred to have the frontend accessed through the same server url so you don't run in to cross site scripting issues

For this you should think about using nginx to proxy the url `http://server/` to the angular code and `http://server/petclinic/api` to the api service.

