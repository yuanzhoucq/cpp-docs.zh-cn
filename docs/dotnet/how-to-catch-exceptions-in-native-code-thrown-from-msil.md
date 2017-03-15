---
title: "如何：在本机代码中捕捉从 MSIL 引发的异常 | Microsoft Docs"
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
  - "捕捉异常, 从 MSIL 引发"
  - "异常, 捕捉"
  - "MSIL, 在本机代码中捕捉异常"
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：在本机代码中捕捉从 MSIL 引发的异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本机代码中，则可以捕获从 MSIL 的本机 C\+\+ 异常。可以捕获具有 `__try` 和 `__except`的 CLR 异常。  
  
 有关更多信息，请参见[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)和[C\+\+ 异常处理](../cpp/cpp-exception-handling.md)。  
  
## 示例  
 下面的示例定义带有两函数的本机异常，引发异常的 MSIL 和另一模块。  
  
```  
// catch_MSIL_in_native.cpp  
// compile with: /clr /c  
void Test() {  
   throw ("error");  
}  
  
void Test2() {  
   throw (gcnew System::Exception("error2"));  
}  
```  
  
## 示例  
 下面的示例定义捕获本机和 MSIL 异常的模块。  
  
```  
// catch_MSIL_in_native_2.cpp  
// compile with: /clr catch_MSIL_in_native.obj  
#include <iostream>  
using namespace std;  
void Test();  
void Test2();  
  
void Func() {  
   // catch any exception from MSIL  
   // should not catch Visual C++ exceptions like this  
   // runtime may not destroy the object thrown  
   __try {  
      Test2();  
   }  
   __except(1) {  
      cout << "caught an exception" << endl;  
   }  
  
}  
  
int main() {  
   // catch native C++ exception from MSIL  
   try {  
      Test();  
   }  
   catch(char * S) {  
      cout << S << endl;  
   }  
   Func();  
}  
```  
  
  **错误**  
**捕获异常**   
## 请参阅  
 [异常处理](../windows/exception-handling-cpp-component-extensions.md)