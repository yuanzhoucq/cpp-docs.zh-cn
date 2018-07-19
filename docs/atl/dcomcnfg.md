---
title: DCOMCNFG |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DCOMCNFG
dev_langs:
- C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6c188639a7ac9763bb2dcccb926ff6b0f419728
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851504"
---
# <a name="dcomcnfg"></a>DCOMCNFG
DCOMCNFG 是 Windows NT 4.0 实用工具，可让你在注册表中配置各种特定于 DCOM 的设置。 DCOMCNFG 窗口中有三个页： 默认安全、 默认属性和应用程序。 在 Windows 2000 下第四页上，默认协议，不存在。  
  
## <a name="default-security-page"></a>默认安全页  
 默认安全页可用于在系统上指定对象的默认权限。 默认安全页包含三个部分： 访问、 启动和配置。 若要更改节的默认值，请单击相应**编辑默认值**按钮。 这些默认安全设置存储在注册表中`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`。  
  
## <a name="default-protocols-page"></a>默认协议页  
 此页列出了在此计算机上的 DCOM 可用的网络协议的集。 顺序反映了在其中将会使用它们; 的优先级在列表中的第一个具有最高优先级。 可以添加或删除此页面中的协议。  
  
## <a name="default-properties-page"></a>默认值属性页  
 在默认的属性页上，必须选择**在此计算机上启用分布式 COM**复选框，如果你希望在此计算机上运行的访问 COM 对象的其他计算机上的客户端。 选择此选项设置`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM`值设为`Y`。  
  
## <a name="applications-page"></a>应用程序页  
 更改与应用程序页的特定对象的设置。 只需从列表中选择应用程序，然后单击**属性**按钮。 属性窗口具有五个页面：  
  
-   常规页确认您正在使用的应用程序。  
  
-   位置页可以指定应用程序运行时在客户端调用的位置`CoCreateInstance`上相关的 CLSID。 如果选择**以下计算机上运行应用程序**复选框并输入计算机名称，则`RemoteServerName`值则会添加在该应用程序的 AppID。 清除**在此计算机上运行应用程序**复选框重命名`LocalService`值设为`_LocalService`并从而，禁用它。  
  
-   安全性页具有类似于在 DCOMCNFG 窗口中，找到默认安全页，只不过这些设置仅适用于当前应用程序。 同样，设置存储在该对象的 AppID。  
  
-   标识页将标识哪个用户用来运行该应用程序。  
  
-   终结点页列出的一套协议和终结点可供所选的 DCOM 服务器的客户端使用。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)

