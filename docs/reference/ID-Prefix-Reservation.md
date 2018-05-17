---
title: Kimlik öneki ayırma başvurusu
description: Paket kimliği öneki ayırma özellik açıklaması ve yazar Kılavuzu.
author: diverdan92
ms.author: diverdan92
manager: unnir
ms.date: 10/09/2017
ms.topic: reference
ms.reviewer: ananguar
ms.openlocfilehash: 63f442ae25b92aacbbf5af7d9b3ea1a5dafe5fc9
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="package-id-prefix-reservation"></a><span data-ttu-id="16417-103">Paket kimliği öneki ayırma</span><span class="sxs-lookup"><span data-stu-id="16417-103">Package ID prefix reservation</span></span>

<span data-ttu-id="16417-104">Paket sahipleri ayırmak ve kimliği önekleri ayırarak kimliklerini koruyun.</span><span class="sxs-lookup"><span data-stu-id="16417-104">Package owners can reserve and protect their identity by reserving ID prefixes.</span></span> <span data-ttu-id="16417-105">Ek bilgilerle kullanma, paketler, bunlar tüketen paket olmayan tanımlayıcı özelliklerini aldatıcı paket tüketicileri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="16417-105">Package consumers are provided with additional information when consuming packages that the package they are consuming are not deceptive in their identifying properties.</span></span> 

