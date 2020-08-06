---
title: Erstellen einer Datentyp Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time dimensions [Analysis Services]
- dimensions [Analysis Services], time
- adding time intelligence
- server time dimensions [Analysis Services]
- calendars [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: 6d692856-4b01-4dca-a650-f97ac220c114
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e16d38f438b3f319e1c9a87b147269dcd1a8a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698685"
---
# <a name="create-a-date-type-dimension"></a><span data-ttu-id="cc697-102">Erstellen einer Datumstypdimension</span><span class="sxs-lookup"><span data-stu-id="cc697-102">Create a Date type Dimension</span></span>
  <span data-ttu-id="cc697-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist eine Zeitdimension ein Dimensionstyp, dessen Attribute Zeiträume darstellen, z. b. Jahre, Semester, Quartale, Monate und Tage.</span><span class="sxs-lookup"><span data-stu-id="cc697-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a time dimension is a dimension type whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span> <span data-ttu-id="cc697-104">Die in einer Zeitdimension enthaltenen Zeiträume stellen zeitbasierte Granularitätsebenen für Analysen und Berichte bereit.</span><span class="sxs-lookup"><span data-stu-id="cc697-104">The periods in a time dimension provide time-based levels of granularity for analysis and reporting.</span></span> <span data-ttu-id="cc697-105">Die Attribute sind in Hierarchien organisiert, und die Granularität der Zeitdimension wird weitgehend durch die Anforderungen des Geschäfts und des Berichtswesens an historische Daten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="cc697-105">The attributes are organized in hierarchies, and the granularity of the time dimension is determined largely by the business and reporting requirements for historical data.</span></span> <span data-ttu-id="cc697-106">So verwenden beispielsweise die meisten Finanz- und Verkaufsdaten in Business Intelligence-Anwendungen eine monatliche oder quartalsweise Granularität.</span><span class="sxs-lookup"><span data-stu-id="cc697-106">For example, most financial and sales data in business intelligence applications use a monthly or quarterly granularity.</span></span>  
  
 <span data-ttu-id="cc697-107">In der Regel beeinhalten Cubes in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Zeitdimension in irgendeiner Form.</span><span class="sxs-lookup"><span data-stu-id="cc697-107">Typically, cubes in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] incorporate a time dimension in one form or another.</span></span> <span data-ttu-id="cc697-108">Ein Cube kann mehrere Zeitdimensionen oder mehrere Hierarchien derselben Zeitdimension enthalten. Diese hängen von der Granularität der Daten und den Berichtsanforderungen ab.</span><span class="sxs-lookup"><span data-stu-id="cc697-108">A cube may include more than one time dimension, or several hierarchies from the same time dimension, depending on the granularity of the data and the reporting requirements.</span></span> <span data-ttu-id="cc697-109">Es benötigen jedoch nicht alle Cubes eine Zeitdimension.</span><span class="sxs-lookup"><span data-stu-id="cc697-109">However, not all cubes require a time dimension.</span></span> <span data-ttu-id="cc697-110">Manche OLAP-Anwendungen, wie z. B. eine aktivitätsbasierte Kostenrechnung, benötigen keine Zeitdimension, weil die Kostenrechnung in einer aktivitätsbasierten Dimension auf einer Aktivität und nicht auf Zeit basiert.</span><span class="sxs-lookup"><span data-stu-id="cc697-110">Some OLAP applications, such as activity-based costing, do not require a time dimension, because .costing in an activity-based dimension is based on activity instead of time.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="cc697-111">Dimensionsstruktur</span><span class="sxs-lookup"><span data-stu-id="cc697-111">Dimension Structure</span></span>  
 <span data-ttu-id="cc697-112">Die Dimensionsstruktur für eine Zeitdimension hängt davon ab, wie die zugrunde liegende Datenquelle die Zeitraumangaben speichert.</span><span class="sxs-lookup"><span data-stu-id="cc697-112">The dimension structure for a time dimension depends on how the underlying data source stores the time period information.</span></span> <span data-ttu-id="cc697-113">Aus diesem Unterschied beim Speichern ergeben sich zwei Basistypen von Zeitdimensionen:</span><span class="sxs-lookup"><span data-stu-id="cc697-113">This difference in storage produces two basic types of time dimensions:</span></span>  
  
 <span data-ttu-id="cc697-114">Zeitdimension</span><span class="sxs-lookup"><span data-stu-id="cc697-114">Time dimension</span></span>  
 <span data-ttu-id="cc697-115">Zeitdimensionen sind mit anderen Dimensionen vergleichbar, da die Dimensionstabelle die Attribute für die Dimension liefert.</span><span class="sxs-lookup"><span data-stu-id="cc697-115">Time dimensions are similar to other dimensions in that a dimension table supplies the attributes for the dimension.</span></span> <span data-ttu-id="cc697-116">Jede Spalte der Dimensionshaupttabelle definiert ein Attribut für einen bestimmten Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="cc697-116">Each column in the dimension main table defines an attribute for a specific time period.</span></span>  
  
 <span data-ttu-id="cc697-117">Wie bei anderen Dimensionen hat die Faktentabelle eine Fremdschlüsselbeziehung mit der Dimensionstabelle für die Zeitdimension.</span><span class="sxs-lookup"><span data-stu-id="cc697-117">Like other dimensions, the fact table has a foreign key relationship to the dimension table for the time dimension.</span></span> <span data-ttu-id="cc697-118">Das Schlüsselattribut für eine Zeitdimension basiert entweder auf einem Ganzzahlschlüssel, oder auf der niedrigsten Detailebene, wie dem Datum, das in der Dimensionshaupttabelle enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="cc697-118">The key attribute for a time dimension is based either on an integer key or on the lowest level of detail, such as the date, that appears in the dimension main table.</span></span>  
  
 <span data-ttu-id="cc697-119">Serverzeitdimension</span><span class="sxs-lookup"><span data-stu-id="cc697-119">Server time dimension</span></span>  
 <span data-ttu-id="cc697-120">Wenn Sie über keine Dimensionstabelle verfügen, um zeitgestützte Attribute daran zu binden, können Sie durch [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine auf Zeiträumen basierende Serverzeitdimension definieren lassen.</span><span class="sxs-lookup"><span data-stu-id="cc697-120">If you do not have a dimension table to which to bind time-related attributes, you can have [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] define a server time dimension based on time periods.</span></span> <span data-ttu-id="cc697-121">Um die von einer Serverzeitdimension dargestellten Hierarchien, Ebenen und Elemente zu definieren, wählen Sie beim Erstellen der Dimension Standardzeiträume aus.</span><span class="sxs-lookup"><span data-stu-id="cc697-121">To define the hierarchies, levels, and members represented by the server time dimension, you select standard time periods when you create the dimension.</span></span>  
  
 <span data-ttu-id="cc697-122">Attribute in einer Serverzeitdimension verfügen über bestimmte Zeitattributbindungen.</span><span class="sxs-lookup"><span data-stu-id="cc697-122">Attributes in a server time dimension have a special time-attribute binding.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="cc697-123">verwendet die zu Daten gehörigen Attributtypen, z. B. Jahr, Monat oder Tag, um Elemente von Attributen in einer Zeitdimension zu definieren.</span><span class="sxs-lookup"><span data-stu-id="cc697-123">uses the attribute types that are related to dates, such as Year, Month, or Day, to define members of attributes in a time dimension.</span></span>  
  
 <span data-ttu-id="cc697-124">Nachdem Sie die Serverzeitdimension in einen Cube aufgenommen haben, legen Sie die Beziehung zwischen der Measuregruppe und der Serverzeitdimension fest, indem Sie die Beziehung auf der Seite **Dimensionsverwendung definieren** des Cube-Assistenten angeben.</span><span class="sxs-lookup"><span data-stu-id="cc697-124">After you include the server time dimension in a cube, you set the relationship between the measure group and the server time dimension by specifying a relationship on the **Define Dimension Usage** page of the Cube Wizard.</span></span>  
  
### <a name="calendars"></a><span data-ttu-id="cc697-125">Kalender</span><span class="sxs-lookup"><span data-stu-id="cc697-125">Calendars</span></span>  
 <span data-ttu-id="cc697-126">In einer Zeitdimension oder einer Serverzeitdimension werden die Zeitraumattribute in Hierarchien miteinander gruppiert.</span><span class="sxs-lookup"><span data-stu-id="cc697-126">In a time dimension or server time dimension time period attributes are grouped together in hierarchies.</span></span> <span data-ttu-id="cc697-127">Diese Hierarchien werden im Allgemeinen als Kalender bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="cc697-127">Such hierarchies are generally referred to as calendars.</span></span>  
  
 <span data-ttu-id="cc697-128">Business Intelligence-Anwendungen benötigen oft mehrere Kalenderdefinitionen.</span><span class="sxs-lookup"><span data-stu-id="cc697-128">Business intelligence applications frequently require multiple calendar definitions.</span></span> <span data-ttu-id="cc697-129">Beispielsweise kann eine Personalabteilung Mitarbeiter nachverfolgen, indem Sie einen *Standard* Kalender verwendet: einen zwölfmonatigen gregorianischen Kalender, der am 1. Januar beginnt und am 31. Dezember endet.</span><span class="sxs-lookup"><span data-stu-id="cc697-129">For example, a human resource department may track employees by using a *standard* calendar-a twelve-month Gregorian calendar starting on January 1 and ending on December 31st.</span></span> <span data-ttu-id="cc697-130">Dieselbe Personalabteilung kann jedoch Ausgaben mithilfe eines *Geschäfts* Kalenders nachverfolgen, einem zwölfmonatigen Kalender, der das von der Organisation verwendete Geschäftsjahr definiert.</span><span class="sxs-lookup"><span data-stu-id="cc697-130">However, that same human resource department may track expenditures by using a *fiscal* calendar-a twelve-month calendar that defines the fiscal year used by the organization.</span></span>  
  
 <span data-ttu-id="cc697-131">Diese verschiedenen Kalender können Sie manuell im Dimensions-Designer erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-131">You can construct these different calendars manually in Dimension Designer.</span></span> <span data-ttu-id="cc697-132">Der Dimensions-Assistent stellt jedoch verschiedene Hierarchievorlagen bereit, mit denen Sie automatisch verschiedene Kalendertypen generieren können, wenn Sie eine Zeitdimension oder eine Serverzeitdimension erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-132">However, the Dimension Wizard provides several hierarchy templates that can be used to automatically generate several types of calendars when you create a time dimension or server time dimension.</span></span> <span data-ttu-id="cc697-133">Die folgende Tabelle beschreibt die verschiedenen Kalender, die mit dem Dimensions-Assistenten generiert werden können.</span><span class="sxs-lookup"><span data-stu-id="cc697-133">The following table describes the various calendars that can be generated by the Dimension Wizard.</span></span>  
  
|<span data-ttu-id="cc697-134">Kalender</span><span class="sxs-lookup"><span data-stu-id="cc697-134">Calendar</span></span>|<span data-ttu-id="cc697-135">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="cc697-135">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="cc697-136">Standardkalender</span><span class="sxs-lookup"><span data-stu-id="cc697-136">Standard calendar</span></span>|<span data-ttu-id="cc697-137">Ein zwölfmonatiger gregorianischer Kalender, der am 1. Januar beginnt und am 31. Dezember endet.</span><span class="sxs-lookup"><span data-stu-id="cc697-137">A twelve-month Gregorian calendar starting on January 1 and ending on December 31st.</span></span><br /><br /> <span data-ttu-id="cc697-138">Unabhängig davon, ob Sie mit dem Dimensions-Assistenten eine Zeitdimension oder eine Serverzeitdimension erstellen, generiert der Assistent eine Hierarchie für einen Standardkalender, nachdem Sie die Attribute definiert haben, die die Zeiträume der Dimension darstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-138">Regardless of whether you use the Dimension Wizard to create a time dimension or a server time dimension, the wizard generates a hierarchy for a standard calendar after you define the attributes that represent the time periods for the dimension.</span></span> <span data-ttu-id="cc697-139">Wenn Sie mit dem Dimensions-Assistenten eine Serverzeitdimension erstellen, können Sie das Anfangsdatum des Standardkalenders auf einen anderen Tag als den 1. Januar legen.</span><span class="sxs-lookup"><span data-stu-id="cc697-139">If you use the Dimension Wizard to create a server time dimension, you can adjust the starting date of the standard calendar to start on a day other than January 1.</span></span>|  
|<span data-ttu-id="cc697-140">Geschäftskalender</span><span class="sxs-lookup"><span data-stu-id="cc697-140">Fiscal calendar</span></span>|<span data-ttu-id="cc697-141">Ein zwölfmonatiger Geschäftskalender.</span><span class="sxs-lookup"><span data-stu-id="cc697-141">A twelve-month fiscal calendar.</span></span> <span data-ttu-id="cc697-142">Wenn Sie diesen Kalender auswählen, müssen Sie den Anfangstag des vom Unternehmen verwendeten Geschäftsjahres angeben.</span><span class="sxs-lookup"><span data-stu-id="cc697-142">When you select this calendar, specify the starting day and month for the fiscal year used by your organization.</span></span><br /><br /> <span data-ttu-id="cc697-143">Hinweis: Dieser Kalender ist nur verfügbar, wenn Sie mit dem Dimensions-Assistenten eine Serverzeitdimension erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-143">Note: This calendar is only available if you use the Dimension Wizard to create a server time dimension.</span></span>|  
|<span data-ttu-id="cc697-144">Berichtskalender (oder Marketingkalender)</span><span class="sxs-lookup"><span data-stu-id="cc697-144">Reporting calendar (or marketing calendar)</span></span>|<span data-ttu-id="cc697-145">Ein zwölfmonatiger Berichtskalender, der in einem dreimonatigen (quartalsweisen) Muster zwei Monate mit vier und einen Monat mit fünf Wochen enthält.</span><span class="sxs-lookup"><span data-stu-id="cc697-145">A twelve-month reporting calendar that includes two months of four weeks and one month of five weeks in a repeated three-month (quarterly) pattern.</span></span> <span data-ttu-id="cc697-146">Wenn Sie diesen Kalender auswählen, geben Sie den Starttag und-Monat sowie das dreimonatige Muster 4-4-5, 4-5-4 oder 5-4-4 Wochen an, wobei jede Ziffer die Anzahl der Wochen in einem Monat darstellt.</span><span class="sxs-lookup"><span data-stu-id="cc697-146">When you select this calendar, specify the starting day and month and the three-month pattern of 4-4-5, 4-5-4, or 5-4-4 weeks, where each digit represents the number of weeks in a month.</span></span><br /><br /> <span data-ttu-id="cc697-147">Hinweis: Dieser Kalender ist nur verfügbar, wenn Sie mit dem Dimensions-Assistenten eine Serverzeitdimension erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-147">Note: This calendar is only available if you use the Dimension Wizard to create a server time dimension.</span></span>|  
|<span data-ttu-id="cc697-148">Produktionskalender</span><span class="sxs-lookup"><span data-stu-id="cc697-148">Manufacturing calendar</span></span>|<span data-ttu-id="cc697-149">Ein Kalender, der 13 aus vier Wochen bestehende Perioden verwendet, die in drei Quartale mit drei Perioden und ein Quartal mit vier Perioden unterteilt sind.</span><span class="sxs-lookup"><span data-stu-id="cc697-149">A calendar that uses 13 periods of four weeks, divided into three quarters of three periods and one quarter of four periods.</span></span> <span data-ttu-id="cc697-150">Wenn Sie diesen Kalender auswählen, müssen Sie die Anfangswoche (zwischen 1 und 4) und den Anfangsmonat des von Ihrem Unternehmen verwendeten Produktionsjahres angeben und festlegen, welches Quartal vier Perioden enthält.</span><span class="sxs-lookup"><span data-stu-id="cc697-150">When you select this calendar, you specify the starting week (between 1 and 4) and month for the manufacturing year used by your organization, and also identify which quarter contains four periods.</span></span><br /><br /> <span data-ttu-id="cc697-151">Hinweis: Dieser Kalender ist nur verfügbar, wenn Sie mit dem Dimensions-Assistenten eine Serverzeitdimension erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-151">Note: This calendar is only available if you use the Dimension Wizard to create a server time dimension.</span></span>|  
|<span data-ttu-id="cc697-152">ISO 8601-Kalender</span><span class="sxs-lookup"><span data-stu-id="cc697-152">ISO 8601 Calendar</span></span>|<span data-ttu-id="cc697-153">Der Standardkalender für die Daten- und Zeitdarstellung (8601) der Internationalen Organisation für Normung (International Organization for Standardization, ISO).</span><span class="sxs-lookup"><span data-stu-id="cc697-153">The International Organization for Standardization (ISO) Representation of Dates and Time standard calendar (8601).</span></span> <span data-ttu-id="cc697-154">Dieser Kalender besitzt eine integrale Anzahl von 7-Tage-Wochen.</span><span class="sxs-lookup"><span data-stu-id="cc697-154">This calendar has an integral number of 7-day weeks.</span></span> <span data-ttu-id="cc697-155">Das neue Jahr kann mehrere Wochen vor oder nach dem Beginn des neuen Jahres auf der Basis des gregorianischen Kalenders anfangen.</span><span class="sxs-lookup"><span data-stu-id="cc697-155">The new year may start several days before or after the start of the new year, based on the Gregorian calendar.</span></span> <span data-ttu-id="cc697-156">Die erste Woche dieses Kalenders wird durch die erste Woche des gregorianischen Kalenders bestimmt, die einen Donnerstag enthält.</span><span class="sxs-lookup"><span data-stu-id="cc697-156">The first week of this calendar is determined by the first week of the Gregorian calendar which contains a Thursday.</span></span> <span data-ttu-id="cc697-157">Aus diesem Grund kann es sein, dass der erste Tag dieser Woche – der Sonntag – noch im Vorjahr liegt.</span><span class="sxs-lookup"><span data-stu-id="cc697-157">Therefore, the first day of this week, the Sunday, may actually fall within the previous year.</span></span><br /><br /> <span data-ttu-id="cc697-158">Hinweis: Dieser Kalender ist nur verfügbar, wenn Sie mit dem Dimensions-Assistenten eine Serverzeitdimension erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc697-158">Note: This calendar is only available if you use the Dimension Wizard to create a server time dimension.</span></span>|  
  
 <span data-ttu-id="cc697-159">Wenn Sie eine Serverzeitdimension erstellen und die Zeiträume und Kalender angeben, die in der Dimension verwendet werden sollen, fügt der Dimensions-Assistent die jeweils für die angegebenen Kalender geeigneten Attribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc697-159">When you create a server time dimension, and specify the time periods and the calendars to use in that dimension, the Dimension Wizard adds the attributes for the time periods that are appropriate for each specified calendar.</span></span> <span data-ttu-id="cc697-160">Wenn Sie z. B. eine Serverzeitdimension erstellen, die als Zeitraum "Jahre" verwendet und sowohl Geschäfts- als auch Berichtskalender enthält, fügt der Assistent dann der Dimension die Attribute FiscalYear und ReportingYear sowie das Standardattribut Years hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc697-160">For example, if you create a server time dimension that uses years as the time period and includes both fiscal and reporting calendars, the wizard will then add FiscalYear and ReportingYears attributes, together with the standard Years attribute, to the dimension.</span></span> <span data-ttu-id="cc697-161">Eine Serverzeitdimension besitzt außerdem Attribute für Kombinationen ausgewählter Zeiträume, wie das Attribut DayOfWeek für eine Dimension, die Days und Weeks enthält.</span><span class="sxs-lookup"><span data-stu-id="cc697-161">A server time dimension will also have attributes for combinations of selected time periods, such as a DayOfWeek attribute for a dimension that contains Days and Weeks.</span></span> <span data-ttu-id="cc697-162">Der Dimensions-Assistent erstellt eine Kalenderhierarchie, indem er Attribute kombiniert, die zu einem einzelnen Kalendertyp gehören.</span><span class="sxs-lookup"><span data-stu-id="cc697-162">The Dimension Wizard creates a calendar hierarchy by combining attributes that belong to a single calendar type.</span></span> <span data-ttu-id="cc697-163">Eine Finanzkalenderhierarchie kann die folgenden Ebenen enthalten: Geschäftsjahr, Geschäftshalbjahr, Geschäftsquartal, Geschäftsmonat und Geschäftstag.</span><span class="sxs-lookup"><span data-stu-id="cc697-163">For example, a fiscal calendar hierarchy may contain the following levels: Fiscal Year, Fiscal Half Year, Fiscal Quarter, Fiscal Month, and Fiscal Day.</span></span>  
  
## <a name="adding-time-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="cc697-164">Hinzufügen von Zeitintelligenz mit dem Business Intelligence-Assistenten</span><span class="sxs-lookup"><span data-stu-id="cc697-164">Adding Time Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="cc697-165">Nachdem Sie eine Zeitdimension definiert und diese Dimension einem Cube hinzugefügt haben, können Sie mit dem Business Intelligence-Assistenten eine Zeitintelligenzfunktion hinzufügen, wie Vergleiche zwischen Zeitraum und Datum, Zeitraum und Zeitraum und Measures für einen gleitenden Durchschnitt.</span><span class="sxs-lookup"><span data-stu-id="cc697-165">After you have defined a time dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add time intelligence functionality, such as period-to-date, period-to-period, and rolling average measures.</span></span> <span data-ttu-id="cc697-166">Weitere Informationen finden Sie unter [Definieren von Zeitintelligenzberechnungen mithilfe des Business Intelligence-Assistenten](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="cc697-166">For more information, see [Define Time Intelligence Calculations using the Business Intelligence Wizard](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc697-167">Mit dem Business Intelligence-Assistenten können Sie keine Zeitintelligenz zu Serverzeitdimensionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cc697-167">You cannot use the Business Intelligence Wizard to add time intelligence to server time dimensions.</span></span> <span data-ttu-id="cc697-168">Der Business Intelligence-Assistent fügt eine Hierarchie für die Unterstützung der Zeitintelligenz hinzu. Diese Hierarchie muss mit einer Spalte der Zeitdimensionstabelle verbunden werden.</span><span class="sxs-lookup"><span data-stu-id="cc697-168">The Business Intelligence Wizard adds a hierarchy to support time intelligence, and this hierarchy must be bound to a column of the time dimension table.</span></span> <span data-ttu-id="cc697-169">Serverzeitdimensionen besitzen keine zugehörige Zeitdimensionstabelle und können diese zusätzliche Hierarchie daher nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="cc697-169">Server time dimensions do not have a corresponding time dimension table and therefore cannot support this additional hierarchy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc697-170">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cc697-170">See Also</span></span>  
 <span data-ttu-id="cc697-171">[Erstellen einer Zeit Dimension durch das Erzeugen einer Zeittabelle](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="cc697-171">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 <span data-ttu-id="cc697-172">[Business Intelligence Wizard (F1-Hilfe)](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="cc697-172">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="cc697-173">Dimensionstypen</span><span class="sxs-lookup"><span data-stu-id="cc697-173">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  