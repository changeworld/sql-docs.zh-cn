---
title: "呈现和执行方法 |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c56c8b0a0fc4e2cb6f6bc78710e6fd4ed8e77cff
ms.contentlocale: zh-cn
ms.lasthandoff: 06/13/2017

---
# <a name="rendering-and-execution-methods"></a>呈现和执行方法
  可以使用这些方法来管理项执行和缓存以及报表呈现。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|使项的缓存无效。|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|返回项的缓存配置以及说明项的缓存副本何时到期的设置。|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|返回单个项的执行选项和相关设置。|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|返回支持的执行设置的列表。|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|处理指定报表并以指定格式呈现报表。|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|配置要缓存的项并提供指定项的缓存副本何时到期的设置。|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|为指定的项设置执行选项和相关的执行属性。|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|生成指定项的项执行快照。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 Web 服务和.NET Framework 构建应用程序](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [报表服务器 Web 服务](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [报表服务器 Web 服务方法](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [技术参考 &#40;SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  