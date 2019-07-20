---
title: NuGet CLı paketi komutu
description: NuGet. exe paketi komutu için başvuru
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 0e12944bdd5d43b8b9e84908be480a5249dd924f
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68328302"
---
# <a name="pack-command-nuget-cli"></a>Pack komutu (NuGet CLı)

**Uygulama hedefi:** paket oluşturma &bullet; **Desteklenen sürümler:** 2.7+

Belirtilen `.nuspec` veya proje dosyasını temel alan bir NuGet paketi oluşturur. Komut (bkz. [DotNet komutları](../dotnet-Commands.md)) ve `msbuild -t:pack` (bkz. [MSBuild hedefleri](../msbuild-targets.md)), alternatifler olarak kullanılabilir. `dotnet pack`

> [!Important]
> Mono bölümünde proje dosyasından bir paket oluşturmak desteklenmez. NuGet. exe Windows yol adları 'in kendisini dönüştürmediğinden, `.nuspec` dosyadaki yerel olmayan yolları UNIX stili yollarla da ayarlamanız gerekir.

## <a name="usage"></a>Kullanım

```cli
nuget pack <nuspecPath | projectPath> [options] [-Properties ...]
```

Burada `<nuspecPath>` veya proje dosyasını sırasıyla belirtin.`<projectPath>` `.nuspec`

## <a name="options"></a>Seçenekler

| Seçenek | Açıklama |
| --- | --- |
| BasePath | `.nuspec` Dosyada tanımlanan dosyaların temel yolunu ayarlar. |
| Yapı | Paketi oluşturmadan önce projenin oluşturulması gerektiğini belirtir. |
| Amaz | Bir paket oluştururken dışlanacak bir veya daha fazla joker karakter deseni belirtir. Birden fazla model belirtmek için-exclude bayrağını tekrarlayın. Aşağıdaki örneğe bakın. |
| Excludeemptydizinler | Paketi oluştururken boş dizinlerin eklenmesini engeller. |
| ForceEnglishOutput | *(3,5 +)* NuGet. exe ' yi sabit, Ingilizce tabanlı bir kültür kullanarak çalışmaya zorlar. |
| ConfigFile | Paket komutu için yapılandırma dosyasını belirtin. |
| Help | Komut için yardım bilgilerini görüntüler. |
| IncludeReferencedProjects | Oluşturulan paketin, bağımlılık olarak veya paketin parçası olarak başvurulan projeleri içermesi gerektiğini gösterir. Başvurulan bir proje, projeyle aynı ada `.nuspec` sahip karşılık gelen bir dosya içeriyorsa, bu başvurulan proje bir bağımlılık olarak eklenir. Aksi takdirde, başvurulan proje, paketin parçası olarak eklenir. |
| minClientVersion | Oluşturulan paket için *Minclientversion* özniteliğini ayarlayın. Bu değer, `.nuspec` dosyadaki var olan *minclientversion* özniteliğinin (varsa) değerini geçersiz kılar. |
| MSBuildPath | *(4.0 +)* Komutuyla birlikte kullanılacak MSBuild 'in yolunu belirtir `-MSBuildVersion`. |
| MSBuildVersion | *(3.2 +)* Bu komutla kullanılacak MSBuild sürümünü belirtir. Desteklenen değerler şunlardır 4, 12, 14, 15,1, 15,3, 15,4, 15,5, 15,6, 15,7, 15,8, 15,9. Varsayılan olarak, yolunuzda MSBuild çekilir, aksi takdirde en yüksek MSBuild 'in yüklü sürümü varsayılan olarak ayarlanır. |
| NoDefaultExcludes | , `.svn` Ve`.gitignore`gibi bir noktayla başlayan NuGet paket dosyalarının ve dosyalarının ve klasörlerinin varsayılan dışlamasını engeller. |
| NoPackageAnalysis | Paketi derlemeden sonra paketin paket analizini çalıştırmamalıdır. |
| OutputDirectory | Oluşturulan Paketin depolandığı klasörü belirtir. Hiçbir klasör belirtilmemişse, geçerli klasör kullanılır. |
| Özellikler | Diğer seçeneklerden sonra komut satırında son olarak görünmelidir. Proje dosyasındaki değerleri geçersiz kılan özelliklerin bir listesini belirtir; Özellik adları için bkz. [Ortak MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties) . Burada bulunan Properties bağımsız değişkeni, noktalı virgülle ayrılmış bir belirteç = değer çiftleri listesi ve `$token$` `.nuspec` dosyadaki her oluşumun verilen değer ile değiştirilmesidir. Değerler, tırnak işaretleri içinde dizeler olabilir. "Yapılandırma" özelliği için varsayılan "hata ayıkla" dır. Bir sürüm yapılandırmasına geçiş yapmak için kullanın `-Properties Configuration=Release`. |
| Önekini | *(3.4.4 +)* Genellikle derleme veya diğer yayın öncesi tanımlayıcıları eklemek için kullanılan, dahili olarak oluşturulan sürüm numarasına bir sonek ekler. Örneğin, kullanmak `-suffix nightly` gibi `1.2.3-nightly`sürüm numarasına sahip bir paket oluşturur. Farklı NuGet ve NuGet Paket Yöneticisi sürümleriyle uyarı, hata ve potansiyel uyumsuzluktan kaçınmak için son ekler bir harfle başlamalıdır. |
| Simgeleri | Paketin kaynakları ve sembolleri içerdiğini belirtir. Bir `.nuspec` dosya ile kullanıldığında, bu, normal bir NuGet paket dosyası ve ilgili semboller paketini oluşturur. Varsayılan olarak, eski bir [sembol paketi](../../create-packages/Symbol-Packages.md)oluşturur. Sembol paketleri için önerilen yeni biçim. snupkg 'dir. Bkz. [sembol paketleri oluşturma (. snupkg)](../../create-packages/Symbol-Packages-snupkg.md). |
| Aracı | Projenin çıkış dosyalarının `tool` klasöre yerleştirilmesi gerektiğini belirtir. |
| Verbosity | Çıktıda görünen ayrıntı miktarını belirtir: *normal*, *sessiz*, *ayrıntılı*. |
| Sürüm | `.nuspec` Dosyadaki sürüm numarasını geçersiz kılar. |

