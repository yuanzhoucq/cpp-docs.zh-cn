---
title: "函数内联问题 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob1 C++ 编译器选项"
  - "/Ob2 C++ 编译器选项"
  - "函数内联问题"
  - "内联函数, 问题"
  - "-Ob1 C++ 编译器选项"
  - "-Ob2 C++ 编译器选项"
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 函数内联问题
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果使用函数内联，必须：  
  
-   在包括的头文件中实现内联函数。  
  
-   在头文件中打开内联。  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 然后，  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 如果使用 `#pragma inline_depth` 编译器指令，请确保设置了大于或等于 2 的值。  值为零将关闭内联。  同时确保使用 **\/Ob1** 或 **\/Ob2** 编译器选项。  
  
 在不同模块上混合内联和非内联编译选项有时会导致问题。  如果创建 C\+\+ 库时打开了函数内联（[\/Ob1](../../build/reference/ob-inline-function-expansion.md) 或 [\/Ob2](../../build/reference/ob-inline-function-expansion.md)），但描述函数的相应头文件的内联是关闭的（没有选项），将得到错误 LNK2001。  函数不从头文件内联到代码中，但由于它们不在库文件中，因此没有解析引用的地址。  
  
 同样，如果项目使用函数内联，但在 .cpp 文件（而非头文件）中定义函数，也会得到 LNK2019。  头文件包含在任何被认为合适的位置，但只有在 .cpp 文件通过编译器时函数才内联；因此当函数用于其他模块时，链接器将函数看成无法解析的外部对象。  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 然后，  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 然后，  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## 请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)