---
title: 指定合并表项目的处理顺序 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7c4a525c60476f3988d9b7b00130835859a79024
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834675"
---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>指定合并表项目的处理顺序
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  通过使用合并复制，您可以指定在同步过程中合并代理处理项目的顺序。 您可以在使用复制存储过程创建项目时以编程方式为每个项目指定顺序。 项目按值的由低到高顺序进行处理。 如果两个项目具有相同值，将对其进行并发处理。 有关详细信息，请参阅[指定合并项目的处理顺序](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)。  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>为新的合并项目指定处理顺序  
  
1.  在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)。 为 **@processing_order**。 有关详细信息，请参阅 [定义项目](../../../relational-databases/replication/publish/define-an-article.md)。  
  
    > [!NOTE]  
    >  创建指定了顺序的项目时，应在项目顺序值之间留有间隔。 这样便于以后设置新值。 例如，如果有三个项目需要您为它们指定固定处理顺序，则应将 **@processing_order** 的值分别设置为 10、20 和 30，而不是 1、2 和 3。  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>更改合并项目的处理顺序  
  
1.  若要确定项目的处理顺序，请执行 [sp_helpmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)，并记下结果集中的 **processing_order** 值。  
  
2.  在发布服务器上，对发布数据库执行 [sp_changemergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)。 为 **processing_order** 指定值 **@property** ，然后为 **@value**。  
  
## <a name="see-also"></a>另请参阅  
 [指定合并项目的处理顺序](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  
