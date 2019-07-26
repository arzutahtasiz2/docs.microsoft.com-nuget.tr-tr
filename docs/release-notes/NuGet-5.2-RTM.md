---
title: NuGet 5,2 RTM sürüm notları
description: Yeni özellikler, hata düzeltmeleri ve DTU 'lar dahil olmak üzere NuGet 5,2 sürüm notları.
author: karann-msft
ms.author: karann
ms.date: 07/23/2019
ms.topic: conceptual
ms.openlocfilehash: f94bd8ddb8fac8bf47c2826bf5b417595b0efa8b
ms.sourcegitcommit: f291ff91561a6b58c2aec41c624d798e00ce41fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471201"
---
# <a name="nuget-52-release-notes"></a><span data-ttu-id="121ac-103">NuGet 5,2 sürüm notları</span><span class="sxs-lookup"><span data-stu-id="121ac-103">NuGet 5.2 Release Notes</span></span>

<span data-ttu-id="121ac-104">NuGet dağıtım araçlar:</span><span class="sxs-lookup"><span data-stu-id="121ac-104">NuGet distribution vehicles:</span></span>

| <span data-ttu-id="121ac-105">NuGet sürümü</span><span class="sxs-lookup"><span data-stu-id="121ac-105">NuGet version</span></span> | <span data-ttu-id="121ac-106">Visual Studio sürümünde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="121ac-106">Available in Visual Studio version</span></span>| <span data-ttu-id="121ac-107">.NET SDK 'ları 'nda kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="121ac-107">Available in .NET SDK(s)</span></span>|
|:---|:---|:---|
| [<span data-ttu-id="121ac-108">**5.2.0**</span><span class="sxs-lookup"><span data-stu-id="121ac-108">**5.2.0**</span></span>](https://nuget.org/downloads) | [<span data-ttu-id="121ac-109">Visual Studio 2019 sürüm 16,2</span><span class="sxs-lookup"><span data-stu-id="121ac-109">Visual Studio 2019 version 16.2</span></span>](https://visualstudio.microsoft.com/downloads/) | <span data-ttu-id="121ac-110">[2.1.80 X](https://dotnet.microsoft.com/download/dotnet-core/2.1) <sup>1</sup>, [2.2.40 X](https://dotnet.microsoft.com/download/dotnet-core/2.2)<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="121ac-110">[2.1.80X](https://dotnet.microsoft.com/download/dotnet-core/2.1)<sup>1</sup>, [2.2.40X](https://dotnet.microsoft.com/download/dotnet-core/2.2)<sup>2</sup></span></span> |

<span data-ttu-id="121ac-111"><sup>1</sup> .NET Core iş yüküne sahip Visual Studio 2019 ile yüklendi</span><span class="sxs-lookup"><span data-stu-id="121ac-111"><sup>1</sup>Installed with Visual Studio 2019 with .NET Core workload</span></span> 

<span data-ttu-id="121ac-112"><sup>2</sup> .NET Core iş yüküne sahip Visual Studio 2019 ile isteğe bağlı bir install olarak kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="121ac-112"><sup>2</sup>Available as an optional install with Visual Studio 2019 with .NET Core workload</span></span>

## <a name="summary-whats-new-in-52"></a><span data-ttu-id="121ac-113">Özetleme 5,2 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="121ac-113">Summary: What's New in 5.2</span></span>

* <span data-ttu-id="121ac-114">Linux & Mac [#7341](https://github.com/NuGet/Home/issues/7341) yol sorunları nedeniyle zaman zaman NuGet işlem hatalarıyla kaynaklanan kritik bir hata düzeltildi</span><span class="sxs-lookup"><span data-stu-id="121ac-114">Fixed a critical bug that caused occasional NuGet operation failures due to path issues on Linux & Mac - [#7341](https://github.com/NuGet/Home/issues/7341)</span></span>

* <span data-ttu-id="121ac-115">Visual Studio 'da NuGet Paket Yöneticisi Kullanıcı arabirimini kullanarak paketlere gözatarken geliştirilmiş Kullanıcı arabirimi yanıtlama hızı, yavaş kaynaklar için de fark edilebilir [#8039](https://github.com/NuGet/Home/issues/8039)</span><span class="sxs-lookup"><span data-stu-id="121ac-115">Improved UI responsiveness when browsing packages using the NuGet package manager UI in Visual Studio especially noticeable for slow sources - [#8039](https://github.com/NuGet/Home/issues/8039)</span></span>

* <span data-ttu-id="121ac-116">Kilit dosyası ([#8187](https://github.com/NuGet/Home/issues/8187),[#8160](https://github.com/NuGet/Home/issues/8160),[#8114](https://github.com/NuGet/Home/issues/8114),[#7840](https://github.com/NuGet/Home/issues/7840)) ve kimlik doğrulama eklentisi ([#8300](https://github.com/NuGet/Home/issues/8300),[#8271](https://github.com/NuGet/Home/issues/8271),[#8269](https://github.com/NuGet/Home/issues/8269),[#8210](https://github.com/NuGet/Home/issues/8210),[#8198](https://github.com/NuGet/Home/issues/8198),[#7845](https://github.com/NuGet/Home/issues/7845)) için güvenilirlik düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="121ac-116">Tons of reliability fixes for lock file ([#8187](https://github.com/NuGet/Home/issues/8187),[#8160](https://github.com/NuGet/Home/issues/8160),[#8114](https://github.com/NuGet/Home/issues/8114),[#7840](https://github.com/NuGet/Home/issues/7840)) and authentication plugin ([#8300](https://github.com/NuGet/Home/issues/8300),[#8271](https://github.com/NuGet/Home/issues/8271),[#8269](https://github.com/NuGet/Home/issues/8269),[#8210](https://github.com/NuGet/Home/issues/8210),[#8198](https://github.com/NuGet/Home/issues/8198),[#7845](https://github.com/NuGet/Home/issues/7845))</span></span>

### <a name="issues-fixed-in-this-release"></a><span data-ttu-id="121ac-117">Bu sürümde giderilen sorunlar</span><span class="sxs-lookup"><span data-stu-id="121ac-117">Issues fixed in this release</span></span>

<span data-ttu-id="121ac-118">**Hata**</span><span class="sxs-lookup"><span data-stu-id="121ac-118">**Bugs**</span></span>

* <span data-ttu-id="121ac-119">Erişen Paket Yöneticisi konsolu:  UI gecikmesi "varsayılan proje" ComboBox seçili değer- [#8235](https://github.com/NuGet/Home/issues/8235)</span><span class="sxs-lookup"><span data-stu-id="121ac-119">Perf: Package Manager Console:  UI delay updating "Default project" combobox selected value - [#8235](https://github.com/NuGet/Home/issues/8235)</span></span>

* <span data-ttu-id="121ac-120">Erişen PM Kullanıcı arabirimindeki performans iyileştirmeleri- [#8039](https://github.com/NuGet/Home/issues/8039)</span><span class="sxs-lookup"><span data-stu-id="121ac-120">Perf: Performance improvements in the PM UI - [#8039](https://github.com/NuGet/Home/issues/8039)</span></span>

* <span data-ttu-id="121ac-121">Erişen PMC- [#6824](https://github.com/NuGet/Home/issues/6824) 'de varsayılan proje okunurken UI gecikmesi</span><span class="sxs-lookup"><span data-stu-id="121ac-121">Perf: UI Delay when reading Default Project in PMC - [#6824](https://github.com/NuGet/Home/issues/6824)</span></span>

* <span data-ttu-id="121ac-122">Perf: [vsfeedback] yerel paket kaynağı için NuGet güncelleştirme sekmesi donuyor- [#6470](https://github.com/NuGet/Home/issues/6470)</span><span class="sxs-lookup"><span data-stu-id="121ac-122">Perf: [vsfeedback] NuGet Update tab freezes for a local package source - [#6470](https://github.com/NuGet/Home/issues/6470)</span></span>

* <span data-ttu-id="121ac-123">Kaydet  Eklenti erken [#8300](https://github.com/NuGet/Home/issues/8300) başlatılamazsa veya Sonlandıramazsa NuGet tam el sıkışma zaman aşımını bekler</span><span class="sxs-lookup"><span data-stu-id="121ac-123">Plugins:  NuGet waits full handshake timeout if plugin fails to launch or terminates early - [#8300](https://github.com/NuGet/Home/issues/8300)</span></span>

* <span data-ttu-id="121ac-124">Eklentiler: eklenti başlatma hatası- [#8271](https://github.com/NuGet/Home/issues/8271) tanılama geliştirme</span><span class="sxs-lookup"><span data-stu-id="121ac-124">Plugins:  improve diagnosability of plugin launch failure - [#8271](https://github.com/NuGet/Home/issues/8271)</span></span>

* <span data-ttu-id="121ac-125">Kaydet Yerleşik eklentiler için NuGet. exe bulma ile ilgili sorun- [#8269](https://github.com/NuGet/Home/issues/8269)</span><span class="sxs-lookup"><span data-stu-id="121ac-125">Plugins: Issue with nuget.exe discovery of built in plugins - [#8269](https://github.com/NuGet/Home/issues/8269)</span></span>

* <span data-ttu-id="121ac-126">Eklentiler: önbellek dosyası hiçbir şekilde okunamaz [#8210](https://github.com/NuGet/Home/issues/8210)</span><span class="sxs-lookup"><span data-stu-id="121ac-126">Plugins:  cache file is never read - [#8210](https://github.com/NuGet/Home/issues/8210)</span></span>

* <span data-ttu-id="121ac-127">Kaydet  "Bir görev iptal edildi."</span><span class="sxs-lookup"><span data-stu-id="121ac-127">Plugins:  "A task was canceled."</span></span> <span data-ttu-id="121ac-128">geri yükleme sırasında kimlik doğrulama eklentisi ile ilgili hatalar- [#8198](https://github.com/NuGet/Home/issues/8198)</span><span class="sxs-lookup"><span data-stu-id="121ac-128">errors with authentication plugin during restore - [#8198](https://github.com/NuGet/Home/issues/8198)</span></span>

* <span data-ttu-id="121ac-129">Eklentiler önbelleği, Linux platformlarında zaman zaman keşfedilemez- [#7845](https://github.com/NuGet/Home/issues/7845)</span><span class="sxs-lookup"><span data-stu-id="121ac-129">Plugins cache not discoverable intermittently on linux platforms - [#7845](https://github.com/NuGet/Home/issues/7845)</span></span>

* <span data-ttu-id="121ac-130">LockFile: ATF ile, hatalı hedef Framework eşitlik denetimi- [#8187](https://github.com/NuGet/Home/issues/8187) nedenıyle yanlış NU1004 var</span><span class="sxs-lookup"><span data-stu-id="121ac-130">LockFile: with ATF, it has false NU1004 due to a bad target framework equality check - [#8187](https://github.com/NuGet/Home/issues/8187)</span></span>

* <span data-ttu-id="121ac-131">LockFile: '--kilitli modu ' geri yükleme bayrağı, kilit dosyası boşsa veya hatalı biçimlendirilmiş ise [#8160](https://github.com/NuGet/Home/issues/8160)</span><span class="sxs-lookup"><span data-stu-id="121ac-131">LockFile: '--locked-mode' restore flag not respected if lock file is empty or malformed - [#8160](https://github.com/NuGet/Home/issues/8160)</span></span>

* <span data-ttu-id="121ac-132">Kilit dosyası: Paketler kilit dosyasında özel derleme adlarıyla küçük projeler yapmayın- [#8114](https://github.com/NuGet/Home/issues/8114)</span><span class="sxs-lookup"><span data-stu-id="121ac-132">LockFile: Don't lowercase projects with custom assembly names in packages lock file - [#8114](https://github.com/NuGet/Home/issues/8114)</span></span>

* <span data-ttu-id="121ac-133">Kilit dosyası: Kilit dosyasında proje başvurusu küçük harf yap- [#7840](https://github.com/NuGet/Home/issues/7840)</span><span class="sxs-lookup"><span data-stu-id="121ac-133">LockFile: Make project reference lower case in lock file  - [#7840](https://github.com/NuGet/Home/issues/7840)</span></span>

* <span data-ttu-id="121ac-134">Geri yükle: birden fazla başarısız yükleme denemesine (yinelenen çıkışlarla) yapılan değiştirilmiş bir paket yükleme sonuçları yükleniyor- [#8175](https://github.com/NuGet/Home/issues/8175)</span><span class="sxs-lookup"><span data-stu-id="121ac-134">Restore:  installing a tampered signed package results in multiple failed install attempts (with repeated output) - [#8175](https://github.com/NuGet/Home/issues/8175)</span></span>

* <span data-ttu-id="121ac-135">VS: çözüm Kullanıcı seçenekleri NuGet güncelleştirmesinden sonra seri durumdan çıkarılamıyor- [#8166](https://github.com/NuGet/Home/issues/8166)</span><span class="sxs-lookup"><span data-stu-id="121ac-135">VS: solution user options fail to deserialize after NuGet update - [#8166](https://github.com/NuGet/Home/issues/8166)</span></span>

* <span data-ttu-id="121ac-136">bir UnitTest projesindeki DotNet-List-Package bir hata döndürüyor- [#8154](https://github.com/NuGet/Home/issues/8154)</span><span class="sxs-lookup"><span data-stu-id="121ac-136">dotnet-list-package in a UnitTest project returns an error - [#8154](https://github.com/NuGet/Home/issues/8154)</span></span>

* <span data-ttu-id="121ac-137">VS yükleyici için NuGet paket grubu oluşturma-bazı VSıX kurulum sorunlarını düzeltme- [#8033](https://github.com/NuGet/Home/issues/8033)</span><span class="sxs-lookup"><span data-stu-id="121ac-137">Create NuGet package group for VS installer - fixing some VSIX setup problems - [#8033](https://github.com/NuGet/Home/issues/8033)</span></span>

* <span data-ttu-id="121ac-138">GeneratePackageOnBuild NoBuild öğesini ayarlayamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="121ac-138">GeneratePackageOnBuild should not set NoBuild.</span></span><span data-ttu-id="121ac-139"> - [#7801](https://github.com/NuGet/Home/issues/7801)</span><span class="sxs-lookup"><span data-stu-id="121ac-139"> - [#7801](https://github.com/NuGet/Home/issues/7801)</span></span>

* <span data-ttu-id="121ac-140">"-SymbolPackageFormat snupkg" adlı yeni seçenek,. nuspec dosyası açık bir bütünleştirilmiş kod başvuru öğesi içerdiğinde bir hata oluşturur- [#7638](https://github.com/NuGet/Home/issues/7638)</span><span class="sxs-lookup"><span data-stu-id="121ac-140">The new option "-SymbolPackageFormat snupkg" generates an error when the .nuspec file contains an explicit assembly reference element - [#7638](https://github.com/NuGet/Home/issues/7638)</span></span>

* <span data-ttu-id="121ac-141">NuGet. targets (498, 5): hata: '/Tmp/nugetkaralama- [#7341](https://github.com/NuGet/Home/issues/7341) yolunun bir parçası bulunamadı</span><span class="sxs-lookup"><span data-stu-id="121ac-141">NuGet.targets(498,5): error : Could not find a part of the path '/tmp/NuGetScratch - [#7341](https://github.com/NuGet/Home/issues/7341)</span></span>

<span data-ttu-id="121ac-142">**DCR**</span><span class="sxs-lookup"><span data-stu-id="121ac-142">**DCR:**</span></span>

* <span data-ttu-id="121ac-143">PackageDownload 'in desteklendiğini belirten bir MSBuild özelliği ekleyin- [#8106](https://github.com/NuGet/Home/issues/8106)</span><span class="sxs-lookup"><span data-stu-id="121ac-143">Add an msbuild property that indicates that PackageDownload is supported - [#8106](https://github.com/NuGet/Home/issues/8106)</span></span>

* <span data-ttu-id="121ac-144">FrameworkReference, FrameworkReference. Privatevarlıklar aracılığıyla bağımlılık akışını bastırır- [#7988](https://github.com/NuGet/Home/issues/7988)</span><span class="sxs-lookup"><span data-stu-id="121ac-144">FrameworkReference suppress dependency flow via FrameworkReference.PrivateAssets - [#7988](https://github.com/NuGet/Home/issues/7988)</span></span>

* <span data-ttu-id="121ac-145">Bir paketin dışında Runtime. JSON sağlama mekanizması- [#7351](https://github.com/NuGet/Home/issues/7351)</span><span class="sxs-lookup"><span data-stu-id="121ac-145">Mechanism for supplying runtime.json outside of a package - [#7351](https://github.com/NuGet/Home/issues/7351)</span></span>

<span data-ttu-id="121ac-146">**[Bu yayında düzeltilen tüm sorunların listesi-5,2 RTM](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.2")**</span><span class="sxs-lookup"><span data-stu-id="121ac-146">**[List of all issues fixed in this release - 5.2 RTM](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.2")**</span></span>

