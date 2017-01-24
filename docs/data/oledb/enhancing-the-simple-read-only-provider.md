---
title: "增强简单的只读提供程序 | Microsoft Docs"
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
  - "IRowsetLocate 类"
  - "IRowsetLocate 类, 添加到 OLE DB 模板提供程序"
  - "只读提供程序 [C++]"
  - "简单只读提供程序 [C++]"
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 增强简单的只读提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节说明如何增强在上一节中创建的[简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)。  `IRowsetLocateImpl` 创建 `IRowsetLocate` 接口的实现，并为您添加书签支持。  
  
 有了工作提供程序后，可能需要增强它，以使提供程序更新、处理事务或者增强取行算法的性能。  大多数提供程序增强都涉及将接口添加到现有 COM 对象。  
  
 以下主题中的示例通过将 `IRowsetLocate` 接口添加到 `CAgentRowset` 增强取行机制。  这些主题显示如何：  
  
-   [使 RMyProviderRowset 从 IRowsetLocate 中继承](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)。  
  
-   [动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 请参阅  
 [创建简单的只读提供程序](../../data/oledb/creating-a-simple-read-only-provider.md)