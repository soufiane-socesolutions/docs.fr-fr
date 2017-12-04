---
title: "Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a><span data-ttu-id="f7a48-104">Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité</span><span class="sxs-lookup"><span data-stu-id="f7a48-104">Orchestrating microservices and multi-container applications for high scalability and availability</span></span>

<span data-ttu-id="f7a48-105">À l’aide d’orchestrators pour les applications de l’environnement de production est essentiel si votre application est basée sur microservices ou simplement distribuée sur plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f7a48-105">Using orchestrators for production-ready applications is essential if your application is based on microservices or simply split across multiple containers.</span></span> <span data-ttu-id="f7a48-106">Introduit précédemment, dans une approche basée sur les microservice, chaque microservice possède son modèle et les données afin qu’il soit autonome à partir d’un développement et un point de vue du déploiement.</span><span class="sxs-lookup"><span data-stu-id="f7a48-106">As introduced previously, in a microservice-based approach, each microservice owns its model and data so that it will be autonomous from a development and deployment point of view.</span></span> <span data-ttu-id="f7a48-107">Toutefois, même si vous avez une application plus classique qui est composée de plusieurs services (par exemple, SOA), vous devez également plusieurs conteneurs ou services comprenant une application unique qui doivent être déployés en tant qu’un système distribué.</span><span class="sxs-lookup"><span data-stu-id="f7a48-107">But even if you have a more traditional application that is composed of multiple services (like SOA), you will also have multiple containers or services comprising a single business application that need to be deployed as a distributed system.</span></span> <span data-ttu-id="f7a48-108">Ces types de systèmes sont complexes à monter en charge et gérer ; Par conséquent, vous devez absolument orchestrateur si vous souhaitez disposer d’une application conteneur multi prêt pour la production et évolutive.</span><span class="sxs-lookup"><span data-stu-id="f7a48-108">These kinds of systems are complex to scale out and manage; therefore, you absolutely need an orchestrator if you want to have a production-ready and scalable multi-container application.</span></span>

<span data-ttu-id="f7a48-109">Figure 4-23 illustre un déploiement dans un cluster d’une application composée de plusieurs microservices (conteneurs).</span><span class="sxs-lookup"><span data-stu-id="f7a48-109">Figure 4-23 illustrates deployment into a cluster of an application composed of multiple microservices (containers).</span></span>

![](./media/image23.PNG)

<span data-ttu-id="f7a48-110">**Figure 4-23**.</span><span class="sxs-lookup"><span data-stu-id="f7a48-110">**Figure 4-23**.</span></span> <span data-ttu-id="f7a48-111">Un cluster de conteneurs</span><span class="sxs-lookup"><span data-stu-id="f7a48-111">A cluster of containers</span></span>

<span data-ttu-id="f7a48-112">Il ressemble à une approche logique.</span><span class="sxs-lookup"><span data-stu-id="f7a48-112">It looks like a logical approach.</span></span> <span data-ttu-id="f7a48-113">Mais comment vous équilibrage de charge de gestion, de routage et d’orchestration de ces composés applications ?</span><span class="sxs-lookup"><span data-stu-id="f7a48-113">But how are you handling load-balancing, routing, and orchestrating these composed applications?</span></span>

<span data-ttu-id="f7a48-114">Le moteur Docker brut dans des hôtes Docker uniques répond aux besoins de la gestion des instances d’image unique sur un ordinateur hôte, mais il n’était pas lorsqu’il s’agit de la gestion de plusieurs conteneurs sont déployés sur plusieurs ordinateurs hôtes pour les applications distribuées plus complexes.</span><span class="sxs-lookup"><span data-stu-id="f7a48-114">The plain Docker Engine in single Docker hosts meets the needs of managing single image instances on one host, but it falls short when it comes to managing multiple containers deployed on multiple hosts for more complex distributed applications.</span></span> <span data-ttu-id="f7a48-115">Dans la plupart des cas, vous avez besoin d’une plateforme de gestion des conteneurs, les conteneurs de montée en puissance parallèle avec plusieurs instances par une image de démarrage, les suspendre ou les arrêter si nécessaire, et automatiquement idéalement également contrôler comment accéder aux ressources, telles que le réseau et les données stockage.</span><span class="sxs-lookup"><span data-stu-id="f7a48-115">In most cases, you need a management platform that will automatically start containers, scale-out containers with multiple instances per image, suspend them or shut them down when needed, and ideally also control how they access resources like the network and data storage.</span></span>

