---
title: setAsciiStream 方法 (SQLServerClob) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6e1779df-3b2a-41d1-8dca-99692cc9da14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a93a6a8750f48f58c6e676ebe619985dad67277d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694805"
---
# <a name="setasciistream-method-sqlserverclob"></a>setAsciiStream 方法 (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回用来将 ASCII 字符写入 CLOB 的流（从指定位置开始写入）。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>Parameters  
 *pos*  
  
 开始写入 CLOB 对象的位置。  
  
## <a name="return-value"></a>返回值  
 可向其中写入 ASCII 编码字符的流。  
  
## <a name="exceptions"></a>异常  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 此 setAsciiStream 方法由 java.sql.Clob 接口中的 setAsciiStream 方法指定。  
  
 输出流从指定位置开始覆盖 CLOB 中的字符数据，并可以超过 CLOB 的初始长度。 指定“位置+1”值将追加 ASCII 字符。 指定“位置+2”或更大值（或零或更小值）会引发位置错误。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成员](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 类](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
