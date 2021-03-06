---
title: DotNet CLı kullanarak bir NuGet paketi oluşturma
description: Dosyalar ve sürüm oluşturma gibi önemli karar noktaları da dahil olmak üzere bir NuGet paketi tasarlama ve oluşturma işlemine yönelik ayrıntılı kılavuz.
author: karann-msft
ms.author: karann
ms.date: 02/20/2020
ms.topic: conceptual
ms.openlocfilehash: 87b38d7a707d6175eb3347280784d9dfefd9c17d
ms.sourcegitcommit: cbc87fe51330cdd3eacaad3e8656eb4258882fc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "89359661"
---
# <a name="create-a-nuget-package-using-the-dotnet-cli"></a>DotNet CLı kullanarak bir NuGet paketi oluşturma

Paketinizin ne yaptığını veya hangi kodu içerdiğini bağımsız olarak, `nuget.exe` Bu işlevselliği bir veya daha fazla `dotnet.exe` Geliştirici tarafından kullanılabilen bir bileşene paketlemek için ya da CLI araçlarından birini kullanırsınız. Bu makalede, DotNet CLı kullanarak bir paketin nasıl oluşturulacağı açıklanır. `dotnet`CLI 'yı yüklemek için bkz. [NuGet istemci araçları 'nı yükler](../install-nuget-client-tools.md). Visual Studio 2017 ' den başlayarak, DotNet CLı .NET Core iş yüklerine dahildir.

NuGet, .NET Core ve .NET Standard [SDK stili biçimini](../resources/check-project-format.md)kullanan projeler ve diğer SDK stilindeki projeler için, proje dosyasındaki bilgileri doğrudan bir paket oluşturmak üzere kullanır. Adım adım öğreticiler için bkz. [DotNet CLI ile .NET Standard paketleri oluşturma](../quickstart/create-and-publish-a-package-using-the-dotnet-cli.md) veya [Visual Studio Ile .NET Standard paketleri oluşturma](../quickstart/create-and-publish-a-package-using-visual-studio.md).

`msbuild -t:pack` işlevine eşdeğerdir `dotnet pack` . MSBuild ile derlemek için bkz. [MSBuild kullanarak NuGet paketi oluşturma](creating-a-package-msbuild.md).

> [!IMPORTANT]
> Bu konu, genellikle .NET Core ve .NET Standard projeleri [SDK stilindeki](../resources/check-project-format.md) projeler için geçerlidir.

## <a name="set-properties"></a>Özellikleri ayarlama

Bir paket oluşturmak için aşağıdaki özellikler gereklidir.

- `PackageId`, paketi barındıran Galeri genelinde benzersiz olması gereken paket tanımlayıcısı. Belirtilmemişse, varsayılan değer `AssemblyName` .
- `Version`, *birincil. ikincil. Patch [-suffix]* biçiminde belirli bir sürüm numarası; burada *-suffix* [yayın öncesi sürümlerini](prerelease-packages.md)tanımlar. Belirtilmemişse, varsayılan değer 1.0.0 ' dir.
- Paket başlığı konakta görüntülenecek şekilde (nuget.org gibi)
- `Authors`, yazar ve sahip bilgileri. Belirtilmemişse, varsayılan değer `AssemblyName` .
- `Company`, şirketinizin adı. Belirtilmemişse, varsayılan değer `AssemblyName` .

Visual Studio 'da bu değerleri proje özelliklerinde ayarlayabilirsiniz (Çözüm Gezgini ' de projeye sağ tıklayıp **Özellikler**' i seçin ve **paket** sekmesini seçin). Bu özellikleri doğrudan proje dosyaları () içinde de ayarlayabilirsiniz `.csproj` .

```xml
<PropertyGroup>
  <PackageId>AppLogger</PackageId>
  <Version>1.0.0</Version>
  <Authors>your_name</Authors>
  <Company>your_company</Company>
</PropertyGroup>
```

> [!Important]
> Pakete nuget.org genelinde benzersiz bir tanımlayıcı verin veya kullandığınız herhangi bir paket kaynağını kullanın.

Aşağıdaki örnekte, bu özelliklerle birlikte basit ve tamamlanmış bir proje dosyası gösterilmektedir. (Komutunu kullanarak yeni bir varsayılan proje oluşturabilirsiniz `dotnet new classlib` .)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <PackageId>AppLogger</PackageId>
    <Version>1.0.0</Version>
    <Authors>your_name</Authors>
    <Company>your_company</Company>
  </PropertyGroup>
