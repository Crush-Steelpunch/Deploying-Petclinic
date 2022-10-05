# Deploying-Petclinic

Petclinic requires two services to be deployed, an javascript frontend in angular and the backend rest api in java.

- [Angular Frontend](https://github.com/spring-petclinic/spring-petclinic-angular)
- [Spring REST API](https://github.com/spring-petclinic/spring-petclinic-rest)

The original design of the application is to run on a workstation machine and be accessed on localhost

In order to run it in a cloud environment you will need alter the rest api environment variables for the angular service.

The environment variables are retrieved in the angular code in `spring-petclinic-angular/src/environments/{environment.ts, environment.prod.ts}`

- `REST_API_URL=http://server:port/apipath`
- `production=true/false`

Note: The frontend is written in javascript. So the actual code runs in the users browser, not on the cloud platform. That means the backend API path should be an external, globally routeable address.

## Cloud Deployment

As the backend needs to be accessed from the internet it would be preferred to have the frontend accessed through the same server url so you don't run in to cross site scripting issues.

For this you should think about using nginx to proxy the url `http://server/` to the angular code and `http://server/petclinic/api` to the api service.

## Rebuilding Backend API image

As noted in the petclinic api [docs](https://github.com/spring-petclinic/spring-petclinic-rest#publishing-a-docker-image)

The rest api uses the Google Jib plugin for maven to create the docker image. 

How to create an image that is pushed to a repository, tarball, or one built for a local Docker daemon is [here](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin#build-your-image)

Maven is available in the main Ubuntu repositories.
