---
title: "转换不受提供程序支持的数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序模板, 不支持的数据类型"
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 转换不受提供程序支持的数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用者请求的数据类型不受提供程序支持时，`IRowsetImpl::GetData` 的 OLE DB 提供程序模板代码将调用 Msdadc.dll 以转换该数据类型。  
  
 如果实现象 `IRowsetChange` 这样需要数据转换的接口，可以调用 Msdaenum.dll 进行转换。  使用 Atldb.h 中定义的 `GetData` 作为示例。  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)