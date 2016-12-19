---
title: "编译器警告（等级 4）C4701 | Microsoft Docs"
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
  - "C4701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4701"
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用未初始化的潜在局部变量“name”  
  
 局部指针变量 *name* 可能在没有分配值的情况下被使用。  这可能导致不可预知的结果。  
  
## 示例  
 下面的代码生成 C4701 and C4703。  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
  **c:\\src\\test.cpp\(10\) :警告 C4701:使用潜在未初始化的局部变量“p”。**  
 **c:\\src\\test.cpp\(10\) :警告 C470３:使用潜在未初始化的局部指针变量“p”。** 若要更正此警告，请如下面的例子所示初始化变量：  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## 请参阅  
 [编译器警告（等级 4）C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [警告，\/sdl 和改进未初始化的变量检测](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)