<span data-ttu-id="f7a48-116">Pour aller au-delà de la gestion des conteneurs individuels ou les applications composées très simples et déplacer vers les grandes applications d’entreprise avec microservices, vous devez activer orchestration et le clustering des plateformes.</span><span class="sxs-lookup"><span data-stu-id="f7a48-116">To go beyond the management of individual containers or very simple composed apps and move toward larger enterprise applications with microservices, you must turn to orchestration and clustering platforms.</span></span>

<span data-ttu-id="f7a48-117">À partir d’un point de vue architecture et le développement, si vous générez des grandes entreprises composées d’applications basées sur des microservices, il est important de comprendre les plateformes et les produits qui prennent en charge des scénarios avancés suivants :</span><span class="sxs-lookup"><span data-stu-id="f7a48-117">From an architecture and development point of view, if you are building large enterprise composed of microservices-based applications, it is important to understand the following platforms and products that support advanced scenarios:</span></span>

<span data-ttu-id="f7a48-118">**Clusters et orchestrators**.</span><span class="sxs-lookup"><span data-stu-id="f7a48-118">**Clusters and orchestrators**.</span></span> <span data-ttu-id="f7a48-119">Lorsque vous devez faire évoluer des applications sur plusieurs hôtes Docker, comme lors d’une grande application microservice, il est essentiel de pouvoir gérer tous ces ordinateurs hôtes en tant qu’un seul cluster en faisant abstraction de la complexité de la plateforme sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="f7a48-119">When you need to scale out applications across many Docker hosts, as when a large microservice-based application, it is critical to be able to manage all those hosts as a single cluster by abstracting the complexity of the underlying platform.</span></span> <span data-ttu-id="f7a48-120">C’est ce que les clusters de conteneur et orchestrators fournir.</span><span class="sxs-lookup"><span data-stu-id="f7a48-120">That is what the container clusters and orchestrators provide.</span></span> <span data-ttu-id="f7a48-121">Exemples d’orchestrators sont Azure Service Fabric, Kubernetes, Docker Swarm et mésosphère contrôleur de domaine/système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f7a48-121">Examples of orchestrators are Azure Service Fabric, Kubernetes, Docker Swarm and Mesosphere DC/OS.</span></span> <span data-ttu-id="f7a48-122">Les trois dernières orchestrators open source sont disponibles dans Azure via le Service de conteneur Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-122">The last three open-source orchestrators are available in Azure through Azure Container Service.</span></span>

<span data-ttu-id="f7a48-123">**Planificateurs**.</span><span class="sxs-lookup"><span data-stu-id="f7a48-123">**Schedulers**.</span></span> <span data-ttu-id="f7a48-124">*Planification* signifie la capacité d’un administrateur pour lancer des conteneurs dans un cluster afin qu’ils fournissent également une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f7a48-124">*Scheduling* means to have the capability for an administrator to launch containers in a cluster so they also provide a UI.</span></span> <span data-ttu-id="f7a48-125">Un planificateur de cluster a plusieurs responsabilités : à utiliser efficacement les ressources du cluster, pour définir les contraintes fournis par l’utilisateur, aux conteneurs efficacement d’équilibrer la charge entre les nœuds ou des ordinateurs hôtes et être robustes face à des erreurs tout en offrant une haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="f7a48-125">A cluster scheduler has several responsibilities: to use the cluster’s resources efficiently, to set the constraints provided by the user, to efficiently load-balance containers across nodes or hosts, and to be robust against errors while providing high availability.</span></span>

<span data-ttu-id="f7a48-126">Les concepts d’un cluster et un planificateur sont étroitement liés, les produits fournis par différents fournisseurs souvent fournissent les deux ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f7a48-126">The concepts of a cluster and a scheduler are closely related, so the products provided by different vendors often provide both sets of capabilities.</span></span> <span data-ttu-id="f7a48-127">La liste suivante montre la plate-forme plus importante et les choix d’un logiciel pour les clusters et des planificateurs.</span><span class="sxs-lookup"><span data-stu-id="f7a48-127">The following list shows the most important platform and software choices you have for clusters and schedulers.</span></span> <span data-ttu-id="f7a48-128">Ces orchestrators sont généralement proposées dans des clouds publics comme Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-128">These orchestrators are generally offered in public clouds like Azure.</span></span>

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a><span data-ttu-id="f7a48-129">Plateformes logicielles de clustering de conteneur, d’orchestration et de planification</span><span class="sxs-lookup"><span data-stu-id="f7a48-129">Software platforms for container clustering, orchestration, and scheduling</span></span>

