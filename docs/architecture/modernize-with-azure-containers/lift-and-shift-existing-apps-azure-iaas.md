---
title: Migrar e deslocar aplicativos .NET existentes para IaaS do Azure (pronto para infraestrutura de nuvem)
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure.
ms.date: 04/28/2018
ms.openlocfilehash: e25ddbf9b6e62c264f3f4d4580d7df3553d262ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660746"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="bbee5-103">Migrar e deslocar aplicativos .NET existentes para IaaS do Azure (pronto para infraestrutura de nuvem)</span><span class="sxs-lookup"><span data-stu-id="bbee5-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="bbee5-104">Visão: Como uma primeira etapa, para reduzir seu investimento local e o custo total de manutenção de hardware e rede, basta hospedar novamente os aplicativos existentes na nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="bbee5-105">Antes de entrar em *como* migrar seus aplicativos existentes para a plataforma IaaS (infraestrutura como serviço) do Azure, é importante analisar os motivos pelos *quais* você desejaria migrar diretamente para o IaaS no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="bbee5-106">O cenário nesse nível de maturidade de modernização essencialmente é começar a usar VMs na nuvem, em vez de continuar a usar sua infraestrutura local atual.</span><span class="sxs-lookup"><span data-stu-id="bbee5-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="bbee5-107">Outro ponto a ser analisado é *por que* você pode desejar migrar para a nuvem de IaaS pura em vez de apenas adicionar serviços gerenciados avançados no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="bbee5-108">Determine quais casos podem exigir IaaS em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="bbee5-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="bbee5-109">A Figura 2-1 posiciona os aplicativos prontos para a infraestrutura de nuvem nos níveis de maturidade de modernização:</span><span class="sxs-lookup"><span data-stu-id="bbee5-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Posicionando aplicativos prontos para a infraestrutura de nuvem](./media/image2-1.png)

> <span data-ttu-id="bbee5-111">**Figura 2-1.**</span><span class="sxs-lookup"><span data-stu-id="bbee5-111">**Figure 2-1.**</span></span> <span data-ttu-id="bbee5-112">Posicionando aplicativos prontos para a infraestrutura de nuvem</span><span class="sxs-lookup"><span data-stu-id="bbee5-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="bbee5-113">Por que migrar aplicativos Web .NET existentes para IaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="bbee5-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="bbee5-114">O principal motivo para migrar para a nuvem, mesmo em um nível de IaaS inicial, é obter reduções de custo.</span><span class="sxs-lookup"><span data-stu-id="bbee5-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="bbee5-115">Com o uso de serviços de infraestrutura mais gerenciados, sua organização pode reduzir seu investimento em manutenção de hardware, provisionamento e implantação de servidor ou VM e gerenciamento de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="bbee5-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="bbee5-116">Depois de tomar a decisão de mover seus aplicativos para a nuvem, o principal motivo pelo qual você pode escolher IaaS em vez de opções mais avançadas, como PaaS, é simplesmente que o ambiente de IaaS será mais familiar.</span><span class="sxs-lookup"><span data-stu-id="bbee5-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="bbee5-117">Mover para um ambiente semelhante ao seu ambiente local atual oferece uma curva de aprendizado mais baixa, o que o torna o caminho mais rápido para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="bbee5-118">No entanto, usar o caminho mais rápido para a nuvem não significa que você obterá mais benefícios em ter seus aplicativos em execução na nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="bbee5-119">Qualquer organização obterá os benefícios mais significativos de uma migração na nuvem nos níveis de maturidade já introduzidos e nativos da nuvem e otimizados para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="bbee5-120">Também se tornou evidente que os aplicativos são mais fáceis de modernizar e rearquitetar no futuro quando já estão em execução na nuvem, mesmo no IaaS.</span><span class="sxs-lookup"><span data-stu-id="bbee5-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="bbee5-121">A migração de dados de aplicativos já foi atingida.</span><span class="sxs-lookup"><span data-stu-id="bbee5-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="bbee5-122">Além disso, sua organização terá adquirido as habilidades necessárias para trabalhar na nuvem e fazer a mudança para operar em uma "cultura de nuvem".</span><span class="sxs-lookup"><span data-stu-id="bbee5-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="bbee5-123">Quando migrar para IaaS em vez de para PaaS</span><span class="sxs-lookup"><span data-stu-id="bbee5-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="bbee5-124">As seções a seguir discutem aplicativos otimizados para a nuvem que são basicamente baseados em plataformas e serviços de PaaS.</span><span class="sxs-lookup"><span data-stu-id="bbee5-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="bbee5-125">Esses aplicativos oferecem a você a maior vantagem de migrar para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-125">These apps give you the most benefits from migrating to the cloud.</span></span> 

