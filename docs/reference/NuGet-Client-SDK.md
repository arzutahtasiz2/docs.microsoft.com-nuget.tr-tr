---
title: NuGet İstemci SDK’sı
description: API gelişiyor ve henüz belgelenmemiştir, ancak örnek, bave Glick 'in blogundan bulunabilir.
author: karann-msft
ms.author: karann
ms.date: 01/09/2018
ms.topic: conceptual
ms.openlocfilehash: 39a4de4071eec70c88a2add158f2a3a734f7d7b7
ms.sourcegitcommit: cbc87fe51330cdd3eacaad3e8656eb4258882fc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88622934"
---
# <a name="nuget-client-sdk"></a>NuGet İstemci SDK’sı

*NuGet istemci SDK 'sı* bir NuGet paketleri grubunu ifade eder:

* [`NuGet.Protocol`](https://www.nuget.org/packages/NuGet.Protocol) -HTTP ve dosya tabanlı NuGet akışlarıyla etkileşim kurmak için kullanılır
* [`NuGet.Packaging`](https://www.nuget.org/packages/NuGet.Packaging) -NuGet paketleri ile etkileşim kurmak için kullanılır. `NuGet.Protocol` Bu pakete bağımlıdır

Bu paketlerin kaynak kodunu [NuGet/NuGet. Client](https://github.com/NuGet/NuGet.Client) GitHub deposunda bulabilirsiniz.

> [!Note]
> NuGet sunucu protokolü hakkındaki belgeler için lütfen [NuGet sunucu API](~/api/overview.md)'sine bakın.

## <a name="getting-started"></a>Başlarken

### <a name="install-the-packages"></a>Paketleri yükler

```ps1
dotnet add package NuGet.Protocol  # interact with HTTP and folder-based NuGet package feeds, includes NuGet.Packaging

dotnet add package NuGet.Packaging # interact with .nupkg and .nuspec files from a stream
```

## <a name="examples"></a>Örnekler

Bu örnekleri GitHub 'da [NuGet. Protocol. Samples](https://github.com/NuGet/Samples/tree/master/NuGetProtocolSamples) projesinde bulabilirsiniz.

### <a name="list-package-versions"></a>Paket sürümlerini Listele

[NuGet V3 paketi IÇERIK API](../api/package-base-address-resource.md#enumerate-package-versions)'sini kullanarak tüm Newtonsoft.Jssürümlerini bulun:

[!code-csharp[ListPackageVersions](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=ListPackageVersions)]

### <a name="download-a-package"></a>Paket indir

[NuGet V3 paketi IÇERIK API](../api/package-base-address-resource.md)'sini kullanarak v 12.0.1 üzerinde Newtonsoft.Jsindirin:

[!code-csharp[DownloadPackage](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=DownloadPackage)]

### <a name="get-package-metadata"></a>Paket meta verilerini al

[NuGet V3 paketi meta veri API 'sini](../api/registration-base-url-resource.md)kullanarak "Newtonsoft.Json" paketine ait meta verileri alın:

[!code-csharp[GetPackageMetadata](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=GetPackageMetadata)]

### <a name="search-packages"></a>Paketleri ara

[NuGet v3 arama API](../api/search-query-service-resource.md)'sini kullanarak "JSON" paketleri arayın:

[!code-csharp[SearchPackages](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=SearchPackages)]

### <a name="create-a-package"></a>Paket oluşturma

Bir paket oluşturun, meta veri ayarlayın ve kullanarak bağımlılıklar ekleyin [`NuGet.Packaging`](https://www.nuget.org/packages/NuGet.Packaging) .

> [!IMPORTANT]
> NuGet paketlerinin resmi NuGet **araçları kullanılarak oluşturulması ve bu** alt düzey API 'nin kullanılması önemle önerilir. İyi biçimlendirilmiş bir paket için önemli özellikler vardır ve araç en son sürümü bu en iyi uygulamaların sağlanmasına yardımcı olur.
> 
> NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz. [paket oluşturma iş akışına](../create-packages/overview-and-workflow.md) genel bakış ve resmi paket araçları (örneğin, [DotNet CLI kullanılarak](../create-packages/creating-a-package-dotnet-cli.md)) belgeleri.

[!code-csharp[CreatePackage](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=CreatePackage)]

### <a name="read-a-package"></a>Paket okuma

Kullanarak bir dosya akışından paket okuyun [`NuGet.Packaging`](https://www.nuget.org/packages/NuGet.Packaging) .

[!code-csharp[ReadPackage](~/../nuget-samples/NuGetProtocolSamples/Program.cs?name=ReadPackage)]

## <a name="third-party-documentation"></a>Üçüncü taraf belgeleri

Aşağıdaki blog serisindeki bazı API 'ler için örnekler ve belgeler için Glick, yayımlanan 2016:

- [NuGet v3 kitaplıklarını keşfetme, 1. Bölüm: giriş ve kavramlar](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-1)
- [NuGet v3 kitaplıklarını keşfetme, Bölüm 2: paketleri arama](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-2)
- [NuGet v3 kitaplıklarını keşfetme, 3. Bölüm: paketleri yükleme](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-3)

> [!Note]
> Bu blog gönderileri, NuGet istemci SDK paketlerinin **3.4.3** sürümü yayımlandıktan kısa bir süre sonra yazıldı.
> Paketlerin daha yeni sürümleri, blog gönderilerinin bilgileriyle uyumsuz olabilir.

Marve Glick 'in blog serisine, NuGet paketlerini yüklemek için NuGet Istemci SDK 'sını kullanma konusunda farklı bir yaklaşım tanıtan bir izleme blog gönderisi Björkström.

- [NuGet v3 kitaplıklarını yeniden ziyaret etme](https://martinbjorkstrom.com/posts/2018-09-19-revisiting-nuget-client-libraries)
