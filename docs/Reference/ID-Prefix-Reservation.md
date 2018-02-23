---
title: "Kimlik öneki ayırma başvurusu | Microsoft Docs"
author: diverdan92
ms.author: diverdan92
manager: unniravindranathan
ms.date: 10/09/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Paket kimliği öneki ayırma özellik açıklaması ve yazar Kılavuzu."
keywords: "NuGet paket kimliği, önek, rezervasyonu"
ms.reviewer:
- ananguar
- karann-msft
- unniravindranathan
ms.openlocfilehash: bee215fcc88b03dbdde6c15d1583898bdf205952
ms.sourcegitcommit: b0af28d1c809c7e951b0817d306643fcc162a030
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2018
---
# <a name="package-id-prefix-reservation"></a>Paket kimliği öneki ayırma

Paket sahipleri olan ayırabilir ve kimliği önekleri ayırarak kimliklerini koruyun. Ek bilgilerle kullanma, paketler, bunlar tüketen paket olmayan tanımlayıcı özelliklerini aldatıcı paket tüketicileri sağlanır. 

[nuget.org](https://www.nuget.org/) ve Visual Studio 2017 15.4 veya sonraki bir sürümü Paket ayrılmış kimliği eşleştiği sürece ayrılmış paket kimliği öneki ile sahipleri tarafından gönderilen paketleri adlandırma deseni önek için görsel bir gösterge gösterir. Ne kimliği öneki ayırma kapsar ve sahibi için bir kimlik öneki nasıl uygulayabilirsiniz başvuru açıklanmaktadır.

## <a name="id-prefix-reservation-details"></a>Kimliği öneki ayırması ayrıntıları

Bir paket kimliği öneki ayrılmış, üzerinde olacaklar [nuget.org](https://www.nuget.org/) Galerisi, da Visual Studio gibi. Ayrıca, var. birden çok sahiplerine önek alt kümeleri için temsilci seçme önek 'genel' olarak ayarlanması gibi kimliği öneki ayırmaları tarafından desteklenen gelişmiş senaryoları.

### <a name="id-prefix-reservation-on-nugetorg"></a>Nuget.org ilgili kimliği öneki rezervasyonu

Ne zaman bir öneki ayrılmıştır üzerinde [nuget.org](https://www.nuget.org/), aşağıdakiler olur:

1. Bir önek ayırma sahibi veya sahipleri kümesi ile ilişkili [nuget.org](https://www.nuget.org/).

1. Her bir paket gönderildi için [nuget.org](https://www.nuget.org/) sahibi kimliği öneki ayrılmış görüntülemenize kaynaklandığı sürece ayrılmış kimliği öneki ile eşleşen bir kimliği ile paket reddedilir.

1. Visual Studio 2017 15.4 veya sonraki bir sürümü ve üzerinde ayrılmış kimliği öneki ile eşleşen ve sahibi kimliği öneki ayrılmış görüntülemenize kaynaklı herhangi bir paket görsel bir gösterge olacaktır [nuget.org](https://www.nuget.org/) paket altındadır gösteren ayrılmış bir kimliği öneki. Bu, hem yeni paket gönderimlerini, hem de sahibi görüntülemenize altında varolan paketler için geçerlidir. **Not:** yalnızca tek bir akış paket kaynağı seçtiyseniz Visual Studio'da göstergesi görünür.

1. Ayrılmış kimliği öneki eşleşen tüm önceden var olan ancak paketlerdir *değil* ayrılmış sahibini ait önek değişmeden kalır (bunlar listelenmemiş olmaz ancak aynı zamanda görsel gösterge yoktur). Ayrıca, bu paketleri sahipleri hala paketinin yeni sürümlerini gönderemeyecek olacaktır.

Bu değişiklikler, aşağıdaki koşullara göre ve birkaç ek kısıtlamaları zorunlu tuttukları:

- Bir paketi tek sahibi (için birden çok sahipleri paketlerle) görünmesini visual göstergesi için ayrılmış önek olmalıdır.

- Burada bir veya daha fazla sahipleri ayrılmış önek içeriyor ve bir veya daha fazla sahipleri ayrılmış önek sahip bir paket birden fazla sahibi ise, yalnızca sahibi görüntülemenize ayrılmış önek ile ayrılmış bir önek ile diğer owner(s) kaldırabilirsiniz. Ayrılmış önek olmayan sahipleri ayrılmış önekiyle sahipleri kaldıramazsınız. Bunlar, yine de ayrılmış önek olmayan diğer sahipleri kaldırabilirsiniz.

- Bir paket görsel gösterge sonra gereken *her zaman* görsel gösterge sahip (en az bir sahibi ayrılmış önek ile güvence altına almak her zaman kalacak sahibi)

### <a name="advanced-prefix-reservation-scenarios"></a>Gelişmiş önek ayırma senaryoları

Subprefix temsilci ve genel olarak işaretleme önekleri dahil olmak üzere, aşağıda açıklanan daha gelişmiş birkaç önek ayırma senaryo vardır. Yapılabilmesi için daha gelişmiş önek ayırmaları aşağıda verilmiştir. 

- Önek ayırma sırasında sahibi önek alt kümelerini temsilcisi (veya önek) diğer sahiplerine isteyebilir. Örneğin, varsa '[Microsoft](https://www.nuget.org/profiles/microsoft)' sahibi ' Microsoft\*', ancak '[aspnet](https://www.nuget.org/profiles/aspnet)' yedek istediği ' Microsoft.AspNet.\*','[Microsoft](https://www.nuget.org/profiles/microsoft)' can temsilci seçmek Seç ' Microsoft.AspNet. \*' için [aspnet](https://www.nuget.org/profiles/aspnet) hesabı.

- Önek ayırma sırasında sahibi bir önek genel hale getirmek üzere seçebilirsiniz. Bu hala bunları ayrılmış bir önekten paket kaynağı, ancak içinde gösteren görsel gösterge verecektir **değil** engelleme öneki gelecekteki paket gönderimlerini herhangi sahibi için. Pek çok katkıda bulunanlar sahip açık kaynak projeler için faydalıdır - top veya çekirdek katkıda bulunanlar ayrılmış önek olabilir, ancak bunu hala tüm katkıda bulunanlar için açık olabilir. 

### <a name="prefix-reservation-visual-indicator"></a>Önek ayırma visual göstergesi

Bir paket ayrılmış bir önekten geldiğinde, gördüğünüz visual göstergelerini aşağıda [nuget.org](https://www.nuget.org/) Galerisi ve Visual Studio 2017 15.4 veya sonraki bir sürümü:

**nuget.org Galerisi**
![nuget.org Galerisi](media/nuget-gallery-reserved-prefix.png)

**Visual Studio**
![Visual Studio](media/visual-studio-reserved-prefix.png)

## <a name="id-prefix-reservation-application-process"></a>Kimlik öneki ayırma uygulama işlemi

1. Kabul gözden [öneki kimliği ayırma ölçütlerine](#id-prefix-reservation-criteria).

1. Herhangi bir ek olarak ayırmak istediğiniz ad alanları belirlemek [Gelişmiş önek ayırma senaryoları](#advanced-prefix-reservation-scenarios) gerektirebilir.

1. Bir posta gönderme [ account@nuget.org ](mailto:account@nuget.org) üzerinde görünen adı sahip [nuget.org](https://www.nuget.org/), isteyen herhangi bir ayrılmış önekler yanı sıra. Birden çok sahiplerine önek alt kümelerini temsilci, tüm sahibi görünen adları belirttiğinizden ve alt kümelerini önek emin olun.

Uygulama gönderildikten sonra kabul veya reddetme (ile reddetme nedeni ölçüt) bildirilir. Sahibinin kimliğini onaylamak için ek tanımlayıcı sorular sormak gerekebilir.

### <a name="id-prefix-reservation-criteria"></a>Kimlik öneki ayırma ölçütü

Herhangi bir uygulama kimliği öneki rezervasyon gözden geçirirken [nuget.org](https://www.nuget.org/) takım uygulamaya karşı değerlendirir ölçütleri altında. Tüm ölçütleri bir önek ayrılacak karşılanması gerekir, ancak önemli kanıtı (verilen bir açıklama ile) karşılanıp ölçüt ise uygulama reddedilmiş olabilir:

1. Paket kimliği öneki düzgün ve açıkça paket sahibinden belirler?

1. Çok sayıda zaten gönderilen paketleri paket kimliği öneki altında sahibi tarafından misiniz?

1. Paket kimliği öneki bir şey ortak herhangi bir tek tek sahibi veya kuruluşu ait değil mi?

1. Misiniz *değil* paket kimliği öneki ayırma belirsizlik ve topluluk için Kafa karışıklığına neden?

1. Paket kimliği öneki temizleyin ve tutarlı (özellikle için paket yazarına) eşleşen paketleri tanımlayıcı özelliklerini misiniz?

## <a name="third-party-feed-provider-scenarios"></a>Üçüncü taraf sağlayıcı senaryoları akışı

Bir üçüncü taraf sağlayıcı akış önek ayırmaları sağlamak için kendi hizmet uygulama ilgileniyorsa değiştirerek NuGet V3 arama hizmeti sağlayıcıları akış için bunu yapabilirsiniz. Akış arama hizmeti ek eklemektir *doğrulandı* özelliğiyle örnekler için aşağıdaki V3 akışları. NuGet istemci eklenen özelliğin akış V2'desteklemez.

Daha fazla bilgi için bkz: [API'nin arama hizmeti ile ilgili belgeler](../api/search-query-service-resource.md).