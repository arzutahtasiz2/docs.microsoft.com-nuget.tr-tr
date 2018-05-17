---
title: NuGet Get-proje PowerShell başvurusu
description: Visual Studio'da NuGet Paket Yöneticisi konsolunda GetProject PowerShell komut başvurusu.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: a7b66cbf36095e31b5929596300018239749cb15
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="get-project-package-manager-console-in-visual-studio"></a><span data-ttu-id="d0743-103">Get-Project (Visual Studio'da Paket Yöneticisi Konsolu)</span><span class="sxs-lookup"><span data-stu-id="d0743-103">Get-Project (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="d0743-104">*Yalnızca içinde kullanılabilir [NuGet Paket Yöneticisi Konsolu](package-manager-console.md) Windows Visual Studio'da.*</span><span class="sxs-lookup"><span data-stu-id="d0743-104">*Available only within the [NuGet Package Manager Console](package-manager-console.md) in Visual Studio on Windows.*</span></span>

<span data-ttu-id="d0743-105">Varsayılan ya da belirtilen proje hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0743-105">Displays information about the default or specified project.</span></span> <span data-ttu-id="d0743-106">`Get-Project` özellikle bir tfs'deki projesi için Visual Studio DTE (geliştirme araçları ortamı) nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0743-106">`Get-Project` specifically returns a referent to the Visual Studio DTE (Development Tools Environment) object for the project.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0743-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0743-107">Syntax</span></span>

```ps
Get-Project [[-Name] <string>] [-All] [<CommonParameters>]
```

## <a name="parameters"></a><span data-ttu-id="d0743-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0743-108">Parameters</span></span>

| <span data-ttu-id="d0743-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="d0743-109">Parameter</span></span> | <span data-ttu-id="d0743-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0743-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d0743-111">Ad</span><span class="sxs-lookup"><span data-stu-id="d0743-111">Name</span></span> | <span data-ttu-id="d0743-112">Paket Yöneticisi Konsolu'nda seçili olan varsayılan projeyi varsayarak görüntülemek için projeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0743-112">Specifies the project to display, defaulting to the default project selected in the Package Manager Console.</span></span> <span data-ttu-id="d0743-113">-Name anahtarı kendisini isteğe bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="d0743-113">The -Name switch is itself optional.</span></span> |
| <span data-ttu-id="d0743-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="d0743-114">All</span></span> | <span data-ttu-id="d0743-115">Çözümdeki her projeye ilgili bilgileri görüntüler; projelerin sırası belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="d0743-115">Displays information for every project in the solution; the order of projects is not deterministic.</span></span> |

<span data-ttu-id="d0743-116">Hiçbiri bu parametre ardışık düzen giriş veya joker karakter kabul edin.</span><span class="sxs-lookup"><span data-stu-id="d0743-116">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="d0743-117">Ortak parametreleri</span><span class="sxs-lookup"><span data-stu-id="d0743-117">Common Parameters</span></span>

<span data-ttu-id="d0743-118">`Get-Project` Aşağıdaki destekleyen [ortak PowerShell parametrelerini](http://go.microsoft.com/fwlink/?LinkID=113216): hata ayıklama, hata eylemi, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, ayrıntı, WarningAction ve WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d0743-118">`Get-Project` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="d0743-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d0743-119">Examples</span></span>

```ps
# Displays information for the default project
Get-Project

# Displays information for a project in the solution
Get-Project MyProjectName

    # Displays information for all projects in the solution
Get-Project -All
```