---
title: 'ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56b19a138dc95b94a20183909dd444c90b158b26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616901"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="2368b-102">ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="2368b-102">ListSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="2368b-103">Gibt eine Liste von auf dem Computer installierten SSL-Zertifikaten zurück</span><span class="sxs-lookup"><span data-stu-id="2368b-103">Returns a list of installed SSL certificates on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2368b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2368b-104">Syntax</span></span>  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2368b-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="2368b-105">Parameters</span></span>  
 <span data-ttu-id="2368b-106">*LCID*</span><span class="sxs-lookup"><span data-stu-id="2368b-106">*LCID*</span></span>  
 <span data-ttu-id="2368b-107">Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll</span><span class="sxs-lookup"><span data-stu-id="2368b-107">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="2368b-108">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="2368b-108">*Application[]*</span></span>  
 <span data-ttu-id="2368b-109">[out] Die Anwendungen, die Zertifikatsbindungen aufweisen</span><span class="sxs-lookup"><span data-stu-id="2368b-109">[out] The applications that have certificate bindings.</span></span>  
  
 <span data-ttu-id="2368b-110">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="2368b-110">*CertificateHash[]*</span></span>  
 <span data-ttu-id="2368b-111">[out] Die Hashes für die Zertifikate</span><span class="sxs-lookup"><span data-stu-id="2368b-111">[out] The hashes for the certificates.</span></span>  
  
 <span data-ttu-id="2368b-112">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="2368b-112">*IPAddress[]*</span></span>  
 <span data-ttu-id="2368b-113">[out] Die IP-Adresse für die Anwendungen</span><span class="sxs-lookup"><span data-stu-id="2368b-113">[out] The IP address for the applications.</span></span>  
  
 <span data-ttu-id="2368b-114">*Port[]*</span><span class="sxs-lookup"><span data-stu-id="2368b-114">*Port[]*</span></span>  
 <span data-ttu-id="2368b-115">[out] Die in der Bindung in rsreportserver.config gespeicherte Portnummer.</span><span class="sxs-lookup"><span data-stu-id="2368b-115">[out] The port number stored in the binding in rsreportserver.config.</span></span>  
  
 <span data-ttu-id="2368b-116">*Errors[]*</span><span class="sxs-lookup"><span data-stu-id="2368b-116">*Errors[]*</span></span>  
 <span data-ttu-id="2368b-117">[out] Die Beschreibungen für Fehler, die aufgetreten sind</span><span class="sxs-lookup"><span data-stu-id="2368b-117">[out] The descriptions for errors that occurred.</span></span>  
  
 <span data-ttu-id="2368b-118">*Länge*</span><span class="sxs-lookup"><span data-stu-id="2368b-118">*Length*</span></span>  
 <span data-ttu-id="2368b-119">[out] Die Länge des von der Methode zurückgegebenen Arrays</span><span class="sxs-lookup"><span data-stu-id="2368b-119">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="2368b-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="2368b-120">*HRESULT*</span></span>  
 <span data-ttu-id="2368b-121">[out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.</span><span class="sxs-lookup"><span data-stu-id="2368b-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2368b-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="2368b-122">Return Value</span></span>  
 <span data-ttu-id="2368b-123">Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2368b-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="2368b-124">Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="2368b-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="2368b-125">Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="2368b-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2368b-126">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="2368b-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2368b-127">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="2368b-127">Requirements</span></span>  
 <span data-ttu-id="2368b-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2368b-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2368b-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2368b-129">See Also</span></span>  
 [<span data-ttu-id="2368b-130">MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)</span><span class="sxs-lookup"><span data-stu-id="2368b-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  