---
title: "Catch 块的计算方式 (C++) | Microsoft Docs"
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
  - "C++ 异常处理, catch 处理程序"
  - "catch 关键字 [C++], catch 处理程序的类型"
  - "异常处理, 捕捉和删除异常"
  - "try-catch 关键字 [C++], 可捕获的类型"
  - "类型 [C++], 异常处理"
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Catch 块的计算方式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虽然通常建议您引发派生自 std::exception 的类型，但 C\+\+ 使您能够引发任何类型的异常。  可以通过指定与引发的异常相同的类型的 **catch** 处理程序或通过可捕获任何类型的异常的处理程序来捕获 C\+\+ 异常。  
  
 如果引发的异常的类型是类，它还具有基类（或类），则它可由接受异常类型的基类和对异常类型的基的引用的处理程序捕获。  请注意，当异常由引用捕获时，会将其绑定到实际引发的异常对象；否则，它将为一个副本（与函数的参数大致相同）。  
  
 引发异常时，将由以下类型的 **catch** 处理程序捕获该异常：  
  
-   可以接受任何类型的处理程序（使用省略号语法）。  
  
-   接受与异常对象相同的类型的处理程序；由于它是副本，因此 **const** 和 `volatile` 修饰符将被忽略。  
  
-   接受对与异常对象相同的类型的引用的处理程序。  
  
-   接受对与异常对象相同的类型的 **const** 或 `volatile` 形式的引用的处理程序。  
  
-   接受与异常对象相同的类型的基类的处理程序；由于它是副本，因此 **const** 和 `volatile` 修饰符将被忽略。  基类的 **catch** 处理程序不得位于派生类的 **catch** 处理程序的前面。  
  
-   接受对与异常对象相同的类型的基类的引用的处理程序。  
  
-   接受与异常对象相同的类型的基类的 **const** 或 `volatile` 形式的引用的处理程序。  
  
-   接受可通过标准指针转换规则将引发的指针对象转换为的指针的处理程序。  
  
 **catch** 处理程序出现的顺序是有意义的，因为给定 **try** 块的处理程序按它们的出现顺序进行检查。  例如，将基类的处理程序放置在派生类的处理程序的前面是错误的。    找到一个匹配的 **catch** 处理程序后，不会检查后续处理程序。  因此，省略号 **catch** 处理程序必须是其 **try** 块的最后一个处理程序。  例如：  
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 在此示例中，省略号 **catch** 处理程序是已检查的唯一处理程序。  
  
## 请参阅  
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)