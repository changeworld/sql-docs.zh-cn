---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 353f4bc91c35b5000ab6a02f3b24a11225bc3014
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416596"
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|10520|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|PG_PARAM_NOT_ALLOWED|  
|消息正文|无法创建计划指南 '%.*ls'，因为 @type 指定为 '%ls' ，并且为参数 '%ls' 指定了非 NULL 值。 此类型要求该参数的值为 NULL 值。 请为该参数指定 NULL 值，或将该类型更改为允许该参数为非 NULL 值的类型。|  
  
## <a name="explanation"></a>解释  
 @type 中指定的类型要求指定参数的值为 NULL 值，但却提供了非 NULL 值。  
  
## <a name="user-action"></a>用户操作  
 请为该参数指定 NULL 值，或将该类型更改为允许该参数为非 NULL 值的类型。  
  
## <a name="see-also"></a>请参阅  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [计划指南](../performance/plan-guides.md)  
  
  