<span data-ttu-id="16417-106">[nuget.org](https://www.nuget.org/) ve Visual Studio 2017 15.4 veya sonraki bir sürümü Paket ayrılmış kimliği eşleştiği sürece ayrılmış paket kimliği öneki ile sahipleri tarafından gönderilen paketleri adlandırma deseni önek için görsel bir gösterge gösterir.</span><span class="sxs-lookup"><span data-stu-id="16417-106">[nuget.org](https://www.nuget.org/) and Visual Studio 2017 version 15.4 or later show a visual indicator for packages that are submitted by owners with a reserved package ID prefix, as long as the package matches the reserved ID prefix naming pattern.</span></span> <span data-ttu-id="16417-107">Ne kimliği öneki ayırma kapsar ve sahibi için bir kimlik öneki nasıl uygulayabilirsiniz başvuru açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16417-107">The below reference explains what the ID prefix reservation entails, and how an owner can apply for an ID prefix.</span></span>

## <a name="id-prefix-reservation-details"></a><span data-ttu-id="16417-108">Kimliği öneki ayırması ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="16417-108">ID prefix reservation details</span></span>

<span data-ttu-id="16417-109">Bir paket kimliği öneki ayrılmış, üzerinde olacaklar [nuget.org](https://www.nuget.org/) Galerisi, da Visual Studio gibi.</span><span class="sxs-lookup"><span data-stu-id="16417-109">When a package ID prefix is reserved, several things happen on the [nuget.org](https://www.nuget.org/) gallery, as well as in Visual Studio.</span></span> <span data-ttu-id="16417-110">Ayrıca, var. birden çok sahiplerine önek alt kümeleri için temsilci seçme önek 'genel' olarak ayarlanması gibi kimliği öneki ayırmaları tarafından desteklenen gelişmiş senaryoları.</span><span class="sxs-lookup"><span data-stu-id="16417-110">In addition, there are advanced scenarios that are supported by ID prefix reservations, such as setting a prefix as 'public', delegating prefix subsets to multiple owners.</span></span>

### <a name="id-prefix-reservation-on-nugetorg"></a><span data-ttu-id="16417-111">Nuget.org ilgili kimliği öneki rezervasyonu</span><span class="sxs-lookup"><span data-stu-id="16417-111">ID prefix reservation on nuget.org</span></span>

<span data-ttu-id="16417-112">Ne zaman bir öneki ayrılmıştır üzerinde [nuget.org](https://www.nuget.org/), aşağıdakiler olur:</span><span class="sxs-lookup"><span data-stu-id="16417-112">When a prefix is reserved on [nuget.org](https://www.nuget.org/), the following will happen:</span></span>

1. <span data-ttu-id="16417-113">Bir önek ayırma sahibi veya sahipleri kümesi ile ilişkili [nuget.org](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="16417-113">A prefix reservation is associated with an owner or set of owners on [nuget.org](https://www.nuget.org/).</span></span>

1. <span data-ttu-id="16417-114">Her bir paket gönderildi için [nuget.org](https://www.nuget.org/) sahibi kimliği öneki ayrılmış görüntülemenize kaynaklandığı sürece ayrılmış kimliği öneki ile eşleşen bir kimliği ile paket reddedilir.</span><span class="sxs-lookup"><span data-stu-id="16417-114">Whenever a package is submitted to [nuget.org](https://www.nuget.org/) with an ID that matches the reserved ID prefix, the package is rejected unless it originates from the owner(s) that reserved the ID prefix.</span></span>

1. <span data-ttu-id="16417-115">Visual Studio 2017 15.4 veya sonraki bir sürümü ve üzerinde ayrılmış kimliği öneki ile eşleşen ve sahibi kimliği öneki ayrılmış görüntülemenize kaynaklı herhangi bir paket görsel bir gösterge olacaktır [nuget.org](https://www.nuget.org/) paket altındadır gösteren ayrılmış bir kimliği öneki.</span><span class="sxs-lookup"><span data-stu-id="16417-115">Any package that matches the reserved ID prefix and originates from the owner(s) that reserved the ID prefix will have a visual indicator in Visual Studio 2017 version 15.4 or later, and on [nuget.org](https://www.nuget.org/) indicating that the package is under a reserved ID prefix.</span></span> <span data-ttu-id="16417-116">Bu, hem yeni paket gönderimlerini, hem de sahibi görüntülemenize altında varolan paketler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="16417-116">This is true for both new package submissions as well as existing packages under the owner(s).</span></span> <span data-ttu-id="16417-117">**Not:** yalnızca tek bir akış paket kaynağı seçtiyseniz Visual Studio'da göstergesi görünür.</span><span class="sxs-lookup"><span data-stu-id="16417-117">**Note:** The indicator in Visual Studio appears only if a single feed is selected as the package source.</span></span>

1. <span data-ttu-id="16417-118">Ayrılmış kimliği öneki eşleşen tüm önceden var olan ancak paketlerdir *değil* ayrılmış sahibini ait önek değişmeden kalır (bunlar listelenmemiş olmaz ancak aynı zamanda görsel gösterge yoktur).</span><span class="sxs-lookup"><span data-stu-id="16417-118">All previously existing packages that match the reserved ID prefix, but are *not* owned by the owner of the reserved prefix will remain unchanged (they will not be unlisted, but they will also not have the visual indicator).</span></span> <span data-ttu-id="16417-119">Ayrıca, bu paketleri sahipleri hala paketinin yeni sürümlerini gönderemeyecek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="16417-119">In addition, owners of these packages will still be able to submit new versions to the package.</span></span>

<span data-ttu-id="16417-120">Bu değişiklikler, aşağıdaki koşullara göre ve birkaç ek kısıtlamaları zorunlu tuttukları:</span><span class="sxs-lookup"><span data-stu-id="16417-120">These changes are based on the following conditions and impose several additional restrictions:</span></span>

- <span data-ttu-id="16417-121">Bir paketi tek sahibi (için birden çok sahipleri paketlerle) görünmesini visual göstergesi için ayrılmış önek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16417-121">Only one owner of a package needs to have the reserved prefix for the visual indicator to appear (for packages with multiple-owners).</span></span>

- <span data-ttu-id="16417-122">Burada bir veya daha fazla sahipleri ayrılmış önek içeriyor ve bir veya daha fazla sahipleri ayrılmış önek sahip bir paket birden fazla sahibi ise, yalnızca sahibi görüntülemenize ayrılmış önek ile ayrılmış bir önek ile diğer owner(s) kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16417-122">If there is more than one owner of a package where one or more owners has the reserved prefix and one or more owners does not have the reserved prefix, then only the owner(s) with the reserved prefix can remove other owner(s) with a reserved prefix.</span></span> <span data-ttu-id="16417-123">Ayrılmış önek olmayan sahipleri ayrılmış önekiyle sahipleri kaldıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="16417-123">The owners who do not have the prefix reserved cannot remove owners with the prefix reserved.</span></span> <span data-ttu-id="16417-124">Bunlar, yine de ayrılmış önek olmayan diğer sahipleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16417-124">They can still remove other owners that also do not have the prefix reserved.</span></span>

- <span data-ttu-id="16417-125">Bir paket görsel gösterge sonra gereken *her zaman* görsel gösterge sahip (en az bir sahibi ayrılmış önek ile güvence altına almak her zaman kalacak sahibi)</span><span class="sxs-lookup"><span data-stu-id="16417-125">Once a package has the visual indicator, it should *always* have the visual indicator (guaranteeing that at least one owner with the reserved prefix will always remain an owner)</span></span>

### <a name="advanced-prefix-reservation-scenarios"></a><span data-ttu-id="16417-126">Gelişmiş önek ayırma senaryoları</span><span class="sxs-lookup"><span data-stu-id="16417-126">Advanced prefix reservation scenarios</span></span>

<span data-ttu-id="16417-127">Subprefix temsilci ve genel olarak işaretleme önekleri dahil olmak üzere, aşağıda açıklanan daha gelişmiş birkaç önek ayırma senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="16417-127">There are several more advanced prefix reservation scenarios described below, including subprefix delegation, and marking prefixes as public.</span></span> <span data-ttu-id="16417-128">Yapılabilmesi için daha gelişmiş önek ayırmaları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16417-128">Below are the more advanced prefix reservations that can be made.</span></span> 

- <span data-ttu-id="16417-129">Önek ayırma sırasında sahibi önek alt kümelerini temsilcisi (veya önek) diğer sahiplerine isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="16417-129">During prefix reservation, the owner can request delegation of prefix subsets (or the prefix) to other owners.</span></span> <span data-ttu-id="16417-130">Örneğin, varsa '[Microsoft](https://www.nuget.org/profiles/microsoft)' sahibi ' Microsoft\*', ancak '[aspnet](https://www.nuget.org/profiles/aspnet)' yedek istediği ' Microsoft.AspNet.\*','[Microsoft](https://www.nuget.org/profiles/microsoft)' can temsilci seçmek Seç ' Microsoft.AspNet. \*' için [aspnet](https://www.nuget.org/profiles/aspnet) hesabı.</span><span class="sxs-lookup"><span data-stu-id="16417-130">For example, if '[Microsoft](https://www.nuget.org/profiles/microsoft)' owns 'Microsoft.\*', but '[aspnet](https://www.nuget.org/profiles/aspnet)' wants to reserve 'Microsoft.AspNet.\*', '[Microsoft](https://www.nuget.org/profiles/microsoft)' can choose to delegate 'Microsoft.AspNet.\*' to the [aspnet](https://www.nuget.org/profiles/aspnet) account.</span></span>

- <span data-ttu-id="16417-131">Önek ayırma sırasında sahibi bir önek genel hale getirmek üzere seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16417-131">During prefix reservation, the owner can choose to make a prefix public.</span></span> <span data-ttu-id="16417-132">Bu hala bunları ayrılmış bir önekten paket kaynağı, ancak içinde gösteren görsel gösterge verecektir **değil** engelleme öneki gelecekteki paket gönderimlerini herhangi sahibi için.</span><span class="sxs-lookup"><span data-stu-id="16417-132">This will still give them the visual indicator showing that the package originates from a reserved prefix, but it will **not** block future package submissions on the prefix for any owner.</span></span> <span data-ttu-id="16417-133">Pek çok katkıda bulunanlar sahip açık kaynak projeler için faydalıdır - top veya çekirdek katkıda bulunanlar ayrılmış önek olabilir, ancak bunu hala tüm katkıda bulunanlar için açık olabilir.</span><span class="sxs-lookup"><span data-stu-id="16417-133">This is useful for open source projects with many contributors - the top or core contributors can have the prefix reserved, but it can still be open to all contributors.</span></span> 

### <a name="prefix-reservation-visual-indicator"></a><span data-ttu-id="16417-134">Önek ayırma visual göstergesi</span><span class="sxs-lookup"><span data-stu-id="16417-134">Prefix reservation visual indicator</span></span>

<span data-ttu-id="16417-135">Bir paket ayrılmış bir önekten geldiğinde, gördüğünüz visual göstergelerini aşağıda [nuget.org](https://www.nuget.org/) Galerisi ve Visual Studio 2017 15.4 veya sonraki bir sürümü:</span><span class="sxs-lookup"><span data-stu-id="16417-135">When a package comes from a reserved prefix, you see the below visual indicators on the [nuget.org](https://www.nuget.org/) gallery and in Visual Studio 2017 version 15.4 or later:</span></span>

<span data-ttu-id="16417-136">**nuget.org Galerisi**
![nuget.org Galerisi](media/nuget-gallery-reserved-prefix.png)</span><span class="sxs-lookup"><span data-stu-id="16417-136">**nuget.org Gallery**
![nuget.org Gallery](media/nuget-gallery-reserved-prefix.png)</span></span>

<span data-ttu-id="16417-137">**Visual Studio**
![Visual Studio](media/visual-studio-reserved-prefix.png)</span><span class="sxs-lookup"><span data-stu-id="16417-137">**Visual Studio**
![Visual Studio](media/visual-studio-reserved-prefix.png)</span></span>

## <a name="id-prefix-reservation-application-process"></a><span data-ttu-id="16417-138">Kimlik öneki ayırma uygulama işlemi</span><span class="sxs-lookup"><span data-stu-id="16417-138">ID prefix reservation application process</span></span>

1. <span data-ttu-id="16417-139">Kabul gözden [öneki kimliği ayırma ölçütlerine](#id-prefix-reservation-criteria).</span><span class="sxs-lookup"><span data-stu-id="16417-139">Review the acceptance [criteria for prefix ID reservation](#id-prefix-reservation-criteria).</span></span>

2. <span data-ttu-id="16417-140">Herhangi bir ek olarak ayırmak istediğiniz ad alanları belirlemek [Gelişmiş önek ayırma senaryoları](#advanced-prefix-reservation-scenarios) gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="16417-140">Determine the namespaces you want to reserve, in addition to any [advanced prefix reservation scenarios](#advanced-prefix-reservation-scenarios) you may require.</span></span>

3. <span data-ttu-id="16417-141">Bir posta gönderme [ account@nuget.org ](mailto:account@nuget.org) üzerinde görünen adı sahip [nuget.org](https://www.nuget.org/), isteyen herhangi bir ayrılmış önekler yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="16417-141">Send a mail to [account@nuget.org](mailto:account@nuget.org) with the owner display name on [nuget.org](https://www.nuget.org/), as well as any reserved prefixes you are requesting.</span></span> <span data-ttu-id="16417-142">Birden çok sahiplerine önek alt kümelerini temsilci, tüm sahibi görünen adları belirttiğinizden ve alt kümelerini önek emin olun.</span><span class="sxs-lookup"><span data-stu-id="16417-142">If you are delegating prefix subsets to multiple owners, make sure you mention all owner display names and prefix subsets.</span></span>

<span data-ttu-id="16417-143">Uygulama gönderildikten sonra kabul veya reddetme (ile reddetme nedeni ölçüt) bildirilir.</span><span class="sxs-lookup"><span data-stu-id="16417-143">After the application is submitted, you are notified of acceptance or rejection (with the criteria that caused rejection).</span></span> <span data-ttu-id="16417-144">Sahibinin kimliğini onaylamak için ek tanımlayıcı sorular sormak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16417-144">We may need to ask additional identifying questions to confirm owner identity.</span></span>

### <a name="id-prefix-reservation-criteria"></a><span data-ttu-id="16417-145">Kimlik öneki ayırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="16417-145">ID prefix reservation criteria</span></span>

<span data-ttu-id="16417-146">Herhangi bir uygulama kimliği öneki rezervasyon gözden geçirirken [nuget.org](https://www.nuget.org/) takım uygulamaya karşı değerlendirir ölçütleri altında.</span><span class="sxs-lookup"><span data-stu-id="16417-146">When reviewing any application for ID prefix reservation, the [nuget.org](https://www.nuget.org/) team will evaluate the application against the below criteria.</span></span> <span data-ttu-id="16417-147">Tüm ölçütleri bir önek ayrılacak karşılanması gerekir, ancak önemli kanıtı (verilen bir açıklama ile) karşılanıp ölçüt ise uygulama reddedilmiş olabilir:</span><span class="sxs-lookup"><span data-stu-id="16417-147">Not all criteria needs to be met for a prefix to be reserved, but the application may be denied if there is not substantial evidence of the criteria being met (with an explanation given):</span></span>

1. <span data-ttu-id="16417-148">Paket kimliği öneki düzgün ve açıkça paket sahibinden belirler?</span><span class="sxs-lookup"><span data-stu-id="16417-148">Does the package ID prefix properly and clearly identify the package owner?</span></span>

1. <span data-ttu-id="16417-149">Çok sayıda zaten gönderilen paketleri paket kimliği öneki altında sahibi tarafından misiniz?</span><span class="sxs-lookup"><span data-stu-id="16417-149">Are a significant number of the packages that have already been submitted by the owner under the package ID prefix?</span></span>

1. <span data-ttu-id="16417-150">Paket kimliği öneki bir şey ortak herhangi bir tek tek sahibi veya kuruluşu ait değil mi?</span><span class="sxs-lookup"><span data-stu-id="16417-150">Is the package ID prefix something common that should not belong to any individual owner or organization?</span></span>

1. <span data-ttu-id="16417-151">Misiniz *değil* paket kimliği öneki ayırma belirsizlik ve topluluk için Kafa karışıklığına neden?</span><span class="sxs-lookup"><span data-stu-id="16417-151">Would *not* reserving the package ID prefix cause ambiguity and confusion for the community?</span></span>

1. <span data-ttu-id="16417-152">Paket kimliği öneki temizleyin ve tutarlı (özellikle için paket yazarına) eşleşen paketleri tanımlayıcı özelliklerini misiniz?</span><span class="sxs-lookup"><span data-stu-id="16417-152">Are the identifying properties of the packages that match the package ID prefix clear and consistent (especially the package author)?</span></span>

## <a name="third-party-feed-provider-scenarios"></a><span data-ttu-id="16417-153">Üçüncü taraf sağlayıcı senaryoları akışı</span><span class="sxs-lookup"><span data-stu-id="16417-153">Third party feed provider scenarios</span></span>

<span data-ttu-id="16417-154">Bir üçüncü taraf sağlayıcı akış önek ayırmaları sağlamak için kendi hizmet uygulama ilgileniyorsa değiştirerek NuGet V3 arama hizmeti sağlayıcıları akış için bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16417-154">If a third party feed provider is interested in implementing their own service to provide prefix reservations, you can do so by modifying the search service in the NuGet V3 feed providers.</span></span> <span data-ttu-id="16417-155">Akış arama hizmeti ek eklemektir *doğrulandı* özelliğiyle örnekler için aşağıdaki V3 akışları.</span><span class="sxs-lookup"><span data-stu-id="16417-155">The addition in the feed search service is to add the *verified* property, with examples for the V3 feeds below.</span></span> <span data-ttu-id="16417-156">NuGet istemci eklenen özelliğin akış V2'desteklemez.</span><span class="sxs-lookup"><span data-stu-id="16417-156">The NuGet client will not support the added property in the V2 feed.</span></span>

<span data-ttu-id="16417-157">Daha fazla bilgi için bkz: [API'nin arama hizmeti ile ilgili belgeler](../api/search-query-service-resource.md).</span><span class="sxs-lookup"><span data-stu-id="16417-157">For more information, see the [documentation about the API's search service](../api/search-query-service-resource.md).</span></span>