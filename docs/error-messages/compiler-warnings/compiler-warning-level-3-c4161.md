---
title: "编译器警告（等级 3）C4161 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4161"
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 3）C4161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma pragma\(pop...\) : 出栈比入栈多  
  
 因为对于 ***pragma***，源代码中出栈比入栈多一个，堆栈可能无法正常工作。 若要避免此警告，请确保出栈数不超过入栈数。  
  
## 示例  
 下面的示例生成 C4161:  
  
```  
// C4161.cpp // compile with: /W3 /LD #pragma pack(push, id) #pragma pack(pop, id) #pragma pack(pop, id)   // C4161, an extra pop #pragma bss_seg(".my_data1") int j; #pragma bss_seg(push, stack1, ".my_data2") int l; #pragma bss_seg(pop, stack1) int m; #pragma bss_seg(pop, stack1)   // C4161  
```