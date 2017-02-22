---
title: "DCOMCNFG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DCOMCNFG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DCOM, configuring in ATL"
  - "DCOMCNFG utility"
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# DCOMCNFG
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**DCOMCNFG** 是允许配置在注册表的各种DCOM组特定的Windows NT 4.0实用工具。  **DCOMCNFG** 窗口有三页上:默认安全、默认属性和应用程序。  在Windows 2000下第四页上，默认协议，存在。  
  
## 默认安全页  
 可以使用默认安全页指定对象的默认权限在系统。  默认安全页有三个部分:Access、生成和配置。  若要更改部分的默认设置，单击相应的 **Edit Default** 按钮。  这些默认安全设置在 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`下的注册表存储。  
  
## 默认协议页  
 本页列出设置网络协议可用于该计算机的DCOM。  该命令以反映他们要使用的优先级;第一个列表包含最高优先级。  协议可以从该页中添加或删除。  
  
## 默认属性页  
 在默认属性，如果需要其他设备的客户端访问COM对象运行该计算机，的页，必须选择 **Enable Distributed COM on this computer** 复选框。  选择此选项将 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` 值设置为 `Y`。  
  
## 应用程序页  
 您可以更改特定对象的设置与应用程序页。  选择应用程序从列表中单击 **属性** 按钮。  "属性"窗口有五页:  
  
-   常规页确认您使用的应用程序。  
  
-   位置页可以指定应用程序应运行，当客户端对相关CLSID时的 `CoCreateInstance`。  如果选择 **Run application on the following computer** 复选框并输入计算机名称，则 `RemoteServerName` 值添加该应用程序的AppID下。  清除 **Run application on this computer** 复选框。`LocalService` 值重命名为 `_LocalService`，因此，从而，禁用它。  
  
-   安全页类似于 **DCOMCNFG** 窗口中的默认安全页，除此之外，这些设置仅应用于当前应用程序。  同样，设置存储在该对象的AppID下。  
  
-   标识该页标识哪个用户用来运行应用程序。  
  
-   终结点页列出设置协议和终结点可供选定的DCOM服务器的客户端使用。  
  
## 请参阅  
 [服务](../atl/atl-services.md)