<span data-ttu-id="f7a48-130">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f7a48-130">Kubernetes</span></span>

![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image24.png)

> <span data-ttu-id="f7a48-132">Kubernetes est un produit open source qui fournit des fonctionnalités qui s’étend de l’infrastructure de cluster et le conteneur de la planification des capacités orchestrant ces opérations.</span><span class="sxs-lookup"><span data-stu-id="f7a48-132">Kubernetes is an open-source product that provides functionality that ranges from cluster infrastructure and container scheduling to orchestrating capabilities.</span></span> <span data-ttu-id="f7a48-133">Il vous permet d’automatiser les opérations de conteneurs d’applications, de mise à l’échelle et de déploiement pour tous les clusters d’ordinateurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="f7a48-133">It lets you automate deployment, scaling, and operations of application containers across clusters of hosts.</span></span>
>
> <span data-ttu-id="f7a48-134">Kubernetes fournit une infrastructure orientée conteneur qui regroupe des conteneurs d’applications dans des unités logiques pour faciliter la gestion et la découverte.</span><span class="sxs-lookup"><span data-stu-id="f7a48-134">Kubernetes provides a container-centric infrastructure that groups application containers into logical units for easy management and discovery.</span></span>
>
> <span data-ttu-id="f7a48-135">Kubernetes est déjà rodée dans Linux, moins mature dans Windows.</span><span class="sxs-lookup"><span data-stu-id="f7a48-135">Kubernetes is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="f7a48-136">Docker essaim</span><span class="sxs-lookup"><span data-stu-id="f7a48-136">Docker Swarm</span></span>

