---
title: "编译器警告（等级 4）C4703 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4703"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4703"
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4703
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用潜在的未初始化的局部指针变量“名字”。  
  
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
 [编译器警告（等级 4）C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [警告，\/sdl 和改进未初始化的变量检测](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)