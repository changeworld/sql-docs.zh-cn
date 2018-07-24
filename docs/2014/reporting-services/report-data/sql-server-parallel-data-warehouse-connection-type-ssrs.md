---
title: SQL Server 并行数据仓库连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3925fd3d-2aa1-4768-96ad-cfc2c0ba9283
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b1b12938e2043ee126c81313fc955454742bcde
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149408"
---
# <a name="sql-server-parallel-data-warehouse-connection-type-ssrs"></a>SQL Server Parallel Data Warehouse 连接类型 (SSRS)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] 是一种可缩放的数据仓库工具，可提供性能和可伸缩性通过大规模并行处理。 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 使用[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]数据库进行分布式处理和数据存储。  
  
 该工具可跨多个物理节点对大型数据库表进行分区，每个节点运行自己的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]实例。 当报表连接到 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 以检索报表数据时，它将连接到 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 工具中的控制节点，该节点负责管理查询处理。 建立连接后，无论是使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 环境内部还是外部的 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 实例，都没有任何区别。  
  
 若要包含来自[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]在报表中必须具有基于的报表数据源的类型的数据集[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]并行数据仓库。 此内置数据源类型基于[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]并行数据仓库数据扩展插件。 使用此数据源类型可连接到并从中检索数据[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]。  
  
 此数据扩展插件支持多值参数、服务器聚合以及与连接字符串分开管理的凭据。  
  
 有关详细信息，请参阅网站 [SQL Server 2008 R2 Parallel Data Warehouse](http://go.microsoft.com/fwlink/?LinkId=150895)。  
  
 使用本主题中的信息来生成一个数据源。 有关分步说明，请参阅[添加和验证数据连接或数据源&#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。  
  
##  <a name="Connection"></a> 连接字符串  
 连接到 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)]时，也会连接到 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 工具中的数据库对象。 可在查询设计器中指定要使用的数据库对象。 如果未在连接字符串中指定数据库，则将连接到管理员为您分配的默认数据库。 请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。 下面的连接字符串示例指定示例数据库**CustomerSales**，请在[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]设备：  
  
```  
HOST=<IP address>; database= CustomerSales; port=<port>  
```  
  
 此外，可以使用 **“数据源属性”** 对话框提供用户名和密码等凭据。系统会自动将 `User Id` 和 `Password` 选项追加到连接字符串中，您无需将它们作为连接字符串的一部分键入。 用户界面还提供了选项来指定中的控制节点的 IP 地址[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]设备和端口号。 默认情况下，该端口为 17000。 该端口可由管理员配置，您的连接字符串可能会使用不同的端口号。  
  
 有关连接字符串示例的详细信息，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。  
  
##  <a name="Credentials"></a> 凭据  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 提供其自己的安全技术，以实现和存储用户名和密码。 不能使用 Windows 身份验证。 如果试图使用 Windows 身份验证连接到 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] ，则会发生错误。  
  
 凭据必须具有足够的权限访问数据库。 根据要执行的查询，您可能需要具有其他权限，例如访问表和视图的足够权限。 外部数据源的所有者必须配置相应的凭据，使这些凭据足以提供对所需数据库对象的只读访问。  
  
 在报表创作客户端，可以使用下列选项指定凭据：  
  
-   使用存储的用户名和密码。 若要协商当包含报表数据的数据库与报表服务器不同时产生的双跃点，请选择使用凭据作为 Windows 凭据的选项。 也可以选择在连接到数据源后模拟经过身份验证的用户。  
  
