---
title: SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b40693cd426779f7878c1101fb57efa12ce4e6de
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057257"
---
# <a name="setservicestate-method-wmi-msreportserverconfigurationsetting"></a>SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting)
  打开和关闭报表服务器 Windows 服务和 Web 服务。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameters  
 *EnableWindowsService*  
 一个`Boolean`值，该值指示 Windows 服务的状态。 值为`true`启动报表服务器 Windows 服务; 如果值为`false`停止 Windows 服务。  
  
 *EnableWebService*  
 一个`Boolean`值，该值指示的状态[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Web 服务。 如果值为 `true`，则会启动报表服务器 Web 服务；如果值为 `false`，则会停止该 Web 服务。  
  
 *EnableReportManager*  
 一个`Boolean`值，该值指示报表管理器所需的状态。  
  
 *HRESULT*  
 [out] 指示调用是成功还是失败的值。  
  
## <a name="return-value"></a>返回值  
 返回 *HRESULT* ，指示方法调用是成功还是失败。 值 0 指示方法调用已成功。 非零值指示已发生错误。  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>要求  
 **命名空间:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [MSReportServer_ConfigurationSetting 成员](msreportserver-configurationsetting-members.md)  
  
  
