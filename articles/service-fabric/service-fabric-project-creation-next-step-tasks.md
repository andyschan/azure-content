<properties
   pageTitle="Service Fabric project creation next steps | Microsoft Azure"
   description="This article contains links to a set of core development tasks for Service Fabric"
   services="service-fabric"
   documentationCenter=".net"
   authors="seanmck"
   manager="timlt"
   editor=""/>

<tags
   ms.service="service-fabric"
   ms.devlang="dotNet"
   ms.topic="article"
   ms.tgt_pltfrm="NA"
   ms.workload="NA"
   ms.date="03/08/2016"
   ms.author="seanmck"/>

# Your Service Fabric application and next steps
Your Azure Service Fabric application has been created. This article describes the makeup of your project and some potential next steps.

## Your application
Every new application includes an application project. There may be one or two additional projects, depending on the type of service chosen.

### The application project
The application project consists of:

- A set of references to the services that make up your application.

- Two publish profiles (Local and Cloud) that you can use to maintain preferences for working with different environments--such as preferences related to a cluster endpoint and whether to perform upgrade deployments by default.

- Two application parameter files (Local and Cloud) that you can use to maintain environment-specific application configurations, such as the number of partitions to create for a service.

- A deployment script that you can use to deploy your application from the command line or as part of an automated continuous integration and deployment pipeline.

- The application manifest, which describes the application. You can find the manifest under the ApplicationPackageRoot folder.

### Reliable services
When you add a new reliable service, Visual Studio adds a service project to your solution. The service project contains a class that extends from either `StatelessService` or `StatefulService`, depending on the type you chose.

### Reliable actors
When you add a new reliable actor, Visual Studio adds two projects to your solution: an actor project and an interface project.

The actor project defines the actor type and (for stateful actors) its state. The interface project provides an interface that other services can use to invoke the actor.

Note that actor projects do not contain any default startup behavior, as actors must be activated by other services. Consider adding a reliable service or an ASP.NET project to create and interact with your actors.

### ASP.NET 5
The ASP.NET 5 templates that are provided for use in Service Fabric applications are almost identical to those available for ASP.NET 5 projects that are created independently. The only differences are:

- The project contains a **PackageRoot** folder for storing the ServiceManifest file along with data and config packages.

- The project references an additional NuGet package (Microsoft.ServiceFabric.AspNet.Hosting), which acts as a bridge between the .NET Execution Environment (DNX) and Service Fabric.

## Next steps
### Add a web front end to your application
Service Fabric provides integration with ASP.NET 5 for building web-based entry points to your application. See [Adding a web front end to your application][add-web-frontend] to learn how to create a REST interface based on the ASP.NET Web API.

### Create an Azure cluster
The Service Fabric SDK provides a local cluster for development and testing. To create a cluster in Azure, see [Setting up a Service Fabric cluster from the Azure portal][create-cluster-in-portal].

### Try deploying to Azure for free with party clusters

If you'd like to try deploying and managing applications in Azure without setting up your own clusters, you can use the free [party cluster service](http://aka.ms/tryservicefabric).

### Publish your application to Azure
You can publish your application directly from Visual Studio to an Azure cluster. To learn how, see [Publishing your application to Azure][publish-app-to-azure].

### Use Service Fabric Explorer to visualize your cluster
Service Fabric Explorer offers an easy way to visualize your cluster, including deployed applications and physical layout. To learn more, see [Visualizing your cluster by using Service Fabric Explorer][visualize-with-sfx].

### Version and upgrade your services
Service Fabric enables independent versioning and upgrading of independent services in an application. To learn more, see [Versioning and upgrading your services][app-upgrade-tutorial].

### Configure continuous integration with Visual Studio Team Services
To learn how you can set up a continuous integration process for your Service Fabric application, see [Configure continuous integration with Visual Studio Team Services][ci-with-vso].



<!-- Links -->
[add-web-frontend]: service-fabric-add-a-web-frontend.md
[create-cluster-in-portal]: service-fabric-cluster-creation-via-portal.md
[publish-app-to-azure]: service-fabric-publish-app-remote-cluster.md
[visualize-with-sfx]: service-fabric-visualizing-your-cluster.md
[ci-with-vso]: service-fabric-set-up-continuous-integration.md
[reliable-services-webapi]: service-fabric-reliable-services-communication-webapi.md
[app-upgrade-tutorial]: service-fabric-application-upgrade-tutorial.md