<span data-ttu-id="bbee5-126">Se sua meta é simplesmente mover os aplicativos existentes para a nuvem, primeiro, identifique os aplicativos existentes que não exigem modificação substancial para serem executados no serviço de Azure App.</span><span class="sxs-lookup"><span data-stu-id="bbee5-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="bbee5-127">Esses aplicativos devem ser os primeiros candidatos para a otimização da nuvem.</span><span class="sxs-lookup"><span data-stu-id="bbee5-127">These apps should be the first candidates for Cloud-Optimized.</span></span> 

<span data-ttu-id="bbee5-128">Em seguida, para os aplicativos que ainda não podem ser movidos para contêineres do Windows e PaaS, como serviço de aplicativo ou orquestradores como o serviço kubernetes do Azure, migre-os para VMs simples (IaaS).</span><span class="sxs-lookup"><span data-stu-id="bbee5-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span> 

<span data-ttu-id="bbee5-129">Mas lembre-se de que configurar, proteger e manter corretamente as VMs requer muito mais tempo e experiência de ti em comparação com o uso de serviços de PaaS no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="bbee5-130">Se você estiver considerando as máquinas virtuais do Azure, certifique-se de levar em conta o esforço de manutenção em andamento necessário para corrigir, atualizar e gerenciar seu ambiente de VM.</span><span class="sxs-lookup"><span data-stu-id="bbee5-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="bbee5-131">As máquinas virtuais do Azure são IaaS.</span><span class="sxs-lookup"><span data-stu-id="bbee5-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="bbee5-132">Usar as migrações para Azure para analisar e migrar seus aplicativos existentes para o Azure</span><span class="sxs-lookup"><span data-stu-id="bbee5-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="bbee5-133">A migração para a nuvem não precisa ser difícil.</span><span class="sxs-lookup"><span data-stu-id="bbee5-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="bbee5-134">Mas muitas organizações lutam para começar-a obter uma visibilidade profunda do ambiente e as forte interdependências entre aplicativos, cargas de trabalho e dados.</span><span class="sxs-lookup"><span data-stu-id="bbee5-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="bbee5-135">Sem essa visibilidade, pode ser difícil planejar o caminho para a frente.</span><span class="sxs-lookup"><span data-stu-id="bbee5-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="bbee5-136">Sem informações detalhadas sobre o que é necessário para uma migração bem-sucedida, você não pode ter as conversas certas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="bbee5-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="bbee5-137">Você não sabe o suficiente sobre os benefícios de custo potencial ou se as cargas de trabalho poderiam apenas ser comparadas e trocadas ou exigiriam um retrabalho significativo para migrar com êxito.</span><span class="sxs-lookup"><span data-stu-id="bbee5-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="bbee5-138">Não se perguntou que muitas organizações hesitam.</span><span class="sxs-lookup"><span data-stu-id="bbee5-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="bbee5-139">As migrações para [Azure](https://aka.ms/azuremigrate) são um novo serviço que fornece as diretrizes, as informações e os mecanismos necessários para ajudá-lo a migrar para o Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="bbee5-140">As migrações para Azure fornecem:</span><span class="sxs-lookup"><span data-stu-id="bbee5-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="bbee5-141">Descoberta e avaliação para máquinas virtuais locais</span><span class="sxs-lookup"><span data-stu-id="bbee5-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="bbee5-142">Mapeamento de dependências embutidas para a descoberta de alta confiança de aplicativos de várias camadas</span><span class="sxs-lookup"><span data-stu-id="bbee5-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="bbee5-143">Dimensionamento de direito inteligente para máquinas virtuais do Azure</span><span class="sxs-lookup"><span data-stu-id="bbee5-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="bbee5-144">Relatórios de compatibilidade com diretrizes para correção de possíveis problemas</span><span class="sxs-lookup"><span data-stu-id="bbee5-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="bbee5-145">Integração ao serviço de gerenciamento de banco de dados do Azure para migração e descoberta de banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbee5-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="bbee5-146">As migrações para Azure dão a você confiança de que suas cargas de trabalho podem migrar com impacto mínimo sobre os negócios e são executados conforme o esperado no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="bbee5-147">Com as ferramentas e as diretrizes certas, você pode obter o máximo de retorno sobre o investimento, garantindo que as necessidades críticas de desempenho e confiabilidade sejam atendidas.</span><span class="sxs-lookup"><span data-stu-id="bbee5-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="bbee5-148">A Figura 2-2 mostra o mapeamento de dependência interno para todas as conexões de servidor e aplicativo executadas pelas migrações para Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Posicionando aplicativos prontos para a infraestrutura de nuvem](./media/image2-2.png)

