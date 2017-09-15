---
title: "开始使用 SQL Server 中的机器学习 |Microsoft 文档"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09d6e887a8c64c98a1c3f68c78b07c26da6ffb76
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>开始使用 SQL Server 中的机器学习

Microsoft 提供的机器学习解决方案的集成、 可缩放集用于在本地和云：

+ **集成**，这是因为可以在 SQL Server 中运行 R 或 Python。 这允许您轻松地合并企业进程 ETL 和报告使用数据科学任务，例如工程，模型创建和评分的功能。
+ **可缩放**，因为数据科研人员可以开发和测试的解决方案是便携式计算机，然后将其部署到多个平台，为分布式或并行处理的密钥操作如模型定型集和评分。 支持的平台包括 Windows、 Hadoop 和 Spark 上的 SQL Server。

这篇文章提供有关在 Microsoft 机器学习平台中的每个产品的资源的链接。

## <a name="machine-learning-in-sql-server"></a>SQL Server 中的机器学习

+ SQL Server 2017

  开始使用 SQL Server 自 2017 年 1 CTP 2.0，支持 Python 现已添加，并且名称更改为机器学习服务 （数据库中） 以反映支持广泛的计算机学习解决方案。 现在您可以通过使用 SQL 工具运行 R 或 Python 代码来自动化机器学习任务。 或者，使用 SQL Server 计算机作为_计算上下文_从远程开发环境中启动的作业。

    + [SQL Server 中的 Python 的体系结构概述](python/architecture-overview-sql-server-python.md)
    + [设置 SQL Server R Services 或机器学习服务](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

+ SQL Server 2016

  SQL Server 2016 支持在 SQL Server 使用存储的过程中运行 R 代码。 这可以轻松通过使用 SQL 工具自动化机器学习任务。 或者，您可以从远程便携式计算机或 R 开发环境中，运行 R 代码，在使用 SQL Server 计算机时为_计算上下文_。

  此集成为你的数据提供了安全性，并允许你管理并平衡资源使用。

    + [获取已启动产品 SQL Server R Services](r/getting-started-with-sql-server-r-services.md)
    + [设置 SQL Server R Services 或机器学习服务](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>Microsoft 机器学习服务器 (Microsoft R Server)

在 SQL Server 2017 支持人员想要运行分布式、 可缩放的机器学习作业，但他们不需要使用 SQL Server 数据库引擎时，如使用集成的企业客户提供安装 Microsoft 机器学习服务器选项SQL 计算上下文。

SQL Server 2016 中，使用选项来安装 Microsoft R Server。
  
  + [Microsoft R Server 简介](https://msdn.microsoft.com/microsoft-r/rserver)
  
你还可以通过特定于平台的安装程序可从 MSDN 安装 R Server:

  + [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
  + [R Server for Linux](https://msdn.microsoft.com/microsoft-r/rserver-install-linux-server)
  + [R Server for Hadoop](https://msdn.microsoft.com/microsoft-r/rserver-install-hadoop)

> [!IMPORTANT]
> 如果你想要运行使用 R Server 的 Python，请务必安装最新版本，**机器学习服务器**，即仅可通过提供自 2017 年 SQL Server 安装程序：
> 
>    + [设置 Microsoft R Server 或机器学习服务器](../advanced-analytics/r/create-a-standalone-r-server.md)

## <a name="related-products"></a>相关的产品

+ [设置数据科学客户端](../advanced-analytics/r/set-up-a-data-science-client.md)

  如果你已安装机器学习服务器产品之一，这篇文章提供有关如何设置单独的计算机用于开发和测试解决方案，包括工具和所需的库的信息。

+ [数据科学虚拟机](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  快速开始你进入机器学习通过获取此完整机器学习解决方案从 Azure 应用商店。 数据科学虚拟机 （常缩写为"DSVM"） 包括 SQL Server、 Microsoft 机器学习服务器和所有开发工具。
  
  在 Windows 2016 预览版本，以提供 Windows 10 的全新可自定义外观上运行的最新版本的数据科学虚拟机 (DSVM)。 它是预先配置了与 NVIDIA 驱动程序、 CUDA 工具包 8.0 和 GPU 工作负荷的 NVIDIA cuDNN 库。

## <a name="resources-for-learning"></a>用于了解资源

+ [机器学习教程](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  从此处开始用于了解与使用 SQL Server 2017 和 SQL Server 自 2017 年的计算机学习解决方案中找到的所有资源的列表。

### <a name="r-tutorials"></a>R 教程

+ [SQL Server R 教程](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   了解如何在 SQL Server 中运行 R、 创建和使用远程计算上下文，或使用 SQL Server 的 R 中进行模拟。
   
   包含"提供的所有代码"教程，以便你可以从 SQL Server Management Studio，运行完整的 R 解决方案，而无需曾经打开 R IDE ！

+ [浏览 R 和 ScaleR 在 25 短函数中](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   不熟悉 R？ 想知道 Microsoft R （或 RevoScaleR） 如何比较到标准 R？ R Server，请参阅这些快速启动。

### <a name="python-tutorials"></a>Python 教程

+ [SQL Server Python 教程](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  了解如何在 SQL Server 中运行 Python。 使用 Python 生成一个模型，并使用它来评分 SQL Server 数据。

   SQL 开发人员的端到端解决方案提供了你需要从 SQL Server Management Studio 中运行 Python 的所有代码。

+ [发布和使用的 Python 代码](../advanced-analytics/python/publish-consume-python-code.md)

  本演练中附带了将模型部署到 web 服务使用机器学习服务器所需的所有代码。

### <a name="product-samples-with-code"></a>使用代码的产品示例

SQL Server 开发团队的这些解决方案中 R 或 Python，运行，并演示与业务应用程序集成机器学习的常见方案。

+ [Build an intelligent app with SQL Server and R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

+ [生成与 SQL Server 和 Python 的智能应用程序](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

### <a name="data-science-solution-templates"></a>数据科学解决方案模板

从 Microsoft 数据科学团队的解决方案模板表示定制为特定行业或方案的完整示例解决方案。 应将它们用作构建基块以帮助你实现快，解决方案或演示最佳做法。 每个模板包含示例数据和可自定义代码。

+ [解决方案模板](../advanced-analytics/tutorials/data-science-scenarios-and-solution-templates.md)

## <a name="next-steps"></a>后续步骤

[SQL Server 机器学习服务入门](../advanced-analytics/r/getting-started-with-sql-server-r-services.md)

[要开始使用 Microsoft 机器学习服务器](../advanced-analytics/r/getting-started-with-microsoft-r-server-standalone.md)
