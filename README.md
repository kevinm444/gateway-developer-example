
# About
This is an example repository which uses the [CA API Gateway Developer Plugin][gateway-developer-plugin] to demonstrate storing deployment configurations in a CICD pipeline.

# Getting Started

## Building the Solution
In order to package the solution into something that can be applied to the CA API Gateway run the following Gradle command:

```./gradlew build```

## Running the Solution
In order to run the solution you need to do the following:

1) Put a valid gateway license in the `docker` folder. The license file should be called `license.xml`. For information on getting a license see the [License Section from the Gateway Container readme](https://hub.docker.com/r/caapim/gateway/).
1) Make sure you have already built the solution by running `./gradlew build`
1) Start the Gateway Container by running: `docker-compose up`

After the container is up and running you can connect the CA API Gateway Policy Manager to it (localhost, admin, password )

## Exporting Updates
If you connect to the running gateway with the CA API Gateway Policy Manager and make changes to the services and policies you can export those changes by running:

```./gradlew export```

This will export the changes to the various project folders. Note that your local edits will be overridden by changes from the gateway

## CICD

Build configurations are described in the `Jenkinsfile`. 

The following parameters are required:
1) `NEW_IMAGE_REGISTRY_HOSTNAME` registry to publish to
1) `NEW_IMAGE_REGISTRY_USER` credentials for registry to publish to	
1) `NEW_IMAGE_REGISTRY_PASSWORD` credentials for registry to publish to	

This example includes the following steps:
1) Builds and run the gateway
1) Test by using the endpoint `/env-configuration`
1) publish the docker image with build number as tag

# Giving Back
## How You Can Contribute
Contributions are welcome and much appreciated. To learn more, see the [Contribution Guidelines][contributing].

## License

Copyright (c) 2018 CA. All rights reserved.

This software may be modified and distributed under the terms
of the MIT license. See the [LICENSE][license-link] file for details.


 [license-link]: /LICENSE
 [contributing]: /CONTRIBUTING.md
 [gateway-developer-plugin]: https://github.com/ca-api-gateway/gateway-developer-plugin
