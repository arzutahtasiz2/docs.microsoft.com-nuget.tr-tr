1. <span data-ttu-id="8a426-101">[Nuget.org hesabınızda oturum](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) veya zaten yoksa, bir hesap oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a426-101">[Sign into your nuget.org account](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) or create an account if you don't have one already.</span></span>

1. <span data-ttu-id="8a426-102">Kullanıcı adınıza (sağ üstte) seçin ve ardından **API anahtarları**.</span><span class="sxs-lookup"><span data-stu-id="8a426-102">Select your user name (on the upper right), then select **API Keys**.</span></span>

1. <span data-ttu-id="8a426-103">Seçin **Oluştur**, anahtarınız için bir ad belirtin, seçin **kapsamları seçin > anında iletme**.</span><span class="sxs-lookup"><span data-stu-id="8a426-103">Select **Create**, provide a name for your key, select **Select Scopes > Push**.</span></span> <span data-ttu-id="8a426-104">Altında **API anahtarı**, girin \* için **Glob deseni**, ardından **Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="8a426-104">Under **API Key**, enter \* for **Glob pattern**, then select **Create**.</span></span> <span data-ttu-id="8a426-105">(Aşağıda kapsamları hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="8a426-105">(See below for more about scopes.)</span></span>

1. <span data-ttu-id="8a426-106">Anahtar oluşturulduktan sonra seçin **kopyalama** erişim almak için anahtar CLI'daki gerekir:</span><span class="sxs-lookup"><span data-stu-id="8a426-106">Once the key is created, select **Copy** to retrieve the access key you need in the CLI:</span></span>

    ![API anahtarını Panoya kopyalama](../media/QS_Create-02-APIKey.png)

1. <span data-ttu-id="8a426-108">**Önemli**: anahtar üzerinde yeniden daha sonra kopyalanamıyor çünkü anahtarınızı güvenli bir konuma kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8a426-108">**Important**: Save your key in a secure location because you cannot copy the key again later on.</span></span> <span data-ttu-id="8a426-109">API anahtarı sayfasına geri dönün, kopyalamak için anahtar gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a426-109">If you return to the API key page, you need to regenerate the key to copy it.</span></span> <span data-ttu-id="8a426-110">Artık paketler CLI göndermek istemiyorsanız, API anahtarı kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a426-110">You can also remove the API key if you no longer want to push packages via the CLI.</span></span>

<span data-ttu-id="8a426-111">Kapsam, farklı amaçlar için ayrı API anahtarları oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a426-111">Scoping allows you to create separate API keys for different purposes.</span></span> <span data-ttu-id="8a426-112">Her anahtar, sona erme zaman çerçevesi olan ve özel paketler (veya glob desenleri) ile sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a426-112">Each key has its expiration timeframe and can be scoped to specific packages (or glob patterns).</span></span> <span data-ttu-id="8a426-113">Her anahtar ayrıca belirli işlemler için kapsamlı: yeni paketleri ve güncelleştirmeler, yalnızca güncelleştirmelerini gönderimini veya delisting anında iletme.</span><span class="sxs-lookup"><span data-stu-id="8a426-113">Each key is also scoped to specific operations: push of new packages and updates, push of updates only, or delisting.</span></span> <span data-ttu-id="8a426-114">Kapsam aracılığıyla yalnızca ihtiyaç duydukları iznine sahip oldukları gibi kuruluşunuz için paketleri yöneten farklı kişiler için API anahtarları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a426-114">Through scoping, you can create API keys for different people who manage packages for your organization such that they have only the permissions they need.</span></span> <span data-ttu-id="8a426-115">Daha fazla bilgi için [Introducing kapsamlı API anahtarları](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) (blogs.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="8a426-115">For more information, see [Introducing scoped API keys](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) (blogs.nuget.org).</span></span>