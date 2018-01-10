---
title: "DCOMCNFG |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DCOMCNFG
dev_langs: C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f40b372666ba2b623450eb0e58a6c0ff372559ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG**是 Windows NT 4.0 实用工具，可以在注册表中配置各种特定于 DCOM 的设置。 **DCOMCNFG**窗口有三个页： 默认安全性、 默认属性和应用程序。 在 Windows 2000 下第四个页上，默认协议，不存在。  
  
## <a name="default-security-page"></a>默认安全页  
 默认的安全性页可用于在系统上指定的对象的默认权限。 默认安全页具有三个部分： 访问、 启动和配置。 若要更改部分的默认值，请单击相应**编辑默认值**按钮。 在下面的注册表中存储这些默认安全设置`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`。  
  
## <a name="default-protocols-page"></a>默认协议页  
 此页列出 DCOM 到此计算机上可用的网络协议的集。 顺序反映了在其中将会使用它们; 的优先级在列表中的第一个具有最高优先级。 协议可以添加或删除从该页。  
  
## <a name="default-properties-page"></a>默认属性页  
 在默认属性页上，您必须选择**在此计算机上启用分布式 COM**复选框，如果你希望在此计算机上运行的访问 COM 对象的其他计算机上的客户端。 选择此选项设置`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM`值赋给`Y`。  
  
## <a name="applications-page"></a>应用程序页  
 更改具有应用程序页的特定对象的设置。 只需从列表中选择应用程序并单击**属性**按钮。 属性窗口具有 5 个页面：  
  
-   常规页上确认你正在使用的应用程序。  
  
-   位置页可以指定当客户端调用时，应用其中运行`CoCreateInstance`上相关的 CLSID。 如果你选择**下列计算机上运行应用程序**复选框，输入计算机名称时，则`RemoteServerName`下为该应用程序 AppID 添加值。 清除**此计算机上运行应用程序**复选框重命名`LocalService`值赋给`_LocalService`并从而，禁用它。  
  
-   安全页是类似于网页中找到的默认安全性**DCOMCNFG**窗口中，只不过这些设置仅适用于当前应用程序。 同样，这些设置将存储在该对象的 AppID。  
  
-   标识页将标识的用户用于运行应用程序。  
  
-   终结点页上列出的协议和终结点可供所选的 DCOM 服务器的客户端使用的集。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)

