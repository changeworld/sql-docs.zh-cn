---
title: SQUARE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c375621cf6b8f6310fad1beec74b9cf1850478d2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214977"
---
# <a name="square-ssis-expression"></a>SQUARE（SSIS 表达式）
  返回数值表达式的平方。  
  
## <a name="syntax"></a>语法  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 是任意数值数据类型的数值表达式。 有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>结果类型  
 DT_R8  
  
## <a name="remarks"></a>备注  
 如果参数为空，SQUARE 将返回空结果。  
  
 执行 SQUARE 操作前，参数会转换为 DT_R8 数据类型。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例返回 12 的平方。 返回结果为 144。  
  
```  
SQUARE(12)  
```  
  
 以下示例返回两列值相减所得结果的平方。 如果 **Value1** 包含 12， **Value2** 包含 4，则 SQUARE 函数返回 64。  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 以下示例通过对两个变量应用 SQUARE 函数，然后计算其结果相加值的平方根，返回直角三角形斜边的长度。 如果 **Side1** 包含3， **Side2** 包含4，则 SQRT 函数返回 5。  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  在表达式中，变量名始终包含前缀 \@。  
  
## <a name="see-also"></a>请参阅  
 [函数&#40;SSIS 表达式&#41;](functions-ssis-expression.md)  
  
  
