---
title: Herstellen einer Verbindung mit Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, connections
ms.assetid: 73ee8171-3379-4384-bfc8-071b3eebbc8f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 569eb0eaea06b7b2f38caa0fc00682ab384c65cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698835"
---
# <a name="connect-to-analysis-services"></a><span data-ttu-id="b4498-102">Verbindung mit Analysis Services herstellen</span><span class="sxs-lookup"><span data-stu-id="b4498-102">Connect to Analysis Services</span></span>
  <span data-ttu-id="b4498-103">In diesem Abschnitt erfahren Sie etwas über Eigenschaften von Verbindungszeichenfolgen, Clientbibliotheken für Verbindungen, die von Analysis Services unterstützten Authentifizierungsmethoden sowie das Einrichten oder Löschen von Verbindungen, bevor ein Server offline geschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="b4498-103">Use the information in this section to learn about connection string properties, client libraries used for connections, which authentication methods are supported by Analysis Services, and how to set up or clear connections before taking a server offline.</span></span>  
  
## <a name="analysis-services-connections"></a><span data-ttu-id="b4498-104">Analysis Services-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="b4498-104">Analysis Services connections</span></span>  
 <span data-ttu-id="b4498-105">Analysis Services verwendet TCP als Netzwerkprotokoll und XML for Analysis (XMLA) als Kommunikationsprotokoll.</span><span class="sxs-lookup"><span data-stu-id="b4498-105">Analysis Services uses TCP as the network protocol and XML for Analysis (XMLA) as a communication protocol.</span></span> <span data-ttu-id="b4498-106">Auf der untersten Ebene wird von allen Clientbibliotheken, die mit Analysis Services bereitgestellt wurden, XMLA-over-TCP implementiert.</span><span class="sxs-lookup"><span data-stu-id="b4498-106">At the lowest level, all of the client libraries provided with Analysis Services implementing XMLA-over-TCP.</span></span> <span data-ttu-id="b4498-107">Obwohl es möglich ist, Anwendungen auf Grundlage der XMLA-Struktur zu erstellen, verwenden die meisten Anwendungen und Anwendungsentwickler Clientbibliotheken, um die Vorteile von Objektmodellen und die damit verbundene effiziente Codierung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="b4498-107">Although it is possible to build applications based on raw XMLA, most applications and application developers use client libraries to take advantage of the object models and coding efficiencies that they provide.</span></span> <span data-ttu-id="b4498-108">Für Clientverbindungen zu Analysis Services können Sie IIS als zwischengeschaltete Verbindung verwenden, wenn Sie TCP nicht über den Stapel hinweg verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b4498-108">For client connections to Analysis Services, you can use IIS as an intermediary connection if you cannot use TCP across the stack.</span></span> <span data-ttu-id="b4498-109">Ein Vorteil der Verwendung von HTTP-Zugriff über IIS ist die Möglichkeit, eine Verbindung von Anwendungen aus herzustellen, die Anmeldeinformationen in der Verbindungszeichenfolge übergeben.</span><span class="sxs-lookup"><span data-stu-id="b4498-109">One advantage of using HTTP access via IIS is the ability to connect from applications that pass credentials on the connection string.</span></span>  
  
 <span data-ttu-id="b4498-110">In Zusammenhang mit Konnektivität geht es immer auch um Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="b4498-110">Any discussion involving connectivity typically includes authentication.</span></span> <span data-ttu-id="b4498-111">Im Unterschied zu anderen SQL Server-Funktionen verwendet Analysis Services ausschließlich die Windows-Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="b4498-111">In contrast with other SQL Server features, Analysis Services uses Windows credentials exclusively.</span></span> <span data-ttu-id="b4498-112">Es ist nicht möglich, auf der Back-End-Verbindung mit Analysis Services die SQL Server-Datenbankauthentifizierung, die Forderungsauthentifizierung, die formularbasierte Authentifizierung oder Digest zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4498-112">You cannot use SQL Server database authentication, claims authentication, forms-based authentication, or digest on the backend connection to Analysis Services.</span></span> <span data-ttu-id="b4498-113">Weitere Informationen zur Authentifizierung finden Sie in diesem Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="b4498-113">More about authentication is provided in this section.</span></span>  
  
