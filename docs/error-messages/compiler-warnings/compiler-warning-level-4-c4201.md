---
title: "编译器警告（等级 4）C4201 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4201"
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 无名称的结构\/联合  
  
 在 Microsoft 扩展 \(\/Ze\) 下，可以将没有声明符的结构指定为另一个结构或联合的成员。  这些结构在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下生成错误。  
  
## 示例  
  
```  
// C4201.cpp  
// compile with: /W4  
struct S  
{  
   float y;  
   struct  
   {  
      int a, b, c;  // C4201  
   };  
} *p_s;  
  
int main()  
{  
}  
```