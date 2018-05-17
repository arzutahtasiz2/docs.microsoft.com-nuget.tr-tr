---
title: (İçin iOS, Android ve Windows) Xamarin ile Visual Studio 2015 için NuGet paketleri oluşturma
description: NuGet paketleri için Xamarin oluşturduğunuz bir uçtan uca kılavuz, iOS, Android ve Windows yerel API'leri kullanın.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/09/2017
ms.topic: tutorial
ms.openlocfilehash: 1189151b04da6dc4c7b680f759b6a8ca7c5bd85f
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="create-packages-for-xamarin-with-visual-studio-2015"></a><span data-ttu-id="754ad-103">Xamarin ile Visual Studio 2015 için paketler oluşturma</span><span class="sxs-lookup"><span data-stu-id="754ad-103">Create packages for Xamarin with Visual Studio 2015</span></span>

<span data-ttu-id="754ad-104">Bir paket xamarin çalışma zamanı işletim sistemine bağlı iOS, Android ve Windows, yerel API'lerini kullanan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="754ad-104">A package for Xamarin contains code that uses native APIs on iOS, Android, and Windows, depending on the run-time operating system.</span></span> <span data-ttu-id="754ad-105">Bunu yapmak basit olmasına karşın, geliştiricilerin bir PCL paketinden kullanmasına izin vermek için tercih edilir veya ortak bir API üzerinden .NET standart kitaplıkları yüzey alanı.</span><span class="sxs-lookup"><span data-stu-id="754ad-105">Although this is straightforward to do, it's preferable to let developers consume the package from a PCL or .NET Standard libraries through a common API surface area.</span></span>

<span data-ttu-id="754ad-106">Kullandığınız bu kılavuzda, Visual Studio 2015 iOS, Android ve Windows mobil projelerinde kullanılan bir platformlar arası NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="754ad-106">In this walkthrough you use Visual Studio 2015 create a cross-platform NuGet package that can be used in mobile projects on iOS, Android, and Windows.</span></span>

