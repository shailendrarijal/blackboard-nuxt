---
title: Big picture of Pivotal Cloud foundry
subtitle: Understanding pivotal cloud foundry in a bigger picture
category:
  - Technology
author: Shailendra Rijal
date: 2022-08-16T02:52:19.506Z
featureImage: /uploads/inside-glacier-cave-2.jpg
---
There are three different models of cloud services: Infrastructure as a service (IAAS), Platform as a service (PAAS), and Software as a service (SAAS). IAAS like Amazon Web Services provides the underlying infrastructure but you still need to configure your own runtime, Operating system, and middleware. PAAS like Cloudfoundry provides runtime, operating system, and middleware as well and you only need to have your own application and data system. SAAS like Salesforce provides everything for you even the application and data system. 

> ***"The advantages of using PAAS like Cloudfoundry is that you get everything you need to start building your application but you still are free to customize your application and your data systems. Let's dive into the cloudfoundry ecosystem and talk about some of the topics to understand the service better"***

The cloudfoundry ecosystem consists of User interfaces, services, Elastic runtime with Diego, Loggregator, Buildpacks, Cloud controller, Service broker and router, and Extensions, Operations and Cloud foundry BOSH. Lets take a brief look at them.

#### User interface

There are two types of user interfaces available in PCF:

1. Apps manager: This is the UI where you can configure your application configs with button clicks and UI.
2. cf CLI (cloud foundry command line interface): This is the cli interface through which you can write commands to configure and deploy your application. Here is the list of cf commands that you can use to configure and deploy your application: [cf commands](https://cli.cloudfoundry.org/en-US/v8/)

#### Elastic Runtime

Elastic runtime is a collection of DIEGO, buildpacks, cloud controller, service brokers, routing, and loggregator. Let's look at them individually:

##### DIEGO

Diego is a system that manages containers by scheduling and running Long-Running Processes. In an overview, an app instance run within an immutable container and containers run within a cell (virtual machine).  To understand the working of Diego in detail, follow this link for [Diego Components and Architecture](https://docs.pivotal.io/application-service/2-13/concepts/diego/diego-architecture.html).

##### Cloud controller

All the client data related to applications/spaces/organisations are persisted in a database called cloud controller data base. The cloud controller provides REST API endpoints fro clients to access to those data. Along with CCDB, there is a blob store where the app packages and droplets are stored by the cloud controller. To understand the working of cloud controller in detail, follow this link for [cloud controller](https://docs.pivotal.io/application-service/2-13/concepts/architecture/cloud-controller.html).

##### Router

The router directs traffic to an appropriate component. It might be a cloud controller or an application running in Diego cell. To learn the routing within cloud doundry, follow this link for [routing](https://docs.pivotal.io/application-service/2-13/concepts/cf-routing-architecture.html).

In a nutshell, these are the steps that happen when we run the `cf push` command:

1. The message goes to cloud controller to create an app
2. The cloud controller stores the application metadata in cloudcontroller database
3. The cloud controller stores the  application files in blob store
4. The cloud controller stages an app
5. The output of staging is streamed back through cloud controller
6. The Cell creates and stores droplet in blob store
7. The completion of staging report is sent back to cloud controller by the cell
8. The cloud controller then starts the staged application
9. The application status report is sent back to the customer

#### Services

Various services are available in the marketplace and they can be accessed via service brokers. There is a provision for adding credentials needed for an application. Once a service is selected from the marketplace, app binding can be done to bind the application to the service. To learn more about the services, follow the link for [Services.](https://docs.pivotal.io/application-service/2-13/services/overview.html)

#### Loggregator

This is how the logs are streamed to the terminal. The command `cf <appname> logs` outputs the logs. The cf system stores a limited amount of logs and the complete log can be drained to a third-party log management system. To learn more about the logs, follow this link for [App logging in TAS for VMs](https://docs.pivotal.io/application-service/2-13/devguide/deploy-apps/streaming-logs.html).

#### Buildpack

Buildpack is what detects the language or framework our application is using and provides the framework and runtime support for the application. To learn more about the buildpack and how they work, follow the link for [Buildpacks](https://docs.pivotal.io/application-service/2-13/buildpacks/index.html).

#### Operations Manager and BOSH

Apart from elastic runtime, services, and user interfaces, there are extensions, operations manager and cloudfoundry BOSH worth exploring. Extensions such as SSO, Autoscaler are available. The operations manager together with BOSH allows us to deploy on IAAS like AWS or GCP or Azure. To learn more about the operations manager, follow this link for [Operations manager.](https://docs.pivotal.io/ops-manager/2-10/index.html)

#### Some common operations using cloud foundry

* Logging in: `cf login -a <apiUrl>`

  * Enter your login credentials to log in
* Viewing the space and org: `cf target` 

  * Shows your api endpoint, user, org, and space. Organisation is a business unit, space is an environment.
  * To change the space or org, use the `-s` for space and `-o` for org in the command
* Pushing an application: `cf push <appname> -p <pathname> -m <memory-size> -i <number-of-instances>`

  * Pushes an application with the app name. The trailing flags represent their meanings.
* View list of all apps: `cf apps`
* Start/ stop/ delete an app: `cf start <appname> || cf stop <appname> || cf delete <appname>`
* View the logs: `cf logs`
* Scaling up or down: `cf scale <appname> -m <memory-size> -i <instance-number>`

  * An application can be scaled down or scaled up by changing their memory size and number of instances.
* Setting an environment variable: `cf set-env <appname> <KEY> '<value>'`
* View the state of an app: `cf app <appname>`
* View the environment variables of an app: `cf env <appname>`
* Create a service: `cf create-service <service-offering> <plan> <service-instance>`
* Bind service to application: `cf bind-service <appname> <service-instance>`
* Create user provided service instance: `cf create-user-provided-service <service-instance> -c <parameters-as-json> --binding-name <binding-name>` 
* Generate a manifest file from a running app: `cf create-app-manifest <appname> -p ./<manifest-filename>.yml`
* View security groups: `cf security-groups`
* View buildpacks: `cf buildpacks`
* Map a route: `cf map-route <appname> <domain-name> --hostname <hostname>`
* Unmap a route: `cf unmap-route <appname> <domain-name> --hostname <hostname>`