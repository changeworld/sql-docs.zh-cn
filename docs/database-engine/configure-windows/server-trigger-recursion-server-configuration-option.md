---
title: “服务器触发器递归”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0e5ae4e8696a70146f956de173a8f245f720db75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608940"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion 服务器配置选项
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  使用 **server trigger recursion** 选项可指定是否允许服务器级触发器递归激发。 当此选项设置为 1 (ON) 时，将允许服务器级触发器递归激发。 当设置为 0 (OFF) 时，服务器级触发器不能递归激发。 当 server trigger recursion 选项设置为 0 (OFF) 时，仅阻止直接递归。 （若要禁用间接递归，请将 **nested triggers** 选项设置为 0。）该选项的默认值为 1 (ON)。 该设置更改后立即生效，而不需要重新启动服务器。  
  
 有关详细信息，请参阅 [创建嵌套触发器](../../relational-databases/triggers/create-nested-triggers.md)。  
  
## <a name="see-also"></a>另请参阅  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
