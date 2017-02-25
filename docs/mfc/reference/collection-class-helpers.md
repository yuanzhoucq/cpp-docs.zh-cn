---
title: "集合类帮助器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合类, Helper 函数"
  - "ConstructElements 函数"
  - "DestructElements 函数"
  - "帮助器函数集合类"
  - "SerializeElements 函数"
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 集合类帮助器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

集合类 `CMap`、`CList`和 `CArray` 全局使用模板化帮助程序函数的用途类似的比较，复制并序列化元素。  在基于 `CMap`的类的实现的一部分，`CList`和 `CArray`，您必须根据需要重写这些函数与生成定制映射中列出，或数组中存储的数据类型。  有关重写帮助器函数的信息 \(如 `SerializeElements`\)，请参见 [集合：如何生成类型安全的集合](../../mfc/how-to-make-a-type-safe-collection.md)文章。  注意 **ConstructElements** 和 **DestructElements** 中已弃用。  
  
 Microsoft 基础类 \(MFC\) 库提供以下全局函数帮助自定义集合类：  
  
### 集合类帮助器  
  
|||  
|-|-|  
|[CompareElements](../Topic/CompareElements.md)|指示元素是否相同。|  
|[CopyElements](../Topic/CopyElements.md)|从数组的元素复制到另一个。|  
|[DumpElements](../Topic/DumpElements.md)|面向流提供的诊断输出。|  
|[HashKey](../Topic/HashKey.md)|计算哈希键。|  
|[SerializeElements](../Topic/SerializeElements.md)|存储或检索元素方式出入存档。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)