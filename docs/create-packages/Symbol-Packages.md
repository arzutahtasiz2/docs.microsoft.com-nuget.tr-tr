---
title: NuGet simgesi paketleri oluşturma
description: Diğer NuGet paketleri Visual Studio'da hata ayıklamayı desteklemek için yalnızca sembolleri içeren NuGet paketleri oluşturma
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 09/12/2017
ms.topic: conceptual
ms.reviewer: anangaur
ms.openlocfilehash: cf8761ac4c994d864cd49a8fb31b3be626d4c0a6
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="creating-symbol-packages"></a><span data-ttu-id="32bb0-103">Sembol paketleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="32bb0-103">Creating symbol packages</span></span>

<span data-ttu-id="32bb0-104">Nuget.org veya diğer kaynakları NuGet paketleri de oluşturmanın yanı sıra oluşturmayı destekler, simge paketleri ve SymbolSource depoya yayımlama ilişkili.</span><span class="sxs-lookup"><span data-stu-id="32bb0-104">In addition to building packages for nuget.org or other sources, NuGet also supports creating associated symbol packages and publishing them to the SymbolSource repository.</span></span>

<span data-ttu-id="32bb0-105">Paket tüketicileri ardından ekleyebilirsiniz `https://nuget.smbsrc.net` Visual Studio'da simgesi kaynakları için böylece Visual Studio hata ayıklayıcısında paket koda atlama.</span><span class="sxs-lookup"><span data-stu-id="32bb0-105">Package consumers can then add `https://nuget.smbsrc.net` to their symbol sources in Visual Studio, which allows stepping into package code in the Visual Studio debugger.</span></span> <span data-ttu-id="32bb0-106">Bkz: [Visual Studio hata ayıklayıcısında simge (.pdb) ve kaynak dosyaları belirtme](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) işlem hakkında ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="32bb0-106">See [Specify symbol (.pdb) and source files in the Visual Studio debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) for details on that process.</span></span>

## <a name="creating-a-symbol-package"></a><span data-ttu-id="32bb0-107">Sembol paket oluşturma</span><span class="sxs-lookup"><span data-stu-id="32bb0-107">Creating a symbol package</span></span>

<span data-ttu-id="32bb0-108">Sembol paketi oluşturmak için bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="32bb0-108">To create a symbol package, follow these conventions:</span></span>

- <span data-ttu-id="32bb0-109">Birincil paketiyle (kodunuzu) ad `{identifier}.nupkg` ve tüm dosyalar hariç dahil `.pdb` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="32bb0-109">Name the primary package (with your code) `{identifier}.nupkg` and include all your files except `.pdb` files.</span></span>
- <span data-ttu-id="32bb0-110">Sembol paket adı `{identifier}.symbols.nupkg` ve derlemenizi DLL dahil `.pdb` dosyaları, XMLDOC dosyaları, kaynak dosyaları (bölümlerde bakın).</span><span class="sxs-lookup"><span data-stu-id="32bb0-110">Name the symbol package `{identifier}.symbols.nupkg` and include your assembly DLL, `.pdb` files, XMLDOC files, source files (see the sections that follow).</span></span>

<span data-ttu-id="32bb0-111">Her iki paketlerle oluşturabilirsiniz `-Symbols` herhangi birinden seçeneği bir `.nuspec` veya proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="32bb0-111">You can create both packages with the `-Symbols` option, either from a `.nuspec` file or a project file:</span></span>

```cli
nuget pack MyPackage.nuspec -Symbols

nuget pack MyProject.csproj -Symbols
```

<span data-ttu-id="32bb0-112">Unutmayın `pack` Mono 4.4.2 Mac OS x gerektirir ve Linux sistemlerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="32bb0-112">Note that `pack` requires Mono 4.4.2 on Mac OS X and does not work on Linux systems.</span></span> <span data-ttu-id="32bb0-113">Bir Mac üzerinde Windows yol adları olarak da dönüştürmelidir `.nuspec` UNIX stili yollara dosya.</span><span class="sxs-lookup"><span data-stu-id="32bb0-113">On a Mac, you must also convert Windows pathnames in the `.nuspec` file to Unix-style paths.</span></span>

## <a name="symbol-package-structure"></a><span data-ttu-id="32bb0-114">Sembol paket yapısı</span><span class="sxs-lookup"><span data-stu-id="32bb0-114">Symbol package structure</span></span>

