---
title: "已弃用 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "deprecated"
  - "deprecated_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], 已弃用"
  - "deprecated __declspec 关键字"
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 已弃用 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

（Microsoft 专用）在下面所示的异常中，**deprecated** 声明提供与 [deprecated](../preprocessor/deprecated-c-cpp.md) 杂注相同的功能：  
  
-   利用 **deprecated** 声明，您可以将函数重载的特殊形式指定为已弃用，而杂注形式适用于函数名称的所有重载形式。  
  
-   利用 **deprecated** 声明，您可以指定在编译时显示的消息。  该消息的文本可以来自宏。  
  
-   只能使用 **deprecated** 杂注将宏标记为已弃用。  
  
 如果编译器遇到对已弃用的标识符的使用，则会引发 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 警告。  
  
## 示例  
 下面的示例演示在使用已弃用的函数时，如何将函数标记为已弃用以及如何指定在编译时将显示的消息。  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## 示例  
 下面的示例演示在使用已弃用的类时，如何将类标记为已弃用以及如何指定在编译时将显示的消息。  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)