1. [<span data-ttu-id="754ad-107">Önkoşulları</span><span class="sxs-lookup"><span data-stu-id="754ad-107">Prerequisites</span></span>](#prerequisites)
1. [<span data-ttu-id="754ad-108">Proje yapısı ve Özet kodu oluşturma</span><span class="sxs-lookup"><span data-stu-id="754ad-108">Create the project structure and abstraction code</span></span>](#create-the-project-structure-and-abstraction-code)
1. [<span data-ttu-id="754ad-109">Platforma özgü kod yazma</span><span class="sxs-lookup"><span data-stu-id="754ad-109">Write your platform-specific code</span></span>](#write-your-platform-specific-code)
1. [<span data-ttu-id="754ad-110">Oluşturun ve .nuspec dosyası güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="754ad-110">Create and update the .nuspec file</span></span>](#create-and-update-the-nuspec-file)
1. [<span data-ttu-id="754ad-111">Paket bileşeni</span><span class="sxs-lookup"><span data-stu-id="754ad-111">Package the component</span></span>](#package-the-component)
1. [<span data-ttu-id="754ad-112">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="754ad-112">Related topics</span></span>](#related-topics)

## <a name="prerequisites"></a><span data-ttu-id="754ad-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="754ad-113">Prerequisites</span></span>

1. <span data-ttu-id="754ad-114">Evrensel Windows Platformu (UWP) ve Xamarin ile Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="754ad-114">Visual Studio 2015 with Universal Windows Platform (UWP) and Xamarin.</span></span> <span data-ttu-id="754ad-115">Community edition ücretsiz yükleyin [visualstudio.com](https://www.visualstudio.com/); Elbette Professional ve Enterprise sürümleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="754ad-115">Install the Community edition for free from [visualstudio.com](https://www.visualstudio.com/); you can use the Professional and Enterprise editions as well, of course.</span></span> <span data-ttu-id="754ad-116">UWP ve Xamarin Araçları eklemek için bir özel yükleme seçeneğini belirleyin ve uygun seçenekleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-116">To include UWP and Xamarin tools, select a Custom install and check the appropriate options.</span></span>
1. <span data-ttu-id="754ad-117">NuGet CLI.</span><span class="sxs-lookup"><span data-stu-id="754ad-117">NuGet CLI.</span></span> <span data-ttu-id="754ad-118">Nuget.exe en son sürümünü indirme [nuget.org/downloads](https://nuget.org/downloads), tercih ettiğiniz bir konuma kaydetme.</span><span class="sxs-lookup"><span data-stu-id="754ad-118">Download the latest version of nuget.exe from [nuget.org/downloads](https://nuget.org/downloads), saving it to a location of your choice.</span></span> <span data-ttu-id="754ad-119">Zaten yoksa bu konum, PATH ortam değişkenine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-119">Then add that location to your PATH environment variable if it isn't already.</span></span>

> [!Note]
> <span data-ttu-id="754ad-120">nuget.exe CLI aracı kendisini bir yükleyici nedenle bunu çalıştırmak yerine tarayıcınızdan indirilen dosyayı kaydettiğinizden emin olur.</span><span class="sxs-lookup"><span data-stu-id="754ad-120">nuget.exe is the CLI tool itself, not an installer, so be sure to save the downloaded file from your browser instead of running it.</span></span>

## <a name="create-the-project-structure-and-abstraction-code"></a><span data-ttu-id="754ad-121">Proje yapısı ve Özet kodu oluşturma</span><span class="sxs-lookup"><span data-stu-id="754ad-121">Create the project structure and abstraction code</span></span>

1. <span data-ttu-id="754ad-122">İndirme ve çalıştırma [Xamarin Şablonları uzantısı eklentisi](https://marketplace.visualstudio.com/items?itemName=vs-publisher-473885.PluginForXamarinTemplates) Visual Studio için.</span><span class="sxs-lookup"><span data-stu-id="754ad-122">Download and run the [Plugin for Xamarin Templates extension](https://marketplace.visualstudio.com/items?itemName=vs-publisher-473885.PluginForXamarinTemplates) for Visual Studio.</span></span> <span data-ttu-id="754ad-123">Bu şablonlar bu kılavuz için gerekli Proje yapısı oluşturmak kolaylaştıracak.</span><span class="sxs-lookup"><span data-stu-id="754ad-123">These templates will make it easy to create the necessary project structure for this walkthrough.</span></span>
1. <span data-ttu-id="754ad-124">Visual Studio'da **Dosya > Yeni > Proje**, arama `Plugin`seçin **xamarin eklentisi** şablonu adı için LoggingLibrary değiştirin ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="754ad-124">In Visual Studio, **File > New > Project**, search for `Plugin`, select the **Plugin for Xamarin** template, change the name to LoggingLibrary, and click OK.</span></span>

    ![Visual Studio'da yeni boş uygulama (Xamarin.Forms taşınabilir) projesi](media/CrossPlatform-NewProject.png)

<span data-ttu-id="754ad-126">Sonuçta elde edilen çözüm çeşitli platforma özgü projeleri birlikte iki PCL projeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="754ad-126">The resulting solution contains two PCL projects, along with a variety of platform-specific projects:</span></span>

- <span data-ttu-id="754ad-127">Adlı PCL `Plugin.LoggingLibrary.Abstractions (Portable)`, bu durumda bileşenin ortak arabirimi (API yüzey alanını) tanımlar `ILoggingLibrary` ILoggingLibrary.cs dosyasında yer alan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="754ad-127">The PCL named `Plugin.LoggingLibrary.Abstractions (Portable)`, defines the public interface (the API surface area) of the component, in this case the `ILoggingLibrary` interface contained in the ILoggingLibrary.cs file.</span></span> <span data-ttu-id="754ad-128">Arabirim kitaplığınıza tanımladığınız budur.</span><span class="sxs-lookup"><span data-stu-id="754ad-128">This is where you define the interface to your library.</span></span>
- <span data-ttu-id="754ad-129">Diğer PCL `Plugin.LoggingLibrary (Portable)`, çalışma zamanında soyut arabiriminin bir platforma özgü uygulamasını bulun CrossLoggingLibrary.cs kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="754ad-129">The other PCL, `Plugin.LoggingLibrary (Portable)`, contains code in CrossLoggingLibrary.cs that will locate a platform-specific implementation of the abstract interface at run time.</span></span> <span data-ttu-id="754ad-130">Genellikle, bu dosyayı değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="754ad-130">You typically don't need to modify this file.</span></span>
- <span data-ttu-id="754ad-131">Platforma özgü projeleri, gibi `Plugin.LoggingLibrary.Android`, her içeren ilgili LoggingLibraryImplementation.cs dosyalarına arabiriminde yerel bir uygulama içerir.</span><span class="sxs-lookup"><span data-stu-id="754ad-131">The platform-specific projects, such as `Plugin.LoggingLibrary.Android`, each contain contain a native implementation of the interface in their respective LoggingLibraryImplementation.cs files.</span></span> <span data-ttu-id="754ad-132">Burada kitaplığınızın kodu derleme budur.</span><span class="sxs-lookup"><span data-stu-id="754ad-132">This is where you build out your library's code.</span></span>

<span data-ttu-id="754ad-133">Varsayılan olarak, arabirim tanımı, ancak hiçbir yöntemi soyutlamalar projesinin ILoggingLibrary.cs dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="754ad-133">By default, the ILoggingLibrary.cs file of the Abstractions project contains an interface definition, but no methods.</span></span> <span data-ttu-id="754ad-134">Bu kılavuzda amaçları doğrultusunda eklemek bir `Log` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="754ad-134">For the purposes of this walkthrough, add a `Log` method as follows:</span></span>

```cs
using System;

namespace Plugin.LoggingLibrary.Abstractions
{
    /// <summary>
    /// Interface for LoggingLibrary
    /// </summary>
    public interface ILoggingLibrary
    {
        /// <summary>
        /// Log a message
        /// </summary>
        void Log(string text);
    }
}
```

## <a name="write-your-platform-specific-code"></a><span data-ttu-id="754ad-135">Platforma özgü kod yazma</span><span class="sxs-lookup"><span data-stu-id="754ad-135">Write your platform-specific code</span></span>

<span data-ttu-id="754ad-136">Platforma özgü uyarlamasını uygulamak için `ILoggingLibrary` arabirimi ve yöntemlerinden, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="754ad-136">To implement a platform-specific implementation of the `ILoggingLibrary` interface and its methods, do the following:</span></span>

1. <span data-ttu-id="754ad-137">Açık `LoggingLibraryImplementation.cs` dosya her platform için proje ve gerekli kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-137">Open the `LoggingLibraryImplementation.cs` file of each platform project and add the necessary code.</span></span> <span data-ttu-id="754ad-138">Örneğin (kullanarak `Plugin.LoggingLibrary.Android` Proje):</span><span class="sxs-lookup"><span data-stu-id="754ad-138">For example (using the `Plugin.LoggingLibrary.Android` project):</span></span>

    ```cs
    using Plugin.LoggingLibrary.Abstractions;
    using System;

    namespace Plugin.LoggingLibrary
    {
        /// <summary>
        /// Implementation for Feature
        /// </summary>
        public class LoggingLibraryImplementation : ILoggingLibrary
        {
            /// <summary>
            /// Log a message
            /// </summary>
            public void Log(string text)
            {
                throw new NotImplementedException("Called Log on Android");
            }
        }
    }
    ```

1. <span data-ttu-id="754ad-139">Bu uygulama projelerinde desteklemek istediğiniz her platform için yineleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-139">Repeat this implementation in the projects for each platform you want to support.</span></span>
1. <span data-ttu-id="754ad-140">İOS projesine sağ tıklayın, **özellikleri**, tıklatın **yapı** sekmesini tıklatın ve "\iPhone" kaldırma **çıkış yolu** ve **XML belge dosyası**  ayarlar.</span><span class="sxs-lookup"><span data-stu-id="754ad-140">Right-click the iOS project, select **Properties**, click the **Build** tab, and remove "\iPhone" from the **Output path** and **XML documentation file** settings.</span></span> <span data-ttu-id="754ad-141">Bu kılavuzda daha sonra kolaylık sağlamak için yalnızca budur.</span><span class="sxs-lookup"><span data-stu-id="754ad-141">This is just for later convenience in this walkthrough.</span></span> <span data-ttu-id="754ad-142">İşiniz bittiğinde dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="754ad-142">Save the file when done.</span></span>
1. <span data-ttu-id="754ad-143">Çözüme sağ tıklayın, seçin **Configuration Manager...** ve denetleme **yapı** PCLs ve destekleyen her platform için kutuları.</span><span class="sxs-lookup"><span data-stu-id="754ad-143">Right-click the solution, select **Configuration Manager...**, and check the **Build** boxes for the PCLs and each platform you're supporting.</span></span>
1. <span data-ttu-id="754ad-144">Çözüme sağ tıklayın ve seçin **yapı çözümü** çalışmanızı iade etme ve sonraki paketini yapıları üretmek için.</span><span class="sxs-lookup"><span data-stu-id="754ad-144">Right-click the solution and select **Build Solution** to check your work and produce the artifacts that you package next.</span></span> <span data-ttu-id="754ad-145">Eksik başvurular hakkında hata alırsanız, çözüme sağ tıklayın, seçin **NuGet paketleri geri** bağımlılıkları yükler ve yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="754ad-145">If you get errors about missing references, right-click the solution, select **Restore NuGet Packages** to install dependencies, and rebuild.</span></span>

> [!Note]
> <span data-ttu-id="754ad-146">İOS için oluşturmak için Visual Studio için açıklandığı gibi bağlı ağa bağlı bir Mac gereksinim [Visual Studio Xamarin.iOS için giriş](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/).</span><span class="sxs-lookup"><span data-stu-id="754ad-146">To build for iOS you need a networked Mac connected to Visual Studio as described on [Introduction to Xamarin.iOS for Visual Studio](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/).</span></span> <span data-ttu-id="754ad-147">Kullanılabilir bir Mac yoksa, Yapılandırma Yöneticisi'ni (yukarıdaki adım 3) IOS projede temizleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-147">If you don't have a Mac available, clear the iOS project in the configuration manager (step 3 above).</span></span>

## <a name="create-and-update-the-nuspec-file"></a><span data-ttu-id="754ad-148">Oluşturun ve .nuspec dosyası güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="754ad-148">Create and update the .nuspec file</span></span>

1. <span data-ttu-id="754ad-149">Bir komut istemi açıp `LoggingLibrary` where bir düzeyin klasörü `.sln` dosyası olduğunu ve NuGet çalıştırın `spec` ilk oluşturmak için komutu `Package.nuspec` dosyası:</span><span class="sxs-lookup"><span data-stu-id="754ad-149">Open a command prompt, navigate to the `LoggingLibrary` folder that's one level below where the `.sln` file is, and run the NuGet `spec` command to create the initial `Package.nuspec` file:</span></span>

    ```cli
    nuget spec
    ```

1. <span data-ttu-id="754ad-150">Bu dosyayı yeniden adlandırmak `LoggingLibrary.nuspec` ve bir düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="754ad-150">Rename this file to `LoggingLibrary.nuspec` and open it in an editor.</span></span>
1. <span data-ttu-id="754ad-151">Aşağıdaki ile eşleşecek şekilde dosyasını güncelleştirme adiniz uygun bir değerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="754ad-151">Update the file to match the following, replacing YOUR_NAME with an appropriate value.</span></span> <span data-ttu-id="754ad-152">`<id>` Değeri, özellikle, benzersiz olmalıdır nuget.org (açıklanan adlandırma kuralları Bkz [paket oluşturma](../create-packages/creating-a-package.md#choosing-a-unique-package-identifier-and-setting-the-version-number)).</span><span class="sxs-lookup"><span data-stu-id="754ad-152">The `<id>` value, specifically, must be unique across nuget.org (see the naming conventions described in [Creating a package](../create-packages/creating-a-package.md#choosing-a-unique-package-identifier-and-setting-the-version-number)).</span></span> <span data-ttu-id="754ad-153">Ayrıca yazar ve açıklama etiketleri güncelleştirmeniz gerekir veya paket adımı sırasında bir hata alıyorsunuz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="754ad-153">Also note that you must also update the author and description tags or you get an error during the packing step.</span></span>

    ```xml
    <?xml version="1.0"?>
    <package >
        <metadata>
        <id>LoggingLibrary.YOUR_NAME</id>
        <version>1.0.0</version>
        <title>LoggingLibrary</title>
        <authors>YOUR_NAME</authors>
        <owners>YOUR_NAME</owners>
        <requireLicenseAcceptance>false</requireLicenseAcceptance>
        <description>Awesome application logging utility</description>
        <releaseNotes>First release</releaseNotes>
        <copyright>Copyright 2016</copyright>
        <tags>logger logging logs</tags>
        </metadata>
    </package>
    ```

> [!Tip]
> <span data-ttu-id="754ad-154">Paket sürümü ile soneki `-alpha`, `-beta` veya `-rc` paketinizi yayın öncesi olarak işaretlemek için kontrol [yayın öncesi sürümleri](../create-packages/prerelease-packages.md) yayın öncesi sürümleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="754ad-154">You can suffix your package version with `-alpha`, `-beta` or `-rc` to mark your package as pre-release, check [Pre-release versions](../create-packages/prerelease-packages.md) for more information about pre-release versions.</span></span>

### <a name="add-reference-assemblies"></a><span data-ttu-id="754ad-155">Başvuru derlemeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="754ad-155">Add reference assemblies</span></span>

<span data-ttu-id="754ad-156">Platforma özgü başvuru derlemeleri eklemek için aşağıdakileri ekleyin `<files>` öğesinin `LoggingLibrary.nuspec` , desteklenen platformlar için uygun şekilde:</span><span class="sxs-lookup"><span data-stu-id="754ad-156">To include platform-specific reference assemblies, add the following to the `<files>` element of `LoggingLibrary.nuspec` as appropriate for your supported platforms:</span></span>

```xml
<!-- Insert below <metadata> element -->
<files>
    <!-- Cross-platform reference assemblies -->
    <file src="Plugin.LoggingLibrary\bin\Release\Plugin.LoggingLibrary.dll" target="lib\netstandard1.4\Plugin.LoggingLibrary.dll" />
    <file src="Plugin.LoggingLibrary\bin\Release\Plugin.LoggingLibrary.xml" target="lib\netstandard1.4\Plugin.LoggingLibrary.xml" />
    <file src="Plugin.LoggingLibrary.Abstractions\bin\Release\Plugin.LoggingLibrary.Abstractions.dll" target="lib\netstandard1.4\Plugin.LoggingLibrary.Abstractions.dll" />
    <file src="Plugin.LoggingLibrary.Abstractions\bin\Release\Plugin.LoggingLibrary.Abstractions.xml" target="lib\netstandard1.4\Plugin.LoggingLibrary.Abstractions.xml" />

    <!-- iOS reference assemblies -->
    <file src="Plugin.LoggingLibrary.iOS\bin\Release\Plugin.LoggingLibrary.dll" target="lib\Xamarin.iOS10\Plugin.LoggingLibrary.dll" />
    <file src="Plugin.LoggingLibrary.iOS\bin\Release\Plugin.LoggingLibrary.xml" target="lib\Xamarin.iOS10\Plugin.LoggingLibrary.xml" />

    <!-- Android reference assemblies -->
    <file src="Plugin.LoggingLibrary.Android\bin\Release\Plugin.LoggingLibrary.dll" target="lib\MonoAndroid10\Plugin.LoggingLibrary.dll" />
    <file src="Plugin.LoggingLibrary.Android\bin\Release\Plugin.LoggingLibrary.xml" target="lib\MonoAndroid10\Plugin.LoggingLibrary.xml" />

    <!-- UWP reference assemblies -->
    <file src="Plugin.LoggingLibrary.UWP\bin\Release\Plugin.LoggingLibrary.dll" target="lib\UAP10\Plugin.LoggingLibrary.dll" />
    <file src="Plugin.LoggingLibrary.UWP\bin\Release\Plugin.LoggingLibrary.xml" target="lib\UAP10\Plugin.LoggingLibrary.xml" />
</files>
```

> [!Note]
> <span data-ttu-id="754ad-157">DLL ve XML dosyalarının adlarını kısaltmak için tüm verilen projeye, select sağ tıklayın **Kitaplığı** sekmesinde ve derleme adları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="754ad-157">To shorten the names of the DLL and XML files, right-click on any given project, select the **Library** tab, and change the assembly names.</span></span>

### <a name="add-dependencies"></a><span data-ttu-id="754ad-158">Bağımlılıkları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="754ad-158">Add dependencies</span></span>

<span data-ttu-id="754ad-159">Yerel uygulamaları için belirli bağımlılıkları varsa, `<dependencies>` öğeyle `<group>` öğeleri, örneğin belirtin:</span><span class="sxs-lookup"><span data-stu-id="754ad-159">If you have specific dependencies for native implementations, use the `<dependencies>` element with `<group>` elements to specify them, for example:</span></span>

```xml
<!-- Insert within the <metadata> element -->
<dependencies>
    <group targetFramework="MonoAndroid">
        <!--MonoAndroid dependencies go here-->
    </group>
    <group targetFramework="Xamarin.iOS10">
        <!--Xamarin.iOS10 dependencies go here-->
    </group>
    <group targetFramework="uap">
        <!--uap dependencies go here-->
    </group>
</dependencies>
```

<span data-ttu-id="754ad-160">Örneğin, aşağıdaki iTextSharp UAP hedef için bağımlılık olarak ayarlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="754ad-160">For example, the following would set iTextSharp as a dependency for the UAP target:</span></span>

```xml
<dependencies>
    <group targetFramework="uap">
        <dependency id="iTextSharp" version="5.5.9" />
    </group>
</dependencies>
```

### <a name="final-nuspec"></a><span data-ttu-id="754ad-161">Son .nuspec</span><span class="sxs-lookup"><span data-stu-id="754ad-161">Final .nuspec</span></span>

<span data-ttu-id="754ad-162">Son `.nuspec` dosya artık görünmelidir aşağıdaki gibi burada yeniden adiniz uygun bir değerle değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="754ad-162">Your final `.nuspec` file should now look like the following, where again YOUR_NAME should be replaced with an appropriate value:</span></span>

```xml
<?xml version="1.0"?>
<package >
    <metadata>
    <id>LoggingLibrary.YOUR_NAME</id>
    <version>1.0.0</version>
    <title>LoggingLibrary</title>
    <authors>YOUR_NAME</authors>
    <owners>YOUR_NAME</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>Awesome application logging utility</description>
    <releaseNotes>First release</releaseNotes>
    <copyright>Copyright 2016</copyright>
    <tags>logger logging logs</tags>
        <dependencies>
        <group targetFramework="MonoAndroid">
            <!--MonoAndroid dependencies go here-->
        </group>
        <group targetFramework="Xamarin.iOS10">
            <!--Xamarin.iOS10 dependencies go here-->
        </group>
        <group targetFramework="uap">
            <dependency id="iTextSharp" version="5.5.9" />
        </group>
    </dependencies>
    </metadata>
    <files>
        <!-- Cross-platform reference assemblies -->
        <file src="Plugin.LoggingLibrary\bin\Release\Plugin.LoggingLibrary.dll" target="lib\netstandard1.4\Plugin.LoggingLibrary.dll" />
        <file src="Plugin.LoggingLibrary\bin\Release\Plugin.LoggingLibrary.xml" target="lib\netstandard1.4\Plugin.LoggingLibrary.xml" />
        <file src="Plugin.LoggingLibrary.Abstractions\bin\Release\Plugin.LoggingLibrary.Abstractions.dll" target="lib\netstandard1.4\Plugin.LoggingLibrary.Abstractions.dll" />
        <file src="Plugin.LoggingLibrary.Abstractions\bin\Release\Plugin.LoggingLibrary.Abstractions.xml" target="lib\netstandard1.4\Plugin.LoggingLibrary.Abstractions.xml" />

        <!-- iOS reference assemblies -->
        <file src="Plugin.LoggingLibrary.iOS\bin\Release\Plugin.LoggingLibrary.dll" target="lib\Xamarin.iOS10\Plugin.LoggingLibrary.dll" />
        <file src="Plugin.LoggingLibrary.iOS\bin\Release\Plugin.LoggingLibrary.xml" target="lib\Xamarin.iOS10\Plugin.LoggingLibrary.xml" />

        <!-- Android reference assemblies -->
        <file src="Plugin.LoggingLibrary.Android\bin\Release\Plugin.LoggingLibrary.dll" target="lib\MonoAndroid10\Plugin.LoggingLibrary.dll" />
        <file src="Plugin.LoggingLibrary.Android\bin\Release\Plugin.LoggingLibrary.xml" target="lib\MonoAndroid10\Plugin.LoggingLibrary.xml" />

        <!-- UWP reference assemblies -->
        <file src="Plugin.LoggingLibrary.UWP\bin\Release\Plugin.LoggingLibrary.dll" target="lib\UAP10\Plugin.LoggingLibrary.dll" />
        <file src="Plugin.LoggingLibrary.UWP\bin\Release\Plugin.LoggingLibrary.xml" target="lib\UAP10\Plugin.LoggingLibrary.xml" />
    </files>
</package>
```

## <a name="package-the-component"></a><span data-ttu-id="754ad-163">Paket bileşeni</span><span class="sxs-lookup"><span data-stu-id="754ad-163">Package the component</span></span>

<span data-ttu-id="754ad-164">Tamamlanan ile `.nuspec` pakete eklemek için gereken tüm dosyaları başvuran, çalıştırmak hazırsınız `pack` komutu:</span><span class="sxs-lookup"><span data-stu-id="754ad-164">With the completed `.nuspec` referencing all the files you need to include in the package, you're ready to run the `pack` command:</span></span>

```cli
nuget pack LoggingLibrary.nuspec
```

<span data-ttu-id="754ad-165">Bu oluşturur `LoggingLibrary.YOUR_NAME.1.0.0.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="754ad-165">This will generate `LoggingLibrary.YOUR_NAME.1.0.0.nupkg`.</span></span> <span data-ttu-id="754ad-166">Gibi bir araç bu dosyayı açmayı [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ve tüm düğümleri genişleterek, aşağıdaki içeriğe bakın:</span><span class="sxs-lookup"><span data-stu-id="754ad-166">Opening this file in a tool like the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) and expanding all the nodes, you see the following contents:</span></span>

![NuGet paket LoggingLibrary paket gösteren Gezgini](media/Cross-Platform-PackageExplorer.png)

> [!Tip]
> <span data-ttu-id="754ad-168">A `.nupkg` yalnızca bir ZIP dosyasını farklı bir uzantıya sahip bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="754ad-168">A `.nupkg` file is just a ZIP file with a different extension.</span></span> <span data-ttu-id="754ad-169">Ayrıca paket içeriğini, daha sonra değiştirerek inceleyebilirsiniz `.nupkg` için `.zip`, ancak uzantı nuget.org için bir paket karşıya yüklemeden önce geri yüklemek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="754ad-169">You can also examine package contents, then, by changing `.nupkg` to `.zip`, but remember to restore the extension before uploading a package to nuget.org.</span></span>

<span data-ttu-id="754ad-170">Paketinizi diğer geliştiricileri için kullanılabilir yapmak için yönergeleri izleyin [bir paketi yayımlamaya](../create-packages/publish-a-package.md).</span><span class="sxs-lookup"><span data-stu-id="754ad-170">To make your package available to other developers,  follow the instructions on [Publish a package](../create-packages/publish-a-package.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="754ad-171">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="754ad-171">Related topics</span></span>

- [<span data-ttu-id="754ad-172">Nuspec başvurusu</span><span class="sxs-lookup"><span data-stu-id="754ad-172">Nuspec Reference</span></span>](../reference/nuspec.md)
- [<span data-ttu-id="754ad-173">Sembol paketleri</span><span class="sxs-lookup"><span data-stu-id="754ad-173">Symbol packages</span></span>](../create-packages/symbol-packages.md)
- [<span data-ttu-id="754ad-174">Paket sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="754ad-174">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="754ad-175">Birden çok .NET Framework sürümleri destekleme</span><span class="sxs-lookup"><span data-stu-id="754ad-175">Supporting Multiple .NET Framework Versions</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="754ad-176">MSBuild özellik ve hedefleri bir pakete dahil etme</span><span class="sxs-lookup"><span data-stu-id="754ad-176">Including MSBuild props and targets in a package</span></span>](../create-packages/creating-a-package.md#including-msbuild-props-and-targets-in-a-package)
- [<span data-ttu-id="754ad-177">Yerelleştirilmiş Paketler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="754ad-177">Creating Localized Packages</span></span>](../create-packages/creating-localized-packages.md)