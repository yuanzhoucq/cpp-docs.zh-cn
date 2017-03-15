---
title: "未经处理的 C++ 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 未经处理的异常"
  - "catch 关键字 [C++], 未找到处理程序"
  - "事件处理程序, 未经处理的异常"
  - "异常, 未处理的"
  - "未经处理的异常"
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 未经处理的 C++ 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果无法找到当前异常的匹配处理程序（或省略号 **catch** 处理程序），则调用预定义的 `terminate` 运行时函数。（您也可以在任意处理程序中显式调用 `terminate`。）`terminate` 的默认操作是调用 `abort`。  如果您希望 `terminate` 在退出应用程序之前调用程序中的某些其他函数，则用被调用函数的名称作为其单个参数调用 `set_terminate` 函数。  您可以在程序的任何点调用 `set_terminate`。  `terminate` 例程总是调用指定为 `set_terminate` 的参数的最后一个函数。  
  
## 示例  
 以下示例引发 `char *` 异常，但不包含用于捕获类型 `char *` 的异常的指定处理程序。  对 `set_terminate` 的调用指示 `terminate` 调用 `term_func`。  
  
```  
// exceptions_Unhandled_Exceptions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void term_func() {  
   cout << "term_func was called by terminate." << endl;  
   exit( -1 );  
}  
int main() {  
   try  
   {  
      set_terminate( term_func );  
      throw "Out of memory!"; // No catch handler for this exception  
   }  
   catch( int )  
   {  
      cout << "Integer exception raised." << endl;  
   }  
   return 0;  
}  
```  
  
## Output  
  
```  
term_func was called by terminate.  
```  
  
 `term_func` 函数最好是通过调用 `exit` 来终止程序或当前线程。  如果它没有这样做，而是返回到其调用方，则调用 `abort`。  
  
## 请参阅  
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)