-   不需要提供任何凭据。 若要使用此选项，您必须具有为报表服务器配置的无人参与的执行帐户。 有关详细信息，请参阅 msdn.microsoft.com 上 [Reporting Services 文档](http://go.microsoft.com/fwlink/?linkid=121312)中的[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。  
  
 有关详细信息，请参阅[数据连接、 数据源和 Reporting Services 中的连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
##  <a name="Query"></a> 查询  
 查询指定了要为报表数据集检索哪些数据。  
  
 查询的结果集中的列填充数据集的字段集合。 如果查询返回多个结果集，则报表仅处理查询所检索的第一个结果集。 默认情况下，如果您创建一个新查询，或者打开一个可在图形查询设计器中显示的现有查询，则可以使用关系查询设计器。 可以通过下列方式指定查询：  
  
-   以交互方式生成查询。 使用关系查询设计器，此设计器显示表、视图及其他数据库项按数据库架构组织的层次结构视图。 选择表或视图中的列。 通过指定筛选条件、分组和聚合，限制要检索的数据行数。 通过设置参数选项自定义报表运行时的筛选器。  
  
-   键入或粘贴查询。 使用基于文本的查询设计器输入[!INCLUDE[DWsql](../../../includes/dwsql-md.md)]文本直接，粘贴来自其他源，可以输入不能通过使用关系查询设计器中，生成的复杂查询或输入基于查询的表达式的查询文本。  
  
-   从文件或报表中导入现有的查询。 使用任一查询设计器中的 **“导入查询”** 按钮浏览到 .sql 文件或 .rdl 文件，然后导入查询。  
  
 有关详细信息，请参阅[关系查询设计器用户界面（报表生成器）](relational-query-designer-user-interface-report-builder.md)和[基于文本的查询设计器用户界面（报表生成器）](text-based-query-designer-user-interface-report-builder.md)。  
  
 基于文本的查询设计器支持[文本](#QueryText)模式，在此模式下，可以键入 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] 命令，选择来自数据源的数据。  
  
-   [文本](#QueryText)  
  
 在 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] 中，使用 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] ；在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中，使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。 SQL 语言的这两种方言非常相似。 为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据源连接类型编写的查询通常可以用于 [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] 数据源连接类型。  
  
 如果不对数据进行聚合和汇总以减少查询返回的行数，从大型数据库（包括 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 等数据仓库）检索报表数据的查询所生成的结果集就可能会包含大量的行。 您可以使用图形查询设计器或基于文本的查询设计器，编写包括聚合和分组的查询。  
  
 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] 支持的查询设计器提供的用于汇总数据的子句、 关键字和聚合。  
  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 使用的图形查询设计器提供对分组和聚合的内置支持，有助于编写仅检索摘要数据的查询。 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)]语言功能包括： GROUP BY 子句、 DISTINCT 关键字和 SUM 和 COUNT 等聚合。 基于文本的查询设计器提供对完全支持[!INCLUDE[DWsql](../../../includes/dwsql-md.md)]语言，包括分组和聚合。  
  
 有关 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 的详细信息，请参阅 msdn.microsoft.com 上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [联机丛书](http://go.microsoft.com/fwlink/?LinkId=141687)中的 [Transact-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)。  
  
###  <a name="QueryText"></a> 使用 Text 查询类型  
 在基于文本的查询设计器中，可以键入 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] 命令来定义数据集中的数据。 使用要从中检索数据的查询[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]使用的实例从检索数据的相同[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]内未运行[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]应用程序。 例如，以下[!INCLUDE[DWsql](../../../includes/dwsql-md.md)]查询选择职位为销售助理的所有雇员的姓名：  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 单击工具栏上的 **“运行”** 按钮 (**!**) 可以运行查询并显示结果集。  
  
 若要参数化此查询，请添加一个查询参数。 例如，将 WHERE 子句更改为下面的内容：  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 运行查询时，会自动创建与查询参数对应的报表参数。 有关详细信息，请参阅本主题后面的 [查询参数](#Parameters) 。  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
##  <a name="Parameters"></a> Parameters  
 如果查询文本包含查询变量或具有输入参数的存储过程，则将自动生成数据集的对应查询参数和报表的报表参数。 查询文本不得包含针对每个查询变量的 DECLARE 语句。  
  
 例如，下面的 SQL 查询将创建一个名为 `EmpID` 的报表参数：  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 默认情况下，各个报表参数的数据类型均为“Text”，并具有自动创建的数据集，以提供可用值的下拉列表。 创建报表参数后，您可能需要更改默认值。 有关详细信息，请参阅[报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)。  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
##  <a name="Remarks"></a> 注释  
  
###### <a name="platform-and-version-information"></a>平台和版本信息  
 有关平台和版本支持的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][联机丛书](http://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
##  <a name="HowTo"></a> 操作指南主题  
 本节包含使用数据连接、数据源和数据集的分步说明。  
  
 [添加和验证数据连接或数据源&#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [向数据集添加筛选器（报表生成器和 SSRS）](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
##  <a name="Related"></a> 相关章节  
 文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。  
  
 [向报表添加数据&#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md)  
 提供访问报表数据的概述。  
  
 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 提供有关数据连接和数据源的信息。  
  
 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 提供有关嵌入数据集和共享数据集的信息。  
  
 [数据集字段集合（报表生成器和 SSRS）](dataset-fields-collection-report-builder-and-ssrs.md)  
 提供有关查询生成的数据集字段集合的信息。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [联机丛书](http://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。  
 提供有关每个数据扩展插件的平台和版本支持的详细信息。  
  
 ![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于“返回页首”链接的箭头图标")[返回页首](#BackToTop)  
  
## <a name="see-also"></a>请参阅  
 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [表达式（报表生成器和 SSRS）](../report-design/expressions-report-builder-and-ssrs.md)  
  
  