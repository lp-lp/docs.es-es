### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="4d3b8-101">XmlSchemaException ahora establece correctamente las posiciones de las líneas</span><span class="sxs-lookup"><span data-stu-id="4d3b8-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4d3b8-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="4d3b8-102">Details</span></span>|<span data-ttu-id="4d3b8-103">Si el valor de <xref:System.Xml.Linq.LoadOptions.SetLineInfo> se pasa al método Load y se produce un error de validación, las propiedades <xref:System.Xml.Schema.XmlSchemaException.LineNumber> y <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contendrán ahora la información de línea.</span><span class="sxs-lookup"><span data-stu-id="4d3b8-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="4d3b8-104">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="4d3b8-104">Suggestion</span></span>|<span data-ttu-id="4d3b8-105">Se debe actualizar el código de control de excepciones que suponga que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> y <xref:System.Xml.Schema.XmlSchemaException.LinePosition> no se van a establecer, ya que ahora estas propiedades se establecerán correctamente al usar SetLineInfo durante la carga de XML.</span><span class="sxs-lookup"><span data-stu-id="4d3b8-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="4d3b8-106">Ámbito</span><span class="sxs-lookup"><span data-stu-id="4d3b8-106">Scope</span></span>|<span data-ttu-id="4d3b8-107">Borde</span><span class="sxs-lookup"><span data-stu-id="4d3b8-107">Edge</span></span>|
|<span data-ttu-id="4d3b8-108">Versión</span><span class="sxs-lookup"><span data-stu-id="4d3b8-108">Version</span></span>|<span data-ttu-id="4d3b8-109">4.5</span><span class="sxs-lookup"><span data-stu-id="4d3b8-109">4.5</span></span>|
|<span data-ttu-id="4d3b8-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="4d3b8-110">Type</span></span>|<span data-ttu-id="4d3b8-111">Tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="4d3b8-111">Runtime</span></span>|
|<span data-ttu-id="4d3b8-112">API afectadas</span><span class="sxs-lookup"><span data-stu-id="4d3b8-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