Ayrıca bkz. [ortam değişkenleri](cli-ref-environment-variables.md)

## <a name="excluding-development-dependencies"></a>Geliştirme bağımlılıklarını hariç tutma

Bazı NuGet paketleri geliştirme bağımlılıkları olarak faydalıdır, bu da kendi kitaplığınızı yazmanıza yardımcı olur, ancak gerçek paket bağımlılıkları olarak gerekli değildir.

`developmentDependency` `packages.config` Komutu,`package` özniteliği olarak`true`ayarlanmış olan içindeki girişleri yoksayar. `pack` Bu girişler oluşturulan pakette bir bağımlılık olarak dahil edilmez.

Örneğin, kaynak projede aşağıdaki `packages.config` dosyayı göz önünde bulundurun:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="jQuery" version="1.5.2" />
    <package id="netfx-Guard" version="1.3.3.2" developmentDependency="true" />
    <package id="microsoft-web-helpers" version="1.15" />
</packages>
```

Bu `nuget pack` proje için tarafından oluşturulan paketin `jQuery` bağımlılığı `microsoft-web-helpers` olur, ancak uygulanmaz `netfx-Guard`.

## <a name="examples"></a>Örnekler

```cli
nuget pack

nuget pack foo.nuspec

nuget pack foo.csproj

nuget pack foo.csproj -Properties Configuration=Release

nuget pack foo.csproj -Build -Symbols -Properties owners=janedoe,xiaop;version="1.0.5"

# Create a package from project foo.csproj, using MSBuild version 12 to build the project
nuget pack foo.csproj -Build -Symbols -MSBuildVersion 12 -Properties owners=janedoe,xiaop;version="1.0.5"

# Create a package from project foo.nuspec and the corresponding symbol package using the new recommended format .snupkg
nuget pack foo.nuspec -Symbols -SymbolPackageFormat snupkg

nuget pack foo.nuspec -Version 2.1.0

nuget pack foo.nuspec -Version 1.0.0 -MinClientVersion 2.5

nuget pack Package.nuspec -exclude "*.exe" -exclude "*.bat"
```