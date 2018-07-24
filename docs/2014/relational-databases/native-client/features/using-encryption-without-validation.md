---
title: 使用不带验证的加密 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3349bd91f4e0e4e3db252b6406dc58cdbe6179b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430316"
---
# <a name="using-encryption-without-validation"></a>使用不带验证的加密
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 始终对与登录相关的网络数据包进行加密。 如果在服务器启动时未为其提供任何证书，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将生成可用于对登录数据包进行加密的自签名证书。  
  
 应用程序还可以通过使用连接字符串关键字或连接属性请求对所有网络流量加密。 使用的提供程序字符串时，关键字是"Encrypt"用于 ODBC 和 OLE DB **idbinitialize:: Initialize**，或"Use Encryption for Data"的 ADO 和 OLE DB 使用将初始化字符串用于时**IDataInitialize**. 这也可以通过配置[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]使用 Configuration Manager**强制协议加密**选项。 默认情况下，对某一连接的所有网络流量加密要求在服务器上设置证书。  
  
 有关连接字符串关键字的信息，请参阅[将连接字符串关键字用于 SQL Server Native Client](../applications/using-connection-string-keywords-with-sql-server-native-client.md)。  
  
 若要启用加密时未向证书提供的服务器上，使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]配置管理器可用于同时设置**强制协议加密**和**信任服务器证书**选项。 在这种情况下，如果服务器上未设置可验证的证书，加密将使用不带验证的自签名服务器证书。  
  
 应用程序还可以使用 "TrustServerCertificate" 关键字或与其关联的连接属性确保执行加密。 应用程序设置从不会降低 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端配置管理器设置的安全级别，相反还可能提高安全级别。 例如，如果**强制协议加密**未设置的客户端应用程序可能自行请求加密。 甚至是在未设置服务器证书的情况下，为保证加密，应用程序也可能请求加密和 "TrustServerCertificate"。 不过，如果在客户端配置中未启用 "TrustServerCertificate"，则仍需要已设置的服务器证书。 下表介绍了各种情况：  
  
|“强制协议加密”客户端设置|“信任服务器证书”客户端设置|连接字符串/连接属性加密/对数据使用加密|连接字符串/连接属性信任服务器证书|结果|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|“否”|N/A|否（默认值）|忽略|无加密。|  
|“否”|N/A|是|否（默认值）|仅当存在可验证的服务器证书时才加密，否则连接尝试将失败。|  
|“否”|N/A|是|是|始终加密，但可能使用自签名的服务器证书。|  
|是|“否”|忽略|忽略|仅当存在可验证的服务器证书时才加密，否则连接尝试将失败。|  
|是|是|否（默认值）|忽略|始终加密，但可能使用自签名的服务器证书。|  
|是|是|是|否（默认值）|仅当存在可验证的服务器证书时才加密，否则连接尝试将失败。|  
|是|是|是|是|加密始终发生，但可能会使用自签名的服务器证书。|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB 访问接口  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持加密，而无需通过添加 SSPROP_INIT_TRUST_SERVER_CERTIFICATE 数据源初始化属性，它将实现在 DBPROPSET_SQLSERVERDBINIT 属性验证设置。 此外，新的连接字符串关键字"TrustServerCertificate"，已添加。 它接受值 yes 或 no;不是默认值。 使用服务组件时，它接受值 true 或 false；默认值为 false。  
  
 有关 DBPROPSET_SQLSERVERDBINIT 属性集对所做的增强功能的详细信息，请参阅[初始化和授权属性](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC 驱动程序  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序支持而无需通过添加验证的加密[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)并[SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)函数。 添加了 SQL_COPT_SS_TRUST_SERVER_CERTIFICATE 以接受 SQL_TRUST_SERVER_CERTIFICATE_YES 或 SQL_TRUST_SERVER_CERTIFICATE_NO，默认值为 SQL_TRUST_SERVER_CERTIFICATE_NO。 此外，还添加了新的连接字符串关键字 "TrustServerCertificate"。 它接受值 yes 或 no；默认值为 no。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Native Client 功能](sql-server-native-client-features.md)  
  
  