<span data-ttu-id="32bb0-115">Sembol paketi birden çok hedef çerçeveyi kitaplık paketi yapan aynı şekilde hedefleyebilirsiniz böylece yapısını `lib` klasörü tam olarak aynı olmalıdır birincil paketi olarak dahil olmak üzere yalnızca `.pdb` yanında DLL dosyaları.</span><span class="sxs-lookup"><span data-stu-id="32bb0-115">A symbol package can target multiple target frameworks in the same way that a library package does, so the structure of the `lib` folder should be exactly the same as the primary package, only including `.pdb` files alongside the DLL.</span></span>

<span data-ttu-id="32bb0-116">Örneğin, .NET 4.0 ve Silverlight 4 hedefleyen bir sembol paketi bu düzeni sahip olur:</span><span class="sxs-lookup"><span data-stu-id="32bb0-116">For example, a symbol package that targets .NET 4.0 and Silverlight 4 would have this layout:</span></span>

    \lib
        \net40
            \MyAssembly.dll
            \MyAssembly.pdb
        \sl40
            \MyAssembly.dll
            \MyAssembly.pdb

<span data-ttu-id="32bb0-117">Kaynak dosyalarını sonra adlı ayrı bir özel klasöre yerleştirdiğiniz `src`, kaynak deponuz göreli yapısını izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="32bb0-117">Source files are then placed in a separate special folder named `src`, which must follow the relative structure of your source repository.</span></span> <span data-ttu-id="32bb0-118">Pdb mutlak yolları eşleşen DLL derlemek için kullanılan kaynak dosyaları içerir ve yayımlama işlemi sırasında bulunması gerekir çünkü budur.</span><span class="sxs-lookup"><span data-stu-id="32bb0-118">This is because PDBs contain absolute paths to source files used to compile the matching DLL, and they need to be found during the publishing process.</span></span> <span data-ttu-id="32bb0-119">Taban yol (ortak yolu önek) çıkarılır. Örneğin, bu dosyaları dışında oluşturulmuş bir kitaplık göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="32bb0-119">A base path (common path prefix) can be stripped out. For example, consider a library built from these files:</span></span>

    C:\Projects
        \MyProject
            \Common
                \MyClass.cs
            \Full
                \Properties
                    \AssemblyInfo.cs
                \MyAssembly.csproj (producing \lib\net40\MyAssembly.dll)
            \Silverlight
                \Properties
                    \AssemblyInfo.cs
                \MySilverlightExtensions.cs
                \MyAssembly.csproj (producing \lib\sl4\MyAssembly.dll)

<span data-ttu-id="32bb0-120">Apart gelen `lib` klasörü, bir sembol paketi gerekir bu düzeni içerir:</span><span class="sxs-lookup"><span data-stu-id="32bb0-120">Apart from the `lib` folder, a symbol package would need to contain this layout:</span></span>

    \src
        \Common
            \MyClass.cs
        \Full
            \Properties
                \AssemblyInfo.cs
        \Silverlight
            \Properties
                \AssemblyInfo.cs
            \MySilverlightExtensions.cs

## <a name="referring-to-files-in-the-nuspec"></a><span data-ttu-id="32bb0-121">Nuspec dosyalarında başvurma</span><span class="sxs-lookup"><span data-stu-id="32bb0-121">Referring to files in the nuspec</span></span>

<span data-ttu-id="32bb0-122">Sembol paketi kurallarından önceki bölümde açıklandığı gibi klasör yapısı veya içeriğini belirterek yerleşik `files` bildirim bölümü.</span><span class="sxs-lookup"><span data-stu-id="32bb0-122">A symbol package can be built by conventions, from a folder structure as described in the previous section, or by specifying its contents in the `files` section of the manifest.</span></span> <span data-ttu-id="32bb0-123">Örneğin, önceki bölümde gösterilen paketi oluşturmak için aşağıdakileri kullanın `.nuspec` dosyası:</span><span class="sxs-lookup"><span data-stu-id="32bb0-123">For example, to build the package shown in the previous section, use the following in the `.nuspec` file:</span></span>

```xml
<files>
    <file src="Full\bin\Debug\*.dll" target="lib\net40" />
    <file src="Full\bin\Debug\*.pdb" target="lib\net40" />
    <file src="Silverlight\bin\Debug\*.dll" target="lib\sl40" />
    <file src="Silverlight\bin\Debug\*.pdb" target="lib\sl40" />
    <file src="**\*.cs" target="src" />
</files>
```