</Project>
```

Ayrıca,, ve gibi isteğe bağlı özellikleri, `Title` `PackageDescription` `PackageTags` [MSBuild paketi hedefleri](../reference/msbuild-targets.md#pack-target)' nde açıklandığı gibi, [bağımlılık varlıklarını denetleme](../consume-packages/package-references-in-project-files.md#controlling-dependency-assets)ve [NuGet meta verileri özelliklerini](/dotnet/core/tools/csproj#nuget-metadata-properties)de ayarlayabilirsiniz.

> [!NOTE]
> Genel tüketim için derlenmiş paketler için, paket **etiketleri** özelliğine özel bir dikkat edin, Etiketler başkalarının paketinizi bulmasına ve ne yaptığını anlamalarına yardımcı olur.

Bağımlılıkları bildirme ve sürüm numaralarını belirtme hakkında ayrıntılar için bkz. proje dosyaları ve [paket sürümü oluşturma](../concepts/package-versioning.md) [içindeki paket başvuruları](../consume-packages/package-references-in-project-files.md) . Ayrıca, ve özniteliklerini kullanarak doğrudan pakette bulunan bağımlılıklardan gelen bir varlık için de mümkündür `<IncludeAssets>` `<ExcludeAssets>` . Daha fazla bilgi için bkz. [bağımlılık varlıklarını denetleme](../consume-packages/package-references-in-project-files.md#controlling-dependency-assets).

## <a name="add-an-optional-description-field"></a>İsteğe bağlı açıklama alanı ekleme

[!INCLUDE [add description to package](includes/add-description.md)]

## <a name="choose-a-unique-package-identifier-and-set-the-version-number"></a>Benzersiz bir paket tanımlayıcısı seçin ve sürüm numarasını ayarlayın

[!INCLUDE [choose-package-id](includes/choose-package-id.md)]

## <a name="run-the-pack-command"></a>Pack komutunu çalıştırın

Projeden bir NuGet paketi (bir `.nupkg` dosya) oluşturmak için `dotnet pack` komutunu çalıştırın, bu da projeyi otomatik olarak oluşturur:

```dotnetcli
# Uses the project file in the current folder by default
dotnet pack
```

Çıktı, dosyanın yolunu gösterir `.nupkg` .

```output
Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 29.91 ms for D:\proj\AppLoggerNet\AppLogger\AppLogger.csproj.
  AppLogger -> D:\proj\AppLoggerNet\AppLogger\bin\Debug\netstandard2.0\AppLogger.dll
  Successfully created package 'D:\proj\AppLoggerNet\AppLogger\bin\Debug\AppLogger.1.0.0.nupkg'.
```

### <a name="automatically-generate-package-on-build"></a>Derleme üzerinde otomatik olarak paket oluştur

Çalıştırdığınızda otomatik olarak çalıştırmak için `dotnet pack` `dotnet build` , aşağıdaki satırı içindeki proje dosyanıza ekleyin `<PropertyGroup>` :

```xml
<GeneratePackageOnBuild>true</GeneratePackageOnBuild>
```

`dotnet pack`Bir çözümde çalıştırdığınızda bu, çözümdeki ( [<IsPackable>](/dotnet/core/tools/csproj#nuget-metadata-properties) özelliği olarak ayarlanır) Çözümdeki tüm projeleri paketler `true` .

> [!NOTE]
> Paketi otomatik olarak oluşturduğunuzda, paketlenecek süre projenizin derleme süresini arttırır.

### <a name="test-package-installation"></a>Test paketi yüklemesi

Bir paketi yayımlamadan önce, genellikle bir projeye paket yükleme işlemini test etmek istersiniz. Testler, gerekli dosyaların projenin doğru konumlarında bulunduğundan emin olmanızı ister.

Yüklemeleri, Visual Studio 'da veya normal [paket yükleme adımlarını](../consume-packages/overview-and-workflow.md#ways-to-install-a-nuget-package)kullanarak komut satırında el ile test edebilirsiniz.

> [!IMPORTANT]
> Paketler sabittir. Bir sorunu düzeltseniz, yeniden test ettiğinizde, siz de [genel paketler](../consume-packages/managing-the-global-packages-and-cache-folders.md#clearing-local-folders) klasörünüzü kaldırana kadar paketin eski sürümünü kullanmaya devam edersiniz. Bu, özellikle her derlemede benzersiz bir ön sürüm etiketi kullanmayan paketleri test ederken ilgilidir.

## <a name="next-steps"></a>Sonraki Adımlar

Bir dosya olan bir paket oluşturduktan sonra `.nupkg` , bir [paket yayımlama](../nuget-org/publish-a-package.md)konusunda açıklandığı gibi istediğiniz Galeri ile yayımlayabilirsiniz.

Ayrıca, aşağıdaki konularda açıklandığı gibi, paketinizin yeteneklerini genişletmek veya diğer senaryoları desteklemek isteyebilirsiniz:

- [Paket sürümü oluşturma](../concepts/package-versioning.md)
- [Birden çok hedef çerçeveyi destekleme](../create-packages/multiple-target-frameworks-project-file.md)
- [Paket simgesi ekleme](../reference/nuspec.md#icon)
- [Kaynak ve yapılandırma dosyalarının dönüştürmeleri](../create-packages/source-and-config-file-transformations.md)
- [Yerelleştirme](../create-packages/creating-localized-packages.md)
- [Yayın öncesi sürümler](../create-packages/prerelease-packages.md)
- [Paket türünü ayarlama](../create-packages/set-package-type.md)
- [COM birlikte çalışma Derlemeleriyle paket oluşturma](../create-packages/author-packages-with-COM-interop-assemblies.md)

Son olarak, bilmeniz için ek paket türleri vardır:

- [Yerel paketler](../guides/native-packages.md)
- [Sembol paketleri](../create-packages/symbol-packages-snupkg.md)
