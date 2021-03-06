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
# <a name="nuget-52-release-notes"></a>NuGet 5,2 sürüm notları

NuGet dağıtım araçlar:

| NuGet sürümü | Visual Studio sürümünde kullanılabilir| .NET SDK 'ları 'nda kullanılabilir|
|:---|:---|:---|
| [**5.2.0**](https://nuget.org/downloads) | [Visual Studio 2019 sürüm 16,2](https://visualstudio.microsoft.com/downloads/) | [2.1.80 X](https://dotnet.microsoft.com/download/dotnet-core/2.1) <sup>1</sup>, [2.2.40 X](https://dotnet.microsoft.com/download/dotnet-core/2.2)<sup>2</sup> |

<sup>1</sup> .NET Core iş yüküne sahip Visual Studio 2019 ile yüklendi 

<sup>2</sup> .NET Core iş yüküne sahip Visual Studio 2019 ile isteğe bağlı bir install olarak kullanılabilir

## <a name="summary-whats-new-in-52"></a>Özetleme 5,2 sürümündeki yenilikler

* Linux & Mac [#7341](https://github.com/NuGet/Home/issues/7341) yol sorunları nedeniyle zaman zaman NuGet işlem hatalarıyla kaynaklanan kritik bir hata düzeltildi

* Visual Studio 'da NuGet Paket Yöneticisi Kullanıcı arabirimini kullanarak paketlere gözatarken geliştirilmiş Kullanıcı arabirimi yanıtlama hızı, yavaş kaynaklar için de fark edilebilir [#8039](https://github.com/NuGet/Home/issues/8039)

* Kilit dosyası ([#8187](https://github.com/NuGet/Home/issues/8187),[#8160](https://github.com/NuGet/Home/issues/8160),[#8114](https://github.com/NuGet/Home/issues/8114),[#7840](https://github.com/NuGet/Home/issues/7840)) ve kimlik doğrulama eklentisi ([#8300](https://github.com/NuGet/Home/issues/8300),[#8271](https://github.com/NuGet/Home/issues/8271),[#8269](https://github.com/NuGet/Home/issues/8269),[#8210](https://github.com/NuGet/Home/issues/8210),[#8198](https://github.com/NuGet/Home/issues/8198),[#7845](https://github.com/NuGet/Home/issues/7845)) için güvenilirlik düzeltmeleri

### <a name="issues-fixed-in-this-release"></a>Bu sürümde giderilen sorunlar

**Hata**

* Erişen Paket Yöneticisi konsolu:  UI gecikmesi "varsayılan proje" ComboBox seçili değer- [#8235](https://github.com/NuGet/Home/issues/8235)

* Erişen PM Kullanıcı arabirimindeki performans iyileştirmeleri- [#8039](https://github.com/NuGet/Home/issues/8039)

* Erişen PMC- [#6824](https://github.com/NuGet/Home/issues/6824) 'de varsayılan proje okunurken UI gecikmesi

* Perf: [vsfeedback] yerel paket kaynağı için NuGet güncelleştirme sekmesi donuyor- [#6470](https://github.com/NuGet/Home/issues/6470)

* Kaydet  Eklenti erken [#8300](https://github.com/NuGet/Home/issues/8300) başlatılamazsa veya Sonlandıramazsa NuGet tam el sıkışma zaman aşımını bekler

* Eklentiler: eklenti başlatma hatası- [#8271](https://github.com/NuGet/Home/issues/8271) tanılama geliştirme

* Kaydet Yerleşik eklentiler için NuGet. exe bulma ile ilgili sorun- [#8269](https://github.com/NuGet/Home/issues/8269)

* Eklentiler: önbellek dosyası hiçbir şekilde okunamaz [#8210](https://github.com/NuGet/Home/issues/8210)

* Kaydet  "Bir görev iptal edildi." geri yükleme sırasında kimlik doğrulama eklentisi ile ilgili hatalar- [#8198](https://github.com/NuGet/Home/issues/8198)

* Eklentiler önbelleği, Linux platformlarında zaman zaman keşfedilemez- [#7845](https://github.com/NuGet/Home/issues/7845)

* LockFile: ATF ile, hatalı hedef Framework eşitlik denetimi- [#8187](https://github.com/NuGet/Home/issues/8187) nedenıyle yanlış NU1004 var

* LockFile: '--kilitli modu ' geri yükleme bayrağı, kilit dosyası boşsa veya hatalı biçimlendirilmiş ise [#8160](https://github.com/NuGet/Home/issues/8160)

* Kilit dosyası: Paketler kilit dosyasında özel derleme adlarıyla küçük projeler yapmayın- [#8114](https://github.com/NuGet/Home/issues/8114)

* Kilit dosyası: Kilit dosyasında proje başvurusu küçük harf yap- [#7840](https://github.com/NuGet/Home/issues/7840)

* Geri yükle: birden fazla başarısız yükleme denemesine (yinelenen çıkışlarla) yapılan değiştirilmiş bir paket yükleme sonuçları yükleniyor- [#8175](https://github.com/NuGet/Home/issues/8175)

* VS: çözüm Kullanıcı seçenekleri NuGet güncelleştirmesinden sonra seri durumdan çıkarılamıyor- [#8166](https://github.com/NuGet/Home/issues/8166)

* bir UnitTest projesindeki DotNet-List-Package bir hata döndürüyor- [#8154](https://github.com/NuGet/Home/issues/8154)

* VS yükleyici için NuGet paket grubu oluşturma-bazı VSıX kurulum sorunlarını düzeltme- [#8033](https://github.com/NuGet/Home/issues/8033)

* GeneratePackageOnBuild NoBuild öğesini ayarlayamamalıdır. - [#7801](https://github.com/NuGet/Home/issues/7801)

* "-SymbolPackageFormat snupkg" adlı yeni seçenek,. nuspec dosyası açık bir bütünleştirilmiş kod başvuru öğesi içerdiğinde bir hata oluşturur- [#7638](https://github.com/NuGet/Home/issues/7638)

* NuGet. targets (498, 5): hata: '/Tmp/nugetkaralama- [#7341](https://github.com/NuGet/Home/issues/7341) yolunun bir parçası bulunamadı

**DCR**

* PackageDownload 'in desteklendiğini belirten bir MSBuild özelliği ekleyin- [#8106](https://github.com/NuGet/Home/issues/8106)

* FrameworkReference, FrameworkReference. Privatevarlıklar aracılığıyla bağımlılık akışını bastırır- [#7988](https://github.com/NuGet/Home/issues/7988)

* Bir paketin dışında Runtime. JSON sağlama mekanizması- [#7351](https://github.com/NuGet/Home/issues/7351)

**[Bu yayında düzeltilen tüm sorunların listesi-5,2 RTM](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.2")**


