---
title: "确定要使用的访问器类型 | Microsoft Docs"
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
  - "访问器 [C++], 类型"
  - "行集合 [C++], 数据类型"
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 确定要使用的访问器类型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以在编译时或运行时确定行集合上的数据类型。  
  
 如果需要在编译时确定数据类型，则应使用静态访问器（如 `CAccessor`）。  可以手动确定数据类型，也可以通过使用“ATL OLE DB 使用者向导”来确定。  
  
 如果需要在运行时确定数据类型，则应使用动态访问器（`CDynamicAccessor` 或其子级）或手动访问器 \(`CManualAccessor`\)。  在这些情况下，可以在行集合上调用 `GetColumnInfo` 以返回列绑定信息，从此信息中即可确定类型。  
  
 下表列出了使用者模板中所提供的访问器类型。  每种访问器都各有利弊。  根据不同的情况，其中一种访问器类型将适合您的需要。  
  
|访问器类|绑定|参数|注释|  
|----------|--------|--------|--------|  
|`CAccessor`|用 `COLUMN_ENTRY` 宏创建用户记录。  这些宏将该记录中的数据成员绑定到此访问器。  创建行集合后，列将无法取消绑定。|是，通过使用 **PARAM\_MAP** 宏项。  绑定后，参数将无法取消绑定。|速度最快的访问器，因为代码数量较少。|  
|`CDynamicAccessor`|自动。|不可以。|当不知道行集合中的数据类型时很有用。|  
|`CDynamicParameterAccessor`|自动，但可以[重写](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，但条件是提供程序支持 `ICommandWithParameters`。  自动绑定参数。|速度比 `CDynamicAccessor` 慢，但对于调用一般存储过程很有用。|  
|**CDynamicStringAccessor\[A,W\]**|自动。|不可以。|将在数据存储区中存取的数据作为字符串数据检索。|  
|`CManualAccessor`|手动使用 `AddBindEntry`。|手动使用 `AddParameterEntry`。|非常快；参数和列只绑定一次。  您自己确定要使用的数据类型。（有关示例，请参见 [DBVIEWER](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832) 示例）。比 `CDynamicAccessor` 或 `CAccessor` 需要更多的代码。  更类似于直接调用 OLE DB。|  
|`CXMLAccessor`|自动。|不可以。|将在数据存储区中存取的数据作为字符串数据检索，并将其格式化为带有 XML 标记的数据。|  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)