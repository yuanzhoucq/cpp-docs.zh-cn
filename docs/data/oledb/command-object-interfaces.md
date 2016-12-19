---
title: "命令对象接口 | Microsoft Docs"
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
  - "命令对象接口 [C++]"
  - "命令对象 [OLE DB]"
  - "OLE DB [C++], 命令对象接口"
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令对象接口
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命令对象使用 `IAccessor` 接口指定参数绑定。  使用者调用 `IAccessor::CreateAccessor`，调用过程中它会传递一个 `DBBINDING` 结构数组。  `DBBINDING` 包含有关列绑定的信息（如类型和长度）。  提供程序接收这些结构并确定如何传输数据和是否需要转换。  
  
 `ICommandText` 接口提供指定文本命令的方法。  `ICommandProperties` 接口处理所有命令属性。  
  
## 请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)