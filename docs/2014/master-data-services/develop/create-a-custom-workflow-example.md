---
title: 自定义工作流示例 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 47ea8ae372cc796aa99da7dbb0fbdd99d922becd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129079"
---
# <a name="custom-workflow-example-master-data-services"></a>自定义工作流示例 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 中，当您创建一个自定义工作流类库时，将创建一个实现 <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender> 接口的类。 该接口包含一种方法：<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>，该方法是在工作流启动时由 SQL Server MDS Workflow Integration Service 调用的。 <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> 方法包含两个参数：workflowType 包含在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中“工作流类型”文本框中输入的文本；dataElement 包含触发工作流业务规则项的元数据和项数据。  
  
## <a name="custom-workflow-example"></a>自定义工作流示例  
 以下代码示例说明如何实现 <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> 方法以从触发工作流业务规则的元素的 XML 数据中提取 Name、Code 和 LastChgUserName 属性，以及如何调用存储过程以将这些属性插入到其他数据库中。 有关项数据 XML 的示例和其包含的标记的说明，请参阅[自定义工作流 XML 说明 &#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md)。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [创建自定义工作流 &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md)  
  
  
