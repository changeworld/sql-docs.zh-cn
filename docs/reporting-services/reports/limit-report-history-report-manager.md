---
title: 限制报表历史记录（报表管理器）| Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c8a6664802c9e0d893ae0e8c85a956fa4b324ddc
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021881"
---
# <a name="limit-report-history-report-manager"></a>限制报表历史记录（报表管理器）
  报表历史记录是随着时间变化而创建的报表快照的集合。 您可以按需创建报表历史记录，也可以安排快照的创建频率以及将快照添加到报表历史记录中的频率。  
  
 报表历史记录存储在报表服务器数据库中。 如果报表快照中包含大量数据，则可以考虑限制报表历史记录，以便尽可能减少快照保持期对数据库大小的影响。  
  
### <a name="to-configure-report-history-for-a-report-server"></a>为报表服务器配置报表历史记录  
  
1.  在报表管理器中，单击全局工具栏上的 **“站点设置”** 。  
  
2.  如果希望无限制地保留所有报表历史记录，请选择 **“不限制报表历史记录中保留的快照数”** 。 否则，请选择 **“限制报表历史记录的副本数”** ，以指定可以为任何给定报表保留的最多快照数。  
  
3.  单击 **“应用”**。  
  
### <a name="to-configure-report-history-for-a-specific-report"></a>为特定的报表配置报表历史记录  
  
1.  在报表管理器中，导航到要配置历史记录的报表，再单击该报表将其打开。  
  
2.  单击 **“属性”** 选项卡。  
  
3.  单击 **“历史记录”** 选项卡。  
  
4.  为您的报表选择相应选项，再单击 **“应用”**。 有关每个选项的详细信息，请参阅[“快照选项”属性页（报表管理器）](https://msdn.microsoft.com/library/f6641f59-5267-4f57-8957-63b93d1a9679)。  
  
## <a name="see-also"></a>另请参阅  
 [向报表历史记录添加快照（报表管理器）](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [报表管理器（SSRS 本机模式）](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  
