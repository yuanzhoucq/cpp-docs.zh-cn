---
title: "编译器警告（等级 4）C4714 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4714"
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记为 \_\_forceinline 的函数“function”未内联  
  
 为内联展开选定了给定函数，但编译器没有执行内联。  
  
 虽然对编译器而言，`__forceinline` 是比 `__inline`更强的指示，但编译器仍然按照自己的判断执行内联，未使用试探法确定内联此函数的优点。  
  
 在某些情况下，编译器将会因为机理上的原因而不内联某个特定函数。  例如，编译器将不内联：  
  
-   会导致 SEH 和 C\+\+ EH 混合的函数。  
  
-   当 \-GX\/EHs\/EHa 打开时，由值传递的带复制构造对象的某些函数。  
  
-   当 \-GX\/EHs\/EHa 打开时，通过值返回不可展开的对象的函数。  
  
-   在不用 \-Og\/Ox\/O1\/O2 进行编译的情况下，具有内联程序集的函数。  
  
-   包含变量参数列表的函数。  
  
-   带 **try**（C\+\+ 异常处理）语句的函数。  
  
 下面的示例生成 C4714：  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```