> <span data-ttu-id="bbee5-150">**Figura 2-2**.</span><span class="sxs-lookup"><span data-stu-id="bbee5-150">**Figure 2-2.**</span></span> <span data-ttu-id="bbee5-151">Posicionando aplicativos prontos para a infraestrutura de nuvem</span><span class="sxs-lookup"><span data-stu-id="bbee5-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="bbee5-152">Usar Azure Site Recovery para migrar suas VMs existentes para VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="bbee5-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="bbee5-153">Como parte da migração de ponta a ponta [do Azure](https://aka.ms/azuremigrate), [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) é uma ferramenta que você pode usar para migrar facilmente seus aplicativos Web para VMs no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="bbee5-154">Você pode usar Site Recovery para replicar VMs locais e servidores físicos para o Azure ou para replicá-los para um local secundário localmente.</span><span class="sxs-lookup"><span data-stu-id="bbee5-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="bbee5-155">Você pode até mesmo replicar uma carga de trabalho que está sendo executada em uma VM do Azure com suporte, em uma VM do *Hyper-V* local, em uma VM do *VMware* ou em um servidor físico Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="bbee5-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="bbee5-156">A replicação para o Azure elimina o custo e a complexidade de manter um datacenter secundário.</span><span class="sxs-lookup"><span data-stu-id="bbee5-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="bbee5-157">O Site Recovery também é feito especificamente para ambientes híbridos que são parcialmente locais e parcialmente no Azure.</span><span class="sxs-lookup"><span data-stu-id="bbee5-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="bbee5-158">Site Recovery ajuda a garantir a continuidade dos negócios, mantendo seus aplicativos em execução em VMs e servidores físicos locais disponíveis se um site ficar inativo.</span><span class="sxs-lookup"><span data-stu-id="bbee5-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="bbee5-159">Ele Replica cargas de trabalho em execução em VMs e servidores físicos para que permaneçam disponíveis em um local secundário se o site primário não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="bbee5-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="bbee5-160">Ele recupera as cargas de trabalho para o site primário quando ele está em funcionamento novamente.</span><span class="sxs-lookup"><span data-stu-id="bbee5-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="bbee5-161">A Figura 2-3 mostra a execução de várias migrações de VM usando Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="bbee5-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Posicionando aplicativos prontos para a infraestrutura de nuvem](./media/image2-3.png)

> <span data-ttu-id="bbee5-163">**Figura 2-3.**</span><span class="sxs-lookup"><span data-stu-id="bbee5-163">**Figure 2-3.**</span></span> <span data-ttu-id="bbee5-164">Posicionando aplicativos prontos para a infraestrutura de nuvem</span><span class="sxs-lookup"><span data-stu-id="bbee5-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bbee5-165">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="bbee5-165">Additional resources</span></span>

- <span data-ttu-id="bbee5-166">**Folha de tabela de migrações para Azure**</span><span class="sxs-lookup"><span data-stu-id="bbee5-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="bbee5-167">**Migrações para Azure**</span><span class="sxs-lookup"><span data-stu-id="bbee5-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="bbee5-168">**Central de migrações do Azure**</span><span class="sxs-lookup"><span data-stu-id="bbee5-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="bbee5-169">**Migrar para o Azure com Site Recovery**</span><span class="sxs-lookup"><span data-stu-id="bbee5-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="bbee5-170">**Visão geral do serviço de Azure Site Recovery**</span><span class="sxs-lookup"><span data-stu-id="bbee5-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="bbee5-171">**Migrando VMs no AWS para VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="bbee5-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="bbee5-172">[Anterior](index.md)
>[Próximo](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="bbee5-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->