## <a name="publishing-a-symbol-package"></a><span data-ttu-id="32bb0-124">Sembol Paketi Yayımlama</span><span class="sxs-lookup"><span data-stu-id="32bb0-124">Publishing a symbol package</span></span>

> [!Important]
> <span data-ttu-id="32bb0-125">Anında iletme paketlere kullanmalısınız nuget.org için [nuget.exe v4.1.0 veya yukarıdaki](https://www.nuget.org/downloads), gerekli uygulayan [NuGet protokolleri](../api/nuget-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="32bb0-125">To push packages to nuget.org you must use [nuget.exe v4.1.0 or above](https://www.nuget.org/downloads), which implements the required [NuGet protocols](../api/nuget-protocols.md).</span></span>

1. <span data-ttu-id="32bb0-126">Kolaylık olması için NuGet ile ilk API anahtarınıza kaydedin (bkz [bir paketi yayımlamaya](../create-packages/publish-a-package.md)nuget.org ve symbolsource.org için geçerli, symbolsource.org doğrulamak için nuget.org ile denetleyecek olduğundan paket sahibi değil.</span><span class="sxs-lookup"><span data-stu-id="32bb0-126">For convenience, first save your API key with NuGet (see [publish a package](../create-packages/publish-a-package.md), which will apply to both nuget.org and symbolsource.org, because symbolsource.org will check with nuget.org to verify that you are the package owner.</span></span>

    ```cli
    nuget SetApiKey Your-API-Key
    ```

2. <span data-ttu-id="32bb0-127">Birincil paketiniz için nuget.org yayımlandıktan sonra simge paketini aşağıdaki gibi otomatik olarak symbolsource.org nedeniyle hedefi olarak kullanacak anında `.symbols` dosya:</span><span class="sxs-lookup"><span data-stu-id="32bb0-127">After publishing your primary package to nuget.org, push the symbol package as follows, which will automatically use symbolsource.org as the target because of the `.symbols` in the filename:</span></span>

    ```cli
    nuget push MyPackage.symbols.nupkg
    ```

   > [!Note]
   > <span data-ttu-id="32bb0-128">Nuget.exe 4.5.0 veya üzeri, simgeler paketleri otomatik olarak symbolsource.org için gönderilen değil. Sonraki adımda açıklandığı gibi ayrı ayrı simgeleri paketleri göndermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="32bb0-128">With nuget.exe 4.5.0 or above, the symbols packages are not automatically pushed to symbolsource.org. You would need to push the symbols packages separately as explained in the next step.</span></span>

3. <span data-ttu-id="32bb0-129">Farklı simge depoya yayımlamak ya da adlandırma kuralı IU bir sembol paketi göndermek için kullanmak `-Source` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="32bb0-129">To publish to a different symbol repository, or to push a symbol package that doesn't follow the naming convention, use the `-Source` option:</span></span>

    ```cli
    nuget push MyPackage.symbols.nupkg -source https://nuget.smbsrc.net/
    ```

4. <span data-ttu-id="32bb0-130">Ayrıca, hem birincil hem de anında ve aşağıdakileri kullanarak aynı anda hem depoları paketlere simge:</span><span class="sxs-lookup"><span data-stu-id="32bb0-130">You can also push both primary and symbol packages to both repositories at the same time using the following:</span></span>

    ```cli
    nuget push MyPackage.nupkg
    ```

<span data-ttu-id="32bb0-131">Bu durumda, NuGet yayımlayacak `MyPackage.symbols.nupkg`, için varsa, https://nuget.smbsrc.net/ (gönderme URL'sini symbolsource.org), sonra nuget.org için birincil paketi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="32bb0-131">In this case, NuGet will publish `MyPackage.symbols.nupkg`, if present, to https://nuget.smbsrc.net/ (the push URL for symbolsource.org), after it publishes the primary package to nuget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="32bb0-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32bb0-132">See Also</span></span>

<span data-ttu-id="32bb0-133">[Yeni SymbolSource altyapısı taşıma](https://tripleemcoder.com/2015/10/04/moving-to-the-new-symbolsource-engine/) (symbolsource.org)</span><span class="sxs-lookup"><span data-stu-id="32bb0-133">[Moving to the new SymbolSource engine](https://tripleemcoder.com/2015/10/04/moving-to-the-new-symbolsource-engine/) (symbolsource.org)</span></span>