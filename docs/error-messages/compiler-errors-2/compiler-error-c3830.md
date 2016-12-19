---
title: "编译器错误 C3830 | Microsoft Docs"
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
  - "C3830"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3830"
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3830
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”: 无法从“type2”继承，值类型只能从接口类继承  
  
 值类型不能继承基类。有关详细信息，请参阅[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下面的示例生成 C3830：  
  
```  
// C3830a.cpp  
// compile with: /clr /c  
public value struct MyStruct4 {  
   int i;  
};  
  
public value class MyClass : public MyStruct4 {};   // C3830  
  
// OK  
public interface struct MyInterface4 {  
   void i();  
};  
  
public value class MyClass2 : public MyInterface4 {  
public:  
   virtual void i(){}  
};  
```  
  
 **C\+\+ 托管扩展**  
  
 `__value` 类型不能继承基类。  
  
 下面的示例生成 C3830：  
  
```  
// C3830b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__value struct v : public System::Object {};   // C3830  
__value struct w {};   // OK  
```