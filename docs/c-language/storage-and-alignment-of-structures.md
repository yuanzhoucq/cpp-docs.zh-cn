---
title: "结构的存储和对齐 | Microsoft Docs"
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
  - "结构的对齐"
  - "包装结构"
  - "存储结构"
  - "结构存储"
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 结构的存储和对齐
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 结构成员按其声明顺序进行存储：第一个成员的内存地址最低，最后一个成员的内存地址最高。  
  
 每个数据对象具有 *alignment\-requirement*。  对于结构，要求是其成员中的最大者。  为每个对象分配一个 *offset*，以便  
  
 *offset* `%` *alignment\-requirement* `==` 0  
  
 如果整型的大小相同，并且下一个位域适合当前分配单元而未跨位域的常见对齐要求所强加的边界，则将相邻位域打包到相同的 1 字节、2 字节或 4 字节分配单元中。  
  
 为了节省空间或遵循现有数据结构，您可能需要或多或少的简洁存储结构。  [\/Zp](../build/reference/zp-struct-member-alignment.md)\[*n*\] 编译器选项和 [\#pragma pack](../preprocessor/pack.md) 控制将结构数据“打包”到内存中的方式。  使用 \/Zp\[*n*\] 选项（其中，*n* 为 1、2、4、8 或 16）时，第一个结构成员后的每个结构成员将存储在字节边界上，这些字节边界是字段或包装大小 \(*n*\) 的对齐要求（以较小者为准）。  表示为公式，字节边界为  
  
```  
min( n, sizeof( item ) )  
```  
  
 其中，*n* 是使用 \/Zp\[*n*\] 选项表示的包装大小，而 *item* 是结构成员。  默认包装大小为 \/Zp8。  
  
 若要使用 `pack` 杂注为特定结构指定命令行上指定的包装以外的包装，请在结构的前面提供 `pack` 杂注，其中包装大小为 1、2、4、8 或 16。  若要恢复命令行上提供的包装，请指定不带参数的 `pack` 杂注。  
  
 位域默认为 Microsoft C 编译器的 **long** 大小。  基于类型的大小或 \/Zp\[*n*\] 大小（以较小者为准）对齐结构成员。  默认大小为 4。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [结构声明](../c-language/structure-declarations.md)