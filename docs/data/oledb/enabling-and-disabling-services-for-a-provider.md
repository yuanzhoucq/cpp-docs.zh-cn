---
title: "为提供程序启用或禁用服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 服务 [OLE DB], 启用和禁用"
  - "服务提供程序 [OLE DB]"
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 为提供程序启用或禁用服务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认情况下，可以为访问单个提供程序的所有应用程序启用或禁用个别 OLE DB 服务。  实现方法是在提供程序的 CLSID 下添加 **OLEDB\_SERVICES** 注册表项，并提供一个指定要启用或禁用的服务的 `DWORD` 值，如下表所示。  
  
|启用的默认服务|关键字值|  
|-------------|----------|  
|所有服务（默认）|0xffffffff|  
|除“池”和“自动登记”外的所有服务|0xfffffffe|  
|除“客户端光标”外的所有服务|0xfffffffb|  
|除“池”、“自动登记”和“客户端光标”外的所有服务|0xfffffff0|  
|没有服务|0x00000000|  
|没有聚合，禁用所有服务|\<缺少键\>|  
  
## 请参阅  
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)