##  <a name="connection-tasks"></a><a name="bkmk_clientApps"></a> <span data-ttu-id="b4498-114">Verbindungsaufgaben</span><span class="sxs-lookup"><span data-stu-id="b4498-114">Connection Tasks</span></span>  
  
|<span data-ttu-id="b4498-115">Link</span><span class="sxs-lookup"><span data-stu-id="b4498-115">Link</span></span>|<span data-ttu-id="b4498-116">Taskbeschreibung</span><span class="sxs-lookup"><span data-stu-id="b4498-116">Task Description</span></span>|  
|----------|----------------------|  
|[<span data-ttu-id="b4498-117">Herstellen einer Verbindung von Clientanwendungen &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b4498-117">Connect from client applications &#40;Analysis Services&#41;</span></span>](connect-from-client-applications-analysis-services.md)|<span data-ttu-id="b4498-118">Wenn Sie mit Analysis Services nicht vertraut sind, lesen Sie dieses Thema, um sich einen Überblick über die Tools und Anwendungen zu verschaffen, die am häufigsten mit Analysis Services verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b4498-118">If you are new to Analysis Services, read this topic to get started with the tools and applications most often used with Analysis Services.</span></span>|  
|[<span data-ttu-id="b4498-119">Verbindungszeichenfolgen-Eigenschaften &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b4498-119">Connection String Properties &#40;Analysis Services&#41;</span></span>](connection-string-properties-analysis-services.md)|<span data-ttu-id="b4498-120">Analysis Services umfasst zahlreiche Server- und Datenbankeigenschaften, mit denen eine Verbindung unabhängig davon, wie die Instanz oder Datenbank konfiguriert ist, an spezifische Anwendungen angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4498-120">Analysis Services includes numerous server and database properties, allowing you to customize a connection for a specific application, independent of how the instance or database is configured.</span></span>|  
|[<span data-ttu-id="b4498-121">Von Analysis Services unterstützte Authentifizierungsmethoden</span><span class="sxs-lookup"><span data-stu-id="b4498-121">Authentication methodologies supported by Analysis Services</span></span>](authentication-methodologies-supported-by-analysis-services.md)|<span data-ttu-id="b4498-122">Dieses Thema gibt eine kurze Einführung in die Authentifizierungsmethoden, die von Analysis Services verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b4498-122">This topic is a brief introduction to the authentication methods used by Analysis Services.</span></span>|  
|[<span data-ttu-id="b4498-123">Konfigurieren von Analysis Services für die eingeschränkte Kerberos-Delegierung</span><span class="sxs-lookup"><span data-stu-id="b4498-123">Configure Analysis Services for Kerberos constrained delegation</span></span>](configure-analysis-services-for-kerberos-constrained-delegation.md)|<span data-ttu-id="b4498-124">Viele Business Intelligence-Lösungen setzen den Identitätswechsel voraus, um sicherzustellen, dass nur berechtigte Daten an die einzelnen Benutzer zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b4498-124">Many business intelligence solutions require impersonation to ensure that only authorized data is returned to each user.</span></span> <span data-ttu-id="b4498-125">In diesem Thema werden die Voraussetzungen für die Verwendung des Identitätswechsels beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b4498-125">In this topic, learn the requirements for using impersonation.</span></span> <span data-ttu-id="b4498-126">In diesem Thema werden außerdem die Schritte zum Konfigurieren von Analysis Services für die eingeschränkte Kerberos-Delegierung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b4498-126">This topic also explains the steps for configuring Analysis Services for Kerberos constrained delegation.</span></span>|  
|[<span data-ttu-id="b4498-127">SPN-Registrierung für eine Analysis Services-Instanz</span><span class="sxs-lookup"><span data-stu-id="b4498-127">SPN registration for an Analysis Services instance</span></span>](spn-registration-for-an-analysis-services-instance.md)|<span data-ttu-id="b4498-128">Die Kerberos-Authentifizierung setzt einen gültigen Dienstprinzipalnamen (Service Principal Name, SPN) für Dienste voraus, durch die die Identität eines Benutzers in einer Multiserverlösung angenommen oder delegiert wird.</span><span class="sxs-lookup"><span data-stu-id="b4498-128">Kerberos authentication requires a valid Service Principle Name (SPN) for services that impersonate or delegate user identities in multi-server solutions.</span></span> <span data-ttu-id="b4498-129">Verwenden Sie die Informationen in diesem Thema, um mehr darüber zu erfahren, wie Sie die SPN-Registrierung für Analysis Services erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="b4498-129">Use the information in this topic to learn the construction and steps for SPN registration for Analysis Services.</span></span>|  
|[<span data-ttu-id="b4498-130">Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0</span><span class="sxs-lookup"><span data-stu-id="b4498-130">Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0</span></span>](configure-http-access-to-analysis-services-on-iis-8-0.md)|<span data-ttu-id="b4498-131">Standardauthentifizierung oder domänenübergreifende Nutzung sind zwei wichtige Gründe, um Analysis Services für den HTTP-Zugriff zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b4498-131">Basic authentication or cross-domain boundaries are two important reasons for configuring Analysis Services for HTTP access.</span></span>|  
|[<span data-ttu-id="b4498-132">Für Analysis Services-Verbindungen verwendete Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="b4498-132">Data providers used for Analysis Services connections</span></span>](data-providers-used-for-analysis-services-connections.md)|<span data-ttu-id="b4498-133">Analysis Services stellt drei Clientbibliotheken für den Zugriff auf Servervorgänge oder Analysis Services-Daten bereit.</span><span class="sxs-lookup"><span data-stu-id="b4498-133">Analysis Services provides three client libraries for accessing server operations or Analysis Services data.</span></span> <span data-ttu-id="b4498-134">Dieses Thema enthält eine kurze Einführung zu ADOMD.NET, AMOs (Analysis Services Management Objects) und dem OLE DB-Anbieter für Analysis Services (MSOLAP).</span><span class="sxs-lookup"><span data-stu-id="b4498-134">This topic offers a brief introduction to ADOMD.NET, Analysis Services Management Objects (AMO), and the Analysis Services OLE DB provider (MSOLAP).</span></span>|  
|[<span data-ttu-id="b4498-135">Trennen von Benutzern und Sitzungen auf Analysis Services-Server</span><span class="sxs-lookup"><span data-stu-id="b4498-135">Disconnect Users and Sessions on Analysis Services Server</span></span>](disconnect-users-and-sessions-on-analysis-services-server.md)|<span data-ttu-id="b4498-136">Löschen Sie vorhandene Verbindungen und Sitzungen, bevor Sie einen Server offline schalten oder Baseline-Leistungstests durchführen.</span><span class="sxs-lookup"><span data-stu-id="b4498-136">Clear existing connections and sessions before taking a server offline or conducting baseline performance tests.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4498-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b4498-137">See Also</span></span>  
 <span data-ttu-id="b4498-138">[Konfigurations &#40;Analysis Services nach der Installation&#41;](post-install-configuration-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b4498-138">[Post-install Configuration &#40;Analysis Services&#41;](post-install-configuration-analysis-services.md) </span></span>  
 <span data-ttu-id="b4498-139">[Konfigurieren von Server Eigenschaften in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b4498-139">[Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="b4498-140">Skriptverwaltungsaufgaben in Analysis Services</span><span class="sxs-lookup"><span data-stu-id="b4498-140">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  