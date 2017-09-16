---
title: "设置的数据源属性 |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e49d68f567f26e852dcf8bee3a9827797c9c23f2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-data-source-properties"></a>设置数据源属性
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  数据源是在 Java Platform, Enterprise Edition (Java EE) 环境中创建 JDBC 连接的首选机制。 数据源可提供连接、池化连接和分布式连接，并且无需将连接属性硬编码到 Java 代码中。 所有[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]数据源可以设置或通过分别使用相应的 setter 和 getter 方法获取的任何属性值。  
  
 通过使用 Java EE 产品（例如应用程序服务器和 servlet/JSP 引擎），通常可配置数据库访问的数据源。 中列出的任何属性[设置连接属性](../../connect/jdbc/setting-the-connection-properties.md)可以指定任何位置配置将允许你为属性输入属性的主题 = 值对。  
  
 有关详细信息[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]数据源，请参阅[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)类。 有关如何使用 SQLServerDataSource 类来与建立连接的示例[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]数据库，请参阅[数据源示例](../../connect/jdbc/data-source-sample.md)。  
  
## <a name="see-also"></a>另请参阅  
 [连接到 SQL Server 使用 JDBC 驱动程序](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  