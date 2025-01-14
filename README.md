# Nexus Platform on Docker

This repo contains `docker-compose` files associated sample configuration for quickly standing up a number of *Reference Architectures* for the Nexus Platform components.

Ideal if you want to get hands on quickly :-)

Unless you have a license from [Sonatype](https://www.sonatype.com), you will only be able to use [Neuxs Repository OSS](https://www.sonatype.com/products/repository-oss).

If you don't have a trial license and would like one [contact Sonatype](https://www.sonatype.com).

# What is the Nexus Platform?

When we refer to the Nexus Platform, we actually refer to three of Sonatype's core-products and their associated add-on packs. These are:

1. Neuxs Repository (either [Neuxs Repository OSS](https://www.sonatype.com/products/repository-oss) or [Nexus Repository Pro](https://www.sonatype.com/products/repository-pro?))
2. [Nexus Lifecycle](https://www.sonatype.com/products/open-source-security-dependency-management) and it's add-on packs:
    - [Advanced Development Pack](https://www.sonatype.com/product/advanced-development-pack)
    - [Advanced Legal Pack](https://www.sonatype.com/products/advanced-legal-pack)
    - [Infrastructure as Code Pack](https://www.sonatype.com/product/infrastructure-as-code)
3. [Nexus Firewall](https://www.sonatype.com/products/firewall)

For the full suite of products - check out [www.sonatype.com](https://www.sonatype.com).

# How does this code work?

We utilise [docker-compose profiles](https://docs.docker.com/compose/profiles/) to allow you to quickly stand up the required containers to realise a specific refernece architecture.

Assuming you have [Docker Desktop]([https://](https://www.docker.com/products/docker-desktop) 19.03.0+ (or similar) installed, you can simply run `docker-compose` passing the required profile. An example using the `proxied` profile might be:

```
docker-compose --profile=proxied up -d
```

# Providing your Sonatype License

For most of the reference architecutres, you'll need a Sonatype license. If you have this, (it's a `.lic`) file you can use it through one of two methods:

1. Put your `.lic` file in `config/sonatype-license-all.lic`
2. Modify the path to your `.lic` file in the `.env` file:
    ```
    NEXUS_LICENSE_PATH=/your/path/to/your-sonatype.lic
    ```

# Reference Architecture Profiles

| Profile Name    | License Required | Nexus Platform                                | Nexus Repo                               | Nexus Lifecycle                        | Description                                                                                           |
| --------------- | ---------------- | --------------------------------------------- | ---------------------------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `proxied`       | Yes              | Yes - [here](http://nexus-platform.localhost) | Yes [here](http://repo.localhost/)       | Yes [here](http://iq.localhost/)       | Both Nexus Repository Pro and Nexus Lifecycle available behind an nGinx reverse proxy.                |
| `direct`        | Yes              | No                                            | Yes - [here](http://repo.localhost:8081) | Yes - [here](http://iq.localhost:8070) | Both Nexus Repository Pro and Nexus Lifecycle available directly via `localhost` addressed over HTTP. |
| `repoOssDemo`   | No               | No                                            | Yes - [here](http://repo.localhost:8081) | No                                     | Nexus Repo OSS will be started.                                                                       |
| `cicd-jenkins`  | Yes              | Yes - [here](http://nexus-platform.localhost) | Yes [here](http://repo.localhost/)       | Yes [here](http://iq.localhost/)       | Includes a Jenkins [here](http://nexus-platform/jenkins)                                              |
| `cicd-teamcity` | Yes              | Yes - [here](http://nexus-platform.localhost) | Yes [here](http://repo.localhost/)       | Yes [here](http://iq.localhost/)       | Includes a TeamCity Server [here](http://nexus-platform/teamcity)                                     |

## Additional Sub Profiles

The following profiles can be stood up in parallel to the `proxied` profile to provide further services:

| Profile Name | Endpoints                                                                                                                  | Description                   |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| `swagger`    | [Swagger Editor](http://nexus-platform.localhost/swagger-editor), [Swagger UI](http://nexus-platform.localhost/swagger-ui) | Swagger Editor and Swagger UI |


# Acknowledgments
This project makes use of the following open source libraries/plugins:
1. [nexus-casc-plugin](https://github.com/asharapov/nexus-casc-plugin) which is licensed under MIT License and is Copyright 2019 Sven Tschui

# License
See `LICENSE` file for details.
 

# The Fine Print
It is worth noting that this is NOT SUPPORTED by Sonatype, and is a contribution of ours to the open source community (read: you!)

Remember:

- Use this contribution at the risk tolerance that you have
- Do NOT file Sonatype support tickets related to this project
- DO file issues here on GitHub, so that the community can pitch in
- Phew, that was easier than I thought. Last but not least of all:

Have fun creating and using this utility to quikcly get hands-on with Nexus Repository and Nexus Lifecycle. We are glad to have you here!