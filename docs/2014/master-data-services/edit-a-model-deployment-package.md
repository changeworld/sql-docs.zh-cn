---
title: 编辑模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 690897612e73c1f1a9d9cfc8f4a2ed7d8ee84bd9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229267"
---
# <a name="edit-a-model-deployment-package"></a>编辑模型部署包
  本主题介绍如何在 MDS 中部署模型的所选部分，而不是部署整个模型。 为此，您需使用模型包编辑器来编辑 MDS 模型包。  
  
 利用模型包编辑器向导，您可以在要包含在 MDS 包中的模型中选择特定实体、派生层次结构、订阅视图和业务规则，并在稍后进行部署。 您可以忽略不想部署的那部分模型。 当您选择一个实体时，还会自动选择该实体中的所有依赖对象。  
  
 可使用模型包编辑器选择通过 MDSModelDeploy 工具（用于创建包含对象和数据的包文件）或模型部署向导（用于创建仅包含模型结构的文件）创建的包文件中的模型的一部分。 在编辑包中的模型之后，可使用 MDSModelDeploy 工具部署对象和数据，或使用模型部署向导仅部署模型结构。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](administrators-master-data-services.md)。  
  
-   您要编辑的模型包必须存在。 有关详细信息，请参阅[部署模型 (Master Data Services)](../../2014/master-data-services/deploying-models-master-data-services.md)和[使用向导创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)或[使用 MDSModelDeploy 创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。  
  
### <a name="to-edit-a-model-deployment-package"></a>编辑模型部署包  
  
1.  在 Windows 资源管理器在 MDS 服务器上，转至*驱动器*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration。  
  
2.  执行 ModelPackageEditor.exe。  
  
3.  在模型编辑器向导中，单击 **“浏览”**，移至包含您的包的文件夹，选择一个包，然后单击 **“打开”**。 单击“下一步” 。  
  
4.  选择要部署的实体、派生层次结构、订阅视图或业务规则。 取消选择不想部署的这类项。 单击“下一步” 。  
  
5.  验证要部署的所选内容的列表。 若要更改，请单击 **“返回”** 并重复步骤 4。  
  
6.  单击“浏览”，移至要保存部分包的文件夹，然后输入部分包的文件名（使用 .pkg 扩展名）。 单击 **“保存”**。  
  
7.  单击 **“完成”**。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [使用向导部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [使用 MDSModelDeploy 部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  