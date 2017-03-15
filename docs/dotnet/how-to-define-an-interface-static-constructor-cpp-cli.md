---
title: "如何：定义接口静态构造函数 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "构造函数 [C++]"
  - "接口静态构造函数"
  - "静态构造函数, interface"
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定义接口静态构造函数 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

接口可具有静态构造函数，可以将初始化静态数据成员。首次静态的接口成员，访问静态构造函数是最多调用一次和以前调用。  
  
 有关更多信息，请参见[如何：在类或结构中定义静态构造函数](../misc/how-to-define-static-constructors-in-a-class-or-struct.md)。  
  
## 示例  
  
```  
// mcppv2_interface_class2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct MyInterface {  
   static int i;  
   static void Test() {  
      Console::WriteLine(i);  
   }  
  
   static MyInterface() {   
      Console::WriteLine("in MyInterface static constructor");  
      i = 99;  
   }  
};  
  
ref class MyClass : public MyInterface {};  
  
int main() {  
   MyInterface::Test();  
   MyClass::MyInterface::Test();  
  
   MyInterface ^ mi = gcnew MyClass;  
   mi->Test();  
}  
```  
  
  **接口静态构造函数**  
**99**  
**99**  
**99**   
## 请参阅  
 [接口类](../windows/interface-class-cpp-component-extensions.md)