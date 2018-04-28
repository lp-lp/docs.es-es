### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="9dc05-101">Se puede volver a usar RSACng y DSACng en escenarios de confianza parcial</span><span class="sxs-lookup"><span data-stu-id="9dc05-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9dc05-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="9dc05-102">Details</span></span>|<span data-ttu-id="9dc05-103">En algunos casos, CngLightup (que se usa en varias API de criptografía de nivel superior, como <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) y <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> se basan en la plena confianza.</span><span class="sxs-lookup"><span data-stu-id="9dc05-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="9dc05-104">Estos casos incluyen P/Invoke sin permisos <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> de aserción y rutas de código en las que <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> tiene peticiones de permiso para <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9dc05-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9dc05-105">A partir de .NET Framework 4.6.2, CngLightup se usaba para cambiar a <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> siempre que era posible.</span><span class="sxs-lookup"><span data-stu-id="9dc05-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="9dc05-106">Como resultado, las aplicaciones de confianza parcial que usaban <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> correctamente comenzaron a producir errores e iniciar <xref:System.Security.SecurityException> excepciones. Este cambio agrega las aserciones necesarias para que todas las funciones en las que se usa CngLightup tengan los permisos necesarios.</span><span class="sxs-lookup"><span data-stu-id="9dc05-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>|
|<span data-ttu-id="9dc05-107">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="9dc05-107">Suggestion</span></span>|<span data-ttu-id="9dc05-108">Si este cambio en .NET Framework 4.6.2 ha afectado negativamente a las aplicaciones de confianza parcial, actualice a .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9dc05-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>|
|<span data-ttu-id="9dc05-109">Ámbito</span><span class="sxs-lookup"><span data-stu-id="9dc05-109">Scope</span></span>|<span data-ttu-id="9dc05-110">Borde</span><span class="sxs-lookup"><span data-stu-id="9dc05-110">Edge</span></span>|
|<span data-ttu-id="9dc05-111">Versión</span><span class="sxs-lookup"><span data-stu-id="9dc05-111">Version</span></span>|<span data-ttu-id="9dc05-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="9dc05-112">4.6.2</span></span>|
|<span data-ttu-id="9dc05-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="9dc05-113">Type</span></span>|<span data-ttu-id="9dc05-114">Tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="9dc05-114">Runtime</span></span>|
|<span data-ttu-id="9dc05-115">API afectadas</span><span class="sxs-lookup"><span data-stu-id="9dc05-115">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
