---
title: 记录集目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 977cf906b46ae792bc979c5b6b844dbf6368b40e
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2018
ms.locfileid: "51640504"
---
# <a name="recordset-destination"></a>记录集目标
  记录集目标创建和填充内存中的 ADO 记录集。 记录集的形式是在设计时由记录集目标的输入定义的。  
  
## <a name="configuration-of-the-recordset-destination"></a>记录集目标的配置  
 您可以通过指定用于存储 ADO 记录集的变量，来配置记录集目标。  
  
 运行时，ADO 记录集写入由记录集目标的 VariableName 属性所指定的类型变量 Object。 然后，该变量使该记录集在数据流外部可用，这样脚本和其他包元素便可使用它。  
  
 此源具有一个输入。 它不支持错误输出。  
  
 可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 **“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。 有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：  
  
-   [通用属性](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [记录集目标自定义属性](../../integration-services/data-flow/recordset-destination-custom-properties.md)  
  
 有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)。  
  
## <a name="related-tasks"></a>Related Tasks  
 [使用记录集目标](../../integration-services/data-flow/use-a-recordset-destination.md)  
  
  