![http://rancher.com/WP-Content/Themes/rancher-2016/Assets/images/swarm.png?v=2016-07-10-AM](./media/image25.png)

> <span data-ttu-id="f7a48-138">Docker essaim vous permet de planifier des conteneurs Docker et le cluster.</span><span class="sxs-lookup"><span data-stu-id="f7a48-138">Docker Swarm lets you cluster and schedule Docker containers.</span></span> <span data-ttu-id="f7a48-139">À l’aide d’essaim, vous pouvez activer un pool d’hôtes Docker dans un hôte Docker virtuel unique.</span><span class="sxs-lookup"><span data-stu-id="f7a48-139">By using Swarm, you can turn a pool of Docker hosts into a single, virtual Docker host.</span></span> <span data-ttu-id="f7a48-140">Les clients peuvent envoyer des demandes API à Swarm de la même façon qu'ils faire aux hôtes, ce qui signifie que qu’essaim facilite pour les applications à l’échelle sur plusieurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="f7a48-140">Clients can make API requests to Swarm the same way they do to hosts, meaning that Swarm makes it easy for applications to scale to multiple hosts.</span></span>
>
> <span data-ttu-id="f7a48-141">Docker essaim est un produit à partir de Docker, la société.</span><span class="sxs-lookup"><span data-stu-id="f7a48-141">Docker Swarm is a product from Docker, the company.</span></span>
>
> <span data-ttu-id="f7a48-142">Version de docker 1.12 ou plus tard pouvant s’exécuter en Mode natif et intégrées Swarm.</span><span class="sxs-lookup"><span data-stu-id="f7a48-142">Docker v1.12 or later can run native and built-in Swarm Mode.</span></span>

<span data-ttu-id="f7a48-143">Mésosphère contrôleur de domaine/système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f7a48-143">Mesosphere DC/OS</span></span>

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> <span data-ttu-id="f7a48-145">Mésosphère Enterprise contrôleur de domaine/système d’exploitation (basée sur Apache Mesos) est une plateforme de l’environnement de production pour l’exécution des conteneurs et des applications distribuées.</span><span class="sxs-lookup"><span data-stu-id="f7a48-145">Mesosphere Enterprise DC/OS (based on Apache Mesos) is a production-ready platform for running containers and distributed applications.</span></span>
>
> <span data-ttu-id="f7a48-146">Contrôleur de domaine/système d’exploitation fonctionne en faisant abstraction d’une collection de ressources disponibles dans le cluster et la disposition de ces ressources pour les composants générés par-dessus.</span><span class="sxs-lookup"><span data-stu-id="f7a48-146">DC/OS works by abstracting a collection of the resources available in the cluster and making those resources available to components built on top of it.</span></span> <span data-ttu-id="f7a48-147">Marathon est généralement utilisé comme un planificateur intégré à un contrôleur de domaine/système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f7a48-147">Marathon is usually used as a scheduler integrated with DC/OS.</span></span>
>
> <span data-ttu-id="f7a48-148">Contrôleur de domaine/système d’exploitation est déjà rodée dans Linux, moins mature dans Windows.</span><span class="sxs-lookup"><span data-stu-id="f7a48-148">DC/OS is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="f7a48-149">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f7a48-149">Azure Service Fabric</span></span>

![https://Azure.Microsoft.com/svghandler/service-Fabric?Width=600&Height=315](./media/image27.png)

> <span data-ttu-id="f7a48-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) est une plateforme de microservices de Microsoft pour la création d’applications.</span><span class="sxs-lookup"><span data-stu-id="f7a48-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) is a Microsoft microservices platform for building applications.</span></span> <span data-ttu-id="f7a48-152">Il s’agit d’un [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de services et crée des clusters d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f7a48-152">It is an [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) of services and creates clusters of machines.</span></span> <span data-ttu-id="f7a48-153">L’infrastructure de service peut déployer des services en tant que conteneurs ou en tant que processus simples.</span><span class="sxs-lookup"><span data-stu-id="f7a48-153">Service Fabric can deploy services as containers or as plain processes.</span></span> <span data-ttu-id="f7a48-154">Il peut même combinaison de services dans des processus avec les services dans les conteneurs au sein de la même application et le cluster.</span><span class="sxs-lookup"><span data-stu-id="f7a48-154">It can even mix services in processes with services in containers within the same application and cluster.</span></span>
>
> <span data-ttu-id="f7a48-155">Fournit de l’infrastructure de service supplémentaires et facultatifs normative [Service Fabric, modèles de programmation ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) comme [services avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span><span class="sxs-lookup"><span data-stu-id="f7a48-155">Service Fabric provides additional and optional prescriptive [Service Fabric programming models ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) like [stateful services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) and [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span></span>
>
> <span data-ttu-id="f7a48-156">Service Fabric est déjà rodée dans Windows (évolution des années dans Windows), moins mature dans Linux.</span><span class="sxs-lookup"><span data-stu-id="f7a48-156">Service Fabric is mature in Windows (years evolving in Windows), less mature in Linux.</span></span> 
> <span data-ttu-id="f7a48-157">Les conteneurs Linux et Windows sont pris en charge dans l’infrastructure de Service depuis 2017.</span><span class="sxs-lookup"><span data-stu-id="f7a48-157">Both Linux and Windows containers are supported in Service Fabric since 2017.</span></span>

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a><span data-ttu-id="f7a48-158">À l’aide basée sur le conteneur d’orchestrators dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f7a48-158">Using container-based orchestrators in Microsoft Azure</span></span>

<span data-ttu-id="f7a48-159">Plusieurs fournisseurs de cloud computing proposent une prise en charge des conteneurs Docker ainsi que les clusters de Docker et prise en charge de l’orchestration, y compris Microsoft Azure, Amazon EC2 conteneur de Service et le moteur de conteneur de Google.</span><span class="sxs-lookup"><span data-stu-id="f7a48-159">Several cloud vendors offer Docker containers support plus Docker clusters and orchestration support, including Microsoft Azure, Amazon EC2 Container Service, and Google Container Engine.</span></span> <span data-ttu-id="f7a48-160">Microsoft Azure offre Docker la prise en charge des clusters et orchestrator via conteneur de Service (ACS) Azure, comme expliqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="f7a48-160">Microsoft Azure provides Docker cluster and orchestrator support through Azure Container Service (ACS), as explained in the next section.</span></span>

<span data-ttu-id="f7a48-161">Un autre choix est d’utiliser Microsoft Azure Service Fabric (plateforme microservices), qui prend également en charge Docker basé sur les conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="f7a48-161">Another choice is to use Microsoft Azure Service Fabric (a microservices platform), which also supports Docker based on Linux and Windows Containers.</span></span> <span data-ttu-id="f7a48-162">L’infrastructure de service s’exécute sur Azure ou de n’importe quel autre cloud et s’exécute également [local](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span><span class="sxs-lookup"><span data-stu-id="f7a48-162">Service Fabric runs on Azure or any other cloud, and also runs [on-premises](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span></span>

## <a name="using-azure-container-service"></a><span data-ttu-id="f7a48-163">À l’aide du Service de conteneur Azure</span><span class="sxs-lookup"><span data-stu-id="f7a48-163">Using Azure Container Service</span></span>

<span data-ttu-id="f7a48-164">Un cluster de Docker regroupe plusieurs hôtes Docker et les expose sous un hôte Docker virtuel unique, afin de déployer plusieurs conteneurs dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="f7a48-164">A Docker cluster pools multiple Docker hosts and exposes them as a single virtual Docker host, so you can deploy multiple containers into the cluster.</span></span> <span data-ttu-id="f7a48-165">Le cluster gère tous les plomberie de gestion complexes, telles que l’évolutivité, intégrité et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f7a48-165">The cluster will handle all the complex management plumbing, like scalability, health, and so forth.</span></span> <span data-ttu-id="f7a48-166">Figure 4-24 représente la façon dont un cluster de Docker pour les applications composées mappe au conteneur de Service (ACS) Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-166">Figure 4-24 represents how a Docker cluster for composed applications maps to Azure Container Service (ACS).</span></span>

<span data-ttu-id="f7a48-167">ACS permet de simplifier la création, la configuration et la gestion d’un cluster d’ordinateurs virtuels qui sont préconfigurés pour exécuter des applications en conteneur.</span><span class="sxs-lookup"><span data-stu-id="f7a48-167">ACS provides a way to simplify the creation, configuration, and management of a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="f7a48-168">À l’aide d’une configuration optimisée des outils de planification et d’orchestration open source populaires, ACS vous permet d’utiliser vos compétences ou dessiner sur un corps important et croissant d’expertise de communauté pour déployer et gérer les applications basées sur le conteneur sur Microsoft Azure .</span><span class="sxs-lookup"><span data-stu-id="f7a48-168">Using an optimized configuration of popular open-source scheduling and orchestration tools, ACS enables you to use your existing skills or draw on a large and growing body of community expertise to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="f7a48-169">Service de conteneur Azure permet d’optimiser la configuration des outils open source de la gestion de clusters Docker et les technologies populaire spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-169">Azure Container Service optimizes the configuration of popular Docker clustering open source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="f7a48-170">Vous obtenez une solution ouverte qui offre la portabilité de vos conteneurs et configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="f7a48-170">You get an open solution that offers portability for both your containers and your application configuration.</span></span> <span data-ttu-id="f7a48-171">Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator et Service de conteneur gère tout le reste.</span><span class="sxs-lookup"><span data-stu-id="f7a48-171">You select the size, the number of hosts, and the orchestrator tools, and Container Service handles everything else.</span></span>

![](./media/image28.png)

<span data-ttu-id="f7a48-172">**Figure 4-24**.</span><span class="sxs-lookup"><span data-stu-id="f7a48-172">**Figure 4-24**.</span></span> <span data-ttu-id="f7a48-173">Clustering de choix dans le conteneur de Service Azure</span><span class="sxs-lookup"><span data-stu-id="f7a48-173">Clustering choices in Azure Container Service</span></span>

<span data-ttu-id="f7a48-174">ACS s’appuie sur les images Docker pour vous assurer que vos conteneurs d’applications sont entièrement portables.</span><span class="sxs-lookup"><span data-stu-id="f7a48-174">ACS leverages Docker images to ensure that your application containers are fully portable.</span></span> <span data-ttu-id="f7a48-175">Il prend en charge de votre choix des plateformes open source orchestration comme contrôleur de domaine/système d’exploitation (développé par Apache Mesos), Kubernetes (créé à l’origine par Google) et Docker Swarm, pour vous assurer que ces applications peuvent être mis à l’échelle et même des dizaines de milliers de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f7a48-175">It supports your choice of open-source orchestration platforms like DC/OS (powered by Apache Mesos), Kubernetes (originally created by Google), and Docker Swarm, to ensure that these applications can be scaled to thousands or even tens of thousands of containers.</span></span>

<span data-ttu-id="f7a48-176">Le service de conteneur Azure permet de tirer parti des fonctionnalités de niveau entreprise de Azure tout en conservant la portabilité des applications, y compris au niveau des couches d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="f7a48-176">The Azure Container service enables you to take advantage of the enterprise-grade features of Azure while still maintaining application portability, including at the orchestration layers.</span></span>

![](./media/image29.png)

<span data-ttu-id="f7a48-177">**Figure 4-25**.</span><span class="sxs-lookup"><span data-stu-id="f7a48-177">**Figure 4-25**.</span></span> <span data-ttu-id="f7a48-178">Orchestrators dans ACS</span><span class="sxs-lookup"><span data-stu-id="f7a48-178">Orchestrators in ACS</span></span>

<span data-ttu-id="f7a48-179">Comme indiqué dans la Figure 4-25, le Service de conteneur Azure est simplement l’infrastructure fournie par Azure pour déployer le contrôleur de domaine/système d’exploitation, Kubernetes ou Docker Swarm, mais des services ACS n’implémente pas de n’importe quel orchestrator supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f7a48-179">As shown in Figure 4-25, Azure Container Service is simply the infrastructure provided by Azure in order to deploy DC/OS, Kubernetes or Docker Swarm, but ACS does not implement any additional orchestrator.</span></span> <span data-ttu-id="f7a48-180">Par conséquent, ACS n’est pas un orchestrator donc uniquement une infrastructure qui tire parti des orchestrators open source existants pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f7a48-180">Therefore, ACS is not an orchestrator as such, only an infrastructure that leverages existing open-source orchestrators for containers.</span></span>

<span data-ttu-id="f7a48-181">À partir d’un point de vue de l’utilisation, de Service de conteneur Azure vise à fournir un environnement d’hébergement de conteneur à l’aide de technologies et outils open source populaires.</span><span class="sxs-lookup"><span data-stu-id="f7a48-181">From a usage perspective, the goal of Azure Container Service is to provide a container hosting environment by using popular open-source tools and technologies.</span></span> <span data-ttu-id="f7a48-182">À cette fin, elle expose les points de terminaison API standards pour votre orchestrator choisi.</span><span class="sxs-lookup"><span data-stu-id="f7a48-182">To this end, it exposes the standard API endpoints for your chosen orchestrator.</span></span> <span data-ttu-id="f7a48-183">À l’aide de ces points de terminaison, vous pouvez exploiter tout logiciel qui peut communiquer avec ces points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f7a48-183">By using these endpoints, you can leverage any software that can talk to those endpoints.</span></span> <span data-ttu-id="f7a48-184">Par exemple, dans le cas le point de terminaison Docker Swarm, vous pouvez choisir d’utiliser l’interface de ligne de commande Docker (CLI).</span><span class="sxs-lookup"><span data-stu-id="f7a48-184">For example, in the case of the Docker Swarm endpoint, you might choose to use the Docker command-line interface (CLI).</span></span> <span data-ttu-id="f7a48-185">Pour le contrôleur de domaine/système d’exploitation, vous pouvez choisir d’utiliser l’interface CLI de contrôleur de domaine/système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f7a48-185">For DC/OS, you might choose to use the DC/OS CLI.</span></span>

### <a name="getting-started-with-azure-container-service"></a><span data-ttu-id="f7a48-186">Mise en route avec le Service de conteneur Azure</span><span class="sxs-lookup"><span data-stu-id="f7a48-186">Getting started with Azure Container Service</span></span> 

<span data-ttu-id="f7a48-187">Pour commencer à utiliser le Service de conteneur Azure, vous déployez un cluster du Service de conteneur Azure à partir du portail Azure à l’aide d’un modèle Azure Resource Manager ou le [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="f7a48-187">To begin using Azure Container Service, you deploy an Azure Container Service cluster from the Azure portal by using an Azure Resource Manager template or the [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span></span> <span data-ttu-id="f7a48-188">Les modèles disponibles incluent [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), et [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span><span class="sxs-lookup"><span data-stu-id="f7a48-188">Available templates include [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), and [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span></span> <span data-ttu-id="f7a48-189">Les modèles de démarrage rapide peuvent être modifiés pour inclure les configuration d’Azure supplémentaire ou avancée.</span><span class="sxs-lookup"><span data-stu-id="f7a48-189">The quickstart templates can be modified to include additional or advanced Azure configuration.</span></span> <span data-ttu-id="f7a48-190">Pour plus d’informations sur le déploiement d’un cluster du Service de conteneur Azure, consultez [déployer un cluster du Service de conteneur Azure](https://docs.microsoft.com/azure/container-service/container-service-deployment) sur le site Web Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-190">For more information on deploying an Azure Container Service cluster, see [Deploy an Azure Container Service cluster](https://docs.microsoft.com/azure/container-service/container-service-deployment) on the Azure website.</span></span>

<span data-ttu-id="f7a48-191">Il n’existe aucun frais pour les logiciels installés par défaut dans le cadre des services ACS.</span><span class="sxs-lookup"><span data-stu-id="f7a48-191">There are no fees for any of the software installed by default as part of ACS.</span></span> <span data-ttu-id="f7a48-192">Toutes les options par défaut sont implémentées avec des logiciels open source.</span><span class="sxs-lookup"><span data-stu-id="f7a48-192">All default options are implemented with open-source software.</span></span>

<span data-ttu-id="f7a48-193">ACS est actuellement disponible pour la série A Standard, D, DS, G et GS ordinateurs virtuels Linux dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f7a48-193">ACS is currently available for Standard A, D, DS, G, and GS series Linux virtual machines in Azure.</span></span> <span data-ttu-id="f7a48-194">Vous payez uniquement pour les instances de calcul que vous choisissez, ainsi que les autres ressources infrastructure sous-jacente consommés, telles que la mise en réseau et de stockage.</span><span class="sxs-lookup"><span data-stu-id="f7a48-194">You are charged only for the compute instances you choose, as well as the other underlying infrastructure resources consumed, such as storage and networking.</span></span> <span data-ttu-id="f7a48-195">Il n’existe aucun frais incrémentielles pour les services ACS lui-même.</span><span class="sxs-lookup"><span data-stu-id="f7a48-195">There are no incremental charges for ACS itself.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f7a48-196">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f7a48-196">Additional resources</span></span>

-   <span data-ttu-id="f7a48-197">**Introduction au conteneur Docker hébergeant des solutions avec le Service de conteneur Azure**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span><span class="sxs-lookup"><span data-stu-id="f7a48-197">**Introduction to Docker container hosting solutions with Azure Container Service**
[*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span></span>

-   <span data-ttu-id="f7a48-198">**Vue d’ensemble de docker essaim**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span><span class="sxs-lookup"><span data-stu-id="f7a48-198">**Docker Swarm overview**
[*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span></span>

-   <span data-ttu-id="f7a48-199">**Vue d’ensemble du mode de swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span><span class="sxs-lookup"><span data-stu-id="f7a48-199">**Swarm mode overview**
[*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span></span>

-   <span data-ttu-id="f7a48-200">**Vue d’ensemble du contrôleur de domaine/système d’exploitation mésosphère**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span><span class="sxs-lookup"><span data-stu-id="f7a48-200">**Mesosphere DC/OS Overview**
[*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span></span>

-   <span data-ttu-id="f7a48-201">**Kubernetes.**</span><span class="sxs-lookup"><span data-stu-id="f7a48-201">**Kubernetes.**</span></span> <span data-ttu-id="f7a48-202">Le site officiel. \\</span><span class="sxs-lookup"><span data-stu-id="f7a48-202">The official site.\\</span></span>
    [<span data-ttu-id="f7a48-203">*http://kubernetes.IO/*</span><span class="sxs-lookup"><span data-stu-id="f7a48-203">*http://kubernetes.io/*</span></span>](http://kubernetes.io/)


>[!div class="step-by-step"]
<span data-ttu-id="f7a48-204">[Précédente] (résilient-haute-disponibilité-microservices.md) [suivant] (à l’aide de-azure-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="f7a48-204">[Previous] (resilient-high-availability-microservices.md) [Next] (using-azure-service-fabric.md)</span></span>