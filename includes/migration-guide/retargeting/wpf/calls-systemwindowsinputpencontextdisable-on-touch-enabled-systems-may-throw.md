### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="c513a-101">Las llamadas a System.Windows.Input.PenContext.Disable en sistemas táctiles pueden iniciar una excepción ArgumentException</span><span class="sxs-lookup"><span data-stu-id="c513a-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c513a-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="c513a-102">Details</span></span>|<span data-ttu-id="c513a-103">En algunas circunstancias, las llamadas al método interno <strong>System.Windows.Intput.PenContext.Disable</strong> en sistemas táctiles pueden iniciar una excepción <code>T:System.ArgumentException</code> no controlada debido a la reentrada.</span><span class="sxs-lookup"><span data-stu-id="c513a-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="c513a-104">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="c513a-104">Suggestion</span></span>|<span data-ttu-id="c513a-105">Este problema se ha corregido en .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="c513a-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="c513a-106">Para evitar la excepción, actualice a una versión de .NET Framework a partir de .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="c513a-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="c513a-107">Ámbito</span><span class="sxs-lookup"><span data-stu-id="c513a-107">Scope</span></span>|<span data-ttu-id="c513a-108">Borde</span><span class="sxs-lookup"><span data-stu-id="c513a-108">Edge</span></span>|
|<span data-ttu-id="c513a-109">Versión</span><span class="sxs-lookup"><span data-stu-id="c513a-109">Version</span></span>|<span data-ttu-id="c513a-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c513a-110">4.6.1</span></span>|
|<span data-ttu-id="c513a-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="c513a-111">Type</span></span>|<span data-ttu-id="c513a-112">Redestinación</span><span class="sxs-lookup"><span data-stu-id="c513a-112">Retargeting</span></span>|
