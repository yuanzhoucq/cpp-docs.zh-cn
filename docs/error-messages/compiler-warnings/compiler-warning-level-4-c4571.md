---
title: "编译器警告（等级 4）C4571 | Microsoft Docs"
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
  - "C4571"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4571"
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4571
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

信息: 自 Visual C\+\+ 7.1 之后，catch\(...\) 语义发生了变化；不再捕获结构化的异常\(SEH\)  
  
 使用 **\/EHs** 编译时，将针对每个 catch\(...\) 块生成 C4571。  
  
 使用 **\/EHs** 编译时，catch\(...\) 块将不捕获结构化异常（例如，被零除、null 指针）；catch\(...\) 块仅捕获显式引发的 C\+\+ 异常。有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 默认情况下关闭此警告。打开此警告可确保在使用 **\/EHs** 编译时，catch \(...\) 块不会捕获结构化异常。有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 可以通过以下方式之一来解决 C4571，  
  
-   如果仍希望 catch\(...\) 块捕获结构化异常，请使用 **\/EHa** 进行编译。  
  
-   如果不希望 catch\(...\) 块捕获结构化异常，但是仍希望使用 catch\(...\) 块，请不要启用 C4571。仍然可以使用结构化异常处理关键字（**\_\_try**、**\_\_except** 和 **\_\_finally**）来捕获结构化异常。但要记住，在使用 **\/EHs** 编译时，只有在引发 C\+\+ 异常而不是发生 SEH 异常时才调用析构函数。  
  
-   用特定 C\+\+ 异常的 catch 块代替 catch\(...\) 块，并可以选择在 C\+\+ 异常处理处添加结构化异常处理（**\_\_try**、**\_\_except** 和 **\_\_finally**）。有关更多信息，请参见[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 有关更多信息，请参见[\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
## 示例  
 下面的示例生成 C4571。  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```