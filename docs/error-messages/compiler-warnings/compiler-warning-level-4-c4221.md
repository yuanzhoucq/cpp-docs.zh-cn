---
title: "编译器警告（等级 4）C4221 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4221"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4221"
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4221
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 :“identifier”: 无法使用自动变量的地址进行初始化  
  
 在默认 Microsoft 扩展 \(\/Ze\) 下，可以用局部（自动）变量的地址初始化聚合类型（**array**、`struct` 或 **union**）。  
  
## 示例  
  
```  
// C4221.c  
// compile with: /W4  
struct S  
{  
   int *i;  
};  
  
void func()  
{  
   int j;  
   struct S s1 = { &j };   // C4221  
}  
  
int main()  
{  
}  
```  
  
 此类初始化在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下无效。