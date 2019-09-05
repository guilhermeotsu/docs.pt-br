---
title: Arquitetura sem servidor-aplicativos sem servidor
description: Exploração de várias arquiteturas e aplicativos que têm suporte de arquiteturas sem servidor, incluindo aplicativos Web, dispositivos móveis e IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3b22fecfdc693154dbdeb3e872e0e246e8ca41f9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577349"
---
# <a name="serverless-architecture"></a><span data-ttu-id="a2d7c-103">Arquitetura sem servidor</span><span class="sxs-lookup"><span data-stu-id="a2d7c-103">Serverless architecture</span></span>

<span data-ttu-id="a2d7c-104">Há muitas abordagens ao uso de arquiteturas sem [servidor](https://azure.com/serverless) .</span><span class="sxs-lookup"><span data-stu-id="a2d7c-104">There are many approaches to using [serverless](https://azure.com/serverless) architectures.</span></span> <span data-ttu-id="a2d7c-105">Este capítulo explora exemplos de arquiteturas comuns que se integram sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-105">This chapter explores examples of common architectures that integrate serverless.</span></span> <span data-ttu-id="a2d7c-106">Ele também aborda preocupações que podem apresentar desafios adicionais ou exigir uma consideração extra ao implementar sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-106">It also covers concerns that may pose additional challenges or require extra consideration when implementing serverless.</span></span> <span data-ttu-id="a2d7c-107">Por fim, são fornecidos vários exemplos de design que ilustram vários casos de uso sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-107">Finally, several design examples are provided that illustrate various serverless use cases.</span></span>

<span data-ttu-id="a2d7c-108">Os hosts sem servidor geralmente usam uma camada de PaaS ou baseada em contêiner existente para gerenciar as instâncias sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-108">Serverless hosts often use an existing container-based or PaaS layer to manage the serverless instances.</span></span> <span data-ttu-id="a2d7c-109">Por exemplo, Azure Functions se baseia no [serviço Azure app](https://docs.microsoft.com/azure/app-service/).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-109">For example, Azure Functions is based on [Azure App Service](https://docs.microsoft.com/azure/app-service/).</span></span> <span data-ttu-id="a2d7c-110">O serviço de aplicativo é usado para expandir instâncias e gerenciar o tempo de execução que executa Azure Functions código.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-110">The App Service is used to scale out instances and manage the runtime that executes Azure Functions code.</span></span> <span data-ttu-id="a2d7c-111">Para funções baseadas no Windows, o host é executado como PaaS e dimensiona o tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-111">For Windows-based functions, the host runs as PaaS and scales out the .NET runtime.</span></span> <span data-ttu-id="a2d7c-112">Para funções baseadas em Linux, o host aproveita contêineres.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-112">For Linux-based functions, the host leverages containers.</span></span>

![Arquitetura de Azure Functions](./media/azure-functions-architecture.png)

<span data-ttu-id="a2d7c-114">O núcleo de trabalhos Web fornece um contexto de execução para a função.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-114">The WebJobs Core provides an execution context for the function.</span></span> <span data-ttu-id="a2d7c-115">O Language Runtime executa scripts, executa bibliotecas e hospeda a estrutura para o idioma de destino.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-115">The Language Runtime runs scripts, executes libraries and hosts the framework for the target language.</span></span> <span data-ttu-id="a2d7c-116">Por exemplo, Node. js é usado para executar funções JavaScript e o .NET Framework é usado para executar C# funções.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-116">For example, Node.js is used to run JavaScript functions and the .NET Framework is used to run C# functions.</span></span> <span data-ttu-id="a2d7c-117">Você aprenderá mais sobre as opções de linguagem e plataforma mais adiante neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-117">You'll learn more about language and platform options later in this chapter.</span></span>

<span data-ttu-id="a2d7c-118">Alguns projetos podem se beneficiar com a criação de uma abordagem "tudo" para servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-118">Some projects may benefit from taking an "all-in" approach to serverless.</span></span> <span data-ttu-id="a2d7c-119">Os aplicativos que dependem muito de microservices podem implementar todos os microserviços usando a tecnologia sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-119">Applications that rely heavily on microservices may implement all microservices using serverless technology.</span></span> <span data-ttu-id="a2d7c-120">A maioria dos aplicativos é híbrida, seguindo um projeto de N camadas e usando servidores para os componentes que fazem sentido, pois os componentes são modulares e escalonáveis de forma independente.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-120">The majority of apps are hybrid, following an N-tier design and using serverless for the components that make sense because the components are modular and independently scalable.</span></span> <span data-ttu-id="a2d7c-121">Para ajudar a entender esses cenários, esta seção descreve alguns exemplos comuns de arquitetura que usam sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-121">To help make sense of these scenarios, this section walks through some common architecture examples that use serverless.</span></span>

## <a name="full-serverless-back-end"></a><span data-ttu-id="a2d7c-122">Back-end completo sem servidor</span><span class="sxs-lookup"><span data-stu-id="a2d7c-122">Full serverless back end</span></span>

<span data-ttu-id="a2d7c-123">O back-end completo sem servidor é ideal para vários tipos de cenários, especialmente ao criar aplicativos novos ou "de campo verde".</span><span class="sxs-lookup"><span data-stu-id="a2d7c-123">The full serverless back end is ideal for several types of scenarios, especially when building new or "green field" applications.</span></span> <span data-ttu-id="a2d7c-124">Um aplicativo com uma grande área de superfície de APIs pode se beneficiar da implementação de cada API como uma função sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-124">An application with a large surface area of APIs may benefit from implementing each API as a serverless function.</span></span> <span data-ttu-id="a2d7c-125">Aplicativos baseados na arquitetura de microserviços são outro exemplo que podem ser implementados como um back-end completo sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-125">Apps that are based on microservices architecture are another example that could be implemented as a full serverless back end.</span></span> <span data-ttu-id="a2d7c-126">Os microserviços se comunicam por vários protocolos entre si.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-126">The microservices communicate over various protocols with each other.</span></span> <span data-ttu-id="a2d7c-127">Os cenários específicos incluem:</span><span class="sxs-lookup"><span data-stu-id="a2d7c-127">Specific scenarios include:</span></span>

* <span data-ttu-id="a2d7c-128">Produtos SaaS baseados em API (exemplo: processador de pagamentos financeiros).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-128">API-based SaaS products (example: financial payments processor).</span></span>
* <span data-ttu-id="a2d7c-129">Aplicativos orientados a mensagens (exemplo: solução de monitoramento de dispositivo).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-129">Message-driven applications (example: device monitoring solution).</span></span>
* <span data-ttu-id="a2d7c-130">Aplicativos focados na integração entre serviços (exemplo: aplicativo de reservas de viagens).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-130">Apps focused on integration between services (example: airline booking application).</span></span>
* <span data-ttu-id="a2d7c-131">Processos que são executados periodicamente (exemplo: limpeza de banco de dados baseada em temporizador).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-131">Processes that run periodically (example: timer-based database clean-up).</span></span>
* <span data-ttu-id="a2d7c-132">Aplicativos focados na transformação de dados (exemplo: importação disparada por upload de arquivo).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-132">Apps focused on data transformation (example: import triggered by file upload).</span></span>
* <span data-ttu-id="a2d7c-133">Extrair processos de ETL (transformação e carregamento).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-133">Extract Transform and Load (ETL) processes.</span></span>

<span data-ttu-id="a2d7c-134">Há outros casos de uso mais específicos que são abordados posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-134">There are other, more specific use cases that are covered later in this document.</span></span>

## <a name="monoliths-and-starving-the-beast"></a><span data-ttu-id="a2d7c-135">Monolítico e "privando o fera"</span><span class="sxs-lookup"><span data-stu-id="a2d7c-135">Monoliths and "starving the beast"</span></span>

<span data-ttu-id="a2d7c-136">Um desafio comum é migrar um aplicativo monolítico existente para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-136">A common challenge is migrating an existing monolithic application to the cloud.</span></span> <span data-ttu-id="a2d7c-137">A abordagem menos arriscada é "mover e deslocar" totalmente para máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-137">The least risky approach is to "lift and shift" entirely onto virtual machines.</span></span> <span data-ttu-id="a2d7c-138">Muitas lojas preferem usar a migração como uma oportunidade de modernizar sua base de código.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-138">Many shops prefer to use the migration as an opportunity to modernize their code base.</span></span> <span data-ttu-id="a2d7c-139">Uma abordagem prática para a migração é chamada de "privar o fera".</span><span class="sxs-lookup"><span data-stu-id="a2d7c-139">A practical approach to migration is called "starving the beast."</span></span> <span data-ttu-id="a2d7c-140">Nesse cenário, o monolítico é migrado "no estado em que se encontra" para começar.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-140">In this scenario, the monolith is migrated "as is" to start with.</span></span> <span data-ttu-id="a2d7c-141">Em seguida, os serviços selecionados são modernizados.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-141">Then, selected services are modernized.</span></span> <span data-ttu-id="a2d7c-142">Em alguns casos, a assinatura do serviço é idêntica à original: ela simplesmente é hospedada como uma função.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-142">In some cases, the signature of the service is identical to the original: it simply is hosted as a function.</span></span> <span data-ttu-id="a2d7c-143">Os clientes são atualizados para usar o novo serviço em vez do ponto de extremidade monolítico.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-143">Clients are updated to use the new service rather than the monolith endpoint.</span></span> <span data-ttu-id="a2d7c-144">No ínterim, as etapas como replicação de banco de dados permitem que os microserviços hospedem seu próprio armazenamento mesmo quando as transações ainda são tratadas pelo monolítico.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-144">In the interim, steps such as database replication enable microservices to host their own storage even when transactions are still handled by the monolith.</span></span> <span data-ttu-id="a2d7c-145">Eventualmente, todos os clientes são migrados para os novos serviços.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-145">Eventually, all clients are migrated onto the new services.</span></span> <span data-ttu-id="a2d7c-146">O monolítico é "privado" (seus serviços não são mais chamados) até que toda a funcionalidade tenha sido substituída.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-146">The monolith is "starved" (its services no longer called) until all functionality has been replaced.</span></span> <span data-ttu-id="a2d7c-147">A combinação de proxies e sem servidor pode facilitar grande parte dessa migração.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-147">The combination of serverless and proxies can facilitate much of this migration.</span></span>

![Migração monolítica sem servidor](./media/serverless-monolith-migration.png)

<span data-ttu-id="a2d7c-149">Para saber mais sobre essa abordagem, Assista ao vídeo: [Traga seu aplicativo para a nuvem com Azure Functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-149">To learn more about this approach, watch the video: [Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span>

## <a name="web-apps"></a><span data-ttu-id="a2d7c-150">Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="a2d7c-150">Web apps</span></span>

<span data-ttu-id="a2d7c-151">Os aplicativos Web são excelentes candidatos para aplicativos sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-151">Web apps are great candidates for serverless applications.</span></span> <span data-ttu-id="a2d7c-152">Atualmente, há duas abordagens comuns para aplicativos Web: orientado por servidor e controlado por cliente (como um aplicativo de página única ou SPA).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-152">There are two common approaches to web apps today: server-driven, and client-driven (such as Single Page Application or SPA).</span></span> <span data-ttu-id="a2d7c-153">Aplicativos Web baseados em servidor normalmente usam uma camada de middleware para emitir chamadas de API para renderizar a interface do usuário da Web.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-153">Server-driven web apps typically use a middleware layer to issue API calls to render the web UI.</span></span> <span data-ttu-id="a2d7c-154">Os aplicativos SPA fazem chamadas à API REST diretamente do navegador.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-154">SPA applications make REST API calls directly from the browser.</span></span> <span data-ttu-id="a2d7c-155">Em ambos os cenários, o servidor pode acomodar o middleware ou a solicitação da API REST fornecendo a lógica comercial necessária.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-155">In both scenarios, serverless can accommodate the middleware or REST API request by providing the necessary business logic.</span></span> <span data-ttu-id="a2d7c-156">Uma arquitetura comum é criar um servidor Web estático leve.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-156">A common architecture is to stand up a lightweight static web server.</span></span> <span data-ttu-id="a2d7c-157">O aplicativo de página única (SPA) serve HTML, CSS, JavaScript e outros ativos de navegador.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-157">The Single Page Application (SPA) serves HTML, CSS, JavaScript, and other browser assets.</span></span> <span data-ttu-id="a2d7c-158">O aplicativo Web então se conecta a um back-end de microserviço.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-158">The web app then connects to a microservices back end.</span></span>

## <a name="mobile-back-ends"></a><span data-ttu-id="a2d7c-159">Back-ends móveis</span><span class="sxs-lookup"><span data-stu-id="a2d7c-159">Mobile back ends</span></span>

<span data-ttu-id="a2d7c-160">O paradigma controlado por eventos de aplicativos sem servidor os torna ideal como back-ends móveis.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-160">The event-driven paradigm of serverless apps makes them ideal as mobile back ends.</span></span> <span data-ttu-id="a2d7c-161">O dispositivo móvel dispara os eventos e o código sem servidor é executado para atender a solicitações.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-161">The mobile device triggers the events and the serverless code executes to satisfy requests.</span></span> <span data-ttu-id="a2d7c-162">Tirar proveito de um modelo sem servidor permite que os desenvolvedores aprimorem a lógica de negócios sem precisar implantar uma atualização completa do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-162">Taking advantage of a serverless model enables developers to enhance business logic without having to deploy a full application update.</span></span> <span data-ttu-id="a2d7c-163">A abordagem sem servidor também permite que as equipes compartilhem pontos de extremidade e trabalhem em paralelo.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-163">The serverless approach also enables teams to share endpoints and work in parallel.</span></span>

<span data-ttu-id="a2d7c-164">Os desenvolvedores móveis podem criar lógica de negócios sem se tornar especialistas no lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-164">Mobile developers can build business logic without becoming experts on the server side.</span></span> <span data-ttu-id="a2d7c-165">Tradicionalmente, os aplicativos móveis conectados a serviços locais.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-165">Traditionally, mobile apps connected to on-premises services.</span></span> <span data-ttu-id="a2d7c-166">Criar a camada de serviço exigida entendendo a plataforma do servidor e o paradigma de programação.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-166">Building the service layer required understanding the server platform and programming paradigm.</span></span> <span data-ttu-id="a2d7c-167">Os desenvolvedores trabalharam com operações para provisionar servidores e configurá-los adequadamente.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-167">Developers worked with operations to provision servers and configure them appropriately.</span></span> <span data-ttu-id="a2d7c-168">Às vezes, dias ou até mesmo semanas foram gastos na criação de um pipeline de implantação.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-168">Sometimes days or even weeks were spent on building a deployment pipeline.</span></span> <span data-ttu-id="a2d7c-169">Todos esses desafios são abordados por servidor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-169">All of these challenges are addressed by serverless.</span></span>

<span data-ttu-id="a2d7c-170">Sem servidor abstrai as dependências do lado do servidor e permite que o desenvolvedor se concentre na lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-170">Serverless abstracts the server-side dependencies and enables the developer to focus on business logic.</span></span> <span data-ttu-id="a2d7c-171">Por exemplo, um desenvolvedor móvel que cria aplicativos usando uma estrutura JavaScript também pode criar funções sem servidor com JavaScript.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-171">For example, a mobile developer who builds apps using a JavaScript framework can build serverless functions with JavaScript as well.</span></span> <span data-ttu-id="a2d7c-172">O host sem servidor gerencia o sistema operacional, uma instância do node. js para hospedar o código, as dependências do pacote e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-172">The serverless host manages the operating system, a Node.js instance to host the code, package dependencies, and more.</span></span> <span data-ttu-id="a2d7c-173">O desenvolvedor recebe um conjunto simples de entradas e um modelo padrão para saídas.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-173">The developer is provided a simple set of inputs and a standard template for outputs.</span></span> <span data-ttu-id="a2d7c-174">Em seguida, eles podem se concentrar na criação e no teste da lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-174">They then can focus on building and testing the business logic.</span></span> <span data-ttu-id="a2d7c-175">Portanto, eles são capazes de usar habilidades existentes para criar a lógica de back-end para o aplicativo móvel sem precisar aprender novas plataformas ou se tornar um "desenvolvedor do lado do servidor".</span><span class="sxs-lookup"><span data-stu-id="a2d7c-175">They're therefore able to use existing skills to build the back-end logic for the mobile app without having to learn new platforms or become a "server-side developer."</span></span>

![Back-end móvel sem servidor](./media/serverless-mobile-backend.png)

<span data-ttu-id="a2d7c-177">A maioria dos provedores de nuvem oferece produtos sem servidor baseados em móveis que simplificam todo o ciclo de vida do desenvolvimento móvel.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-177">Most cloud providers offer mobile-based serverless products that simplify the entire mobile development lifecycle.</span></span> <span data-ttu-id="a2d7c-178">Os produtos podem automatizar o provisionamento de bancos de dados para persistirem, lidar com preocupações DevOpss, fornecer compilações baseadas em nuvem e estruturas de teste e a capacidade de gerar scripts de processos comerciais usando a linguagem preferencial do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-178">The products may automate the provisioning of databases to persist data, handle DevOps concerns, provide cloud-based builds and testing frameworks and the ability to script business processes using the developer's preferred language.</span></span> <span data-ttu-id="a2d7c-179">Seguir uma abordagem sem servidor voltada para dispositivos móveis pode simplificar o processo.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-179">Following a mobile-centric serverless approach can streamline the process.</span></span> <span data-ttu-id="a2d7c-180">Sem servidor remove a enorme sobrecarga de provisionamento, configuração e manutenção de servidores para o back-end móvel.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-180">Serverless removes the tremendous overhead of provisioning, configuring, and maintaining servers for the mobile back end.</span></span>

## <a name="internet-of-things-iot"></a><span data-ttu-id="a2d7c-181">IoT (Internet das Coisas)</span><span class="sxs-lookup"><span data-stu-id="a2d7c-181">Internet of Things (IoT)</span></span>

<span data-ttu-id="a2d7c-182">A IoT refere-se a objetos físicos que estão em rede.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-182">IoT refers to physical objects that are networked together.</span></span> <span data-ttu-id="a2d7c-183">Às vezes, eles são chamados de "dispositivos conectados" ou "dispositivos inteligentes".</span><span class="sxs-lookup"><span data-stu-id="a2d7c-183">They're sometimes referred to as "connected devices" or "smart devices."</span></span> <span data-ttu-id="a2d7c-184">Tudo, desde carros e máquinas de vendas, pode estar conectado e enviar informações que vão desde o inventário até dados de sensor, como temperatura e umidade.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-184">Everything from cars and vending machines may be connected and send information ranging from inventory to sensor data such as temperature and humidity.</span></span> <span data-ttu-id="a2d7c-185">Na empresa, a IoT fornece melhorias de processos de negócios por meio de monitoramento e automação.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-185">In the enterprise, IoT provides business process improvements through monitoring and automation.</span></span> <span data-ttu-id="a2d7c-186">Os dados de IoT podem ser usados para regulamentar o clima em um grande depósito ou acompanhar o inventário por meio da cadeia de suprimentos.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-186">IoT data may be used to regulate the climate in a large warehouse or track inventory through the supply chain.</span></span> <span data-ttu-id="a2d7c-187">A IoT pode detectar derramamentos químicos e chamar o departamento de incêndio quando a fumaça for detectada.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-187">IoT can sense chemical spills and call the fire department when smoke is detected.</span></span>

<span data-ttu-id="a2d7c-188">O enorme volume de dispositivos e informações geralmente determina uma arquitetura orientada por eventos para rotear e processar mensagens.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-188">The sheer volume of devices and information often dictates an event-driven architecture to route and process messages.</span></span> <span data-ttu-id="a2d7c-189">Sem servidor é uma solução ideal por vários motivos:</span><span class="sxs-lookup"><span data-stu-id="a2d7c-189">Serverless is an ideal solution for several reasons:</span></span>

* <span data-ttu-id="a2d7c-190">Habilita o dimensionamento conforme o volume de dispositivos e dados aumenta.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-190">Enables scale as the volume of devices and data increases.</span></span>
* <span data-ttu-id="a2d7c-191">Acomoda a adição de novos pontos de extremidade para dar suporte a novos dispositivos e sensores.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-191">Accommodates adding new endpoints to support new devices and sensors.</span></span>
* <span data-ttu-id="a2d7c-192">Facilita o controle de versão independente para que os desenvolvedores possam atualizar a lógica de negócios de um dispositivo específico sem precisar implantar o sistema inteiro.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-192">Facilitates independent versioning so developers can update the business logic for a specific device without having to deploy the entire system.</span></span>
* <span data-ttu-id="a2d7c-193">Resiliência e menos tempo de inatividade.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-193">Resiliency and less downtime.</span></span>

<span data-ttu-id="a2d7c-194">A disseminação da IoT resultou em vários produtos sem servidor que se concentram especificamente em preocupações com a IoT, como o [Hub IOT do Azure](https://docs.microsoft.com/azure/iot-hub).</span><span class="sxs-lookup"><span data-stu-id="a2d7c-194">The pervasiveness of IoT has resulted in several serverless products that focus specifically on IoT concerns, such as [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub).</span></span> <span data-ttu-id="a2d7c-195">O servidor automatiza tarefas como registro de dispositivos, imposição de políticas, acompanhamento e até mesmo implantação de código para dispositivos na *borda*.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-195">Serverless automates tasks such as device registration, policy enforcement, tracking, and even deployment of code to devices at *the edge*.</span></span> <span data-ttu-id="a2d7c-196">A borda se refere a dispositivos como sensores e atuadores que estão conectados a, mas não a uma parte ativa do, à Internet.</span><span class="sxs-lookup"><span data-stu-id="a2d7c-196">The edge refers to devices like sensors and actuators that are connected to, but not an active part of, the Internet.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a2d7c-197">[Anterior](architecture-approaches.md)
>[Próximo](serverless-architecture-considerations.md)</span><span class="sxs-lookup"><span data-stu-id="a2d7c-197">[Previous](architecture-approaches.md)
[Next](serverless-architecture-considerations.md)</span></span>