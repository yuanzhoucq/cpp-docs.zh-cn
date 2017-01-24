---
title: "编译器错误 C3815 | Microsoft Docs"
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
  - "C3815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3815"
ms.assetid: c5a3b404-6341-4fd3-92af-152b404c4dde
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

方法“get\_accessor”的返回类型必须与 setter 的最后一个参数的类型匹配  
  
 声明[属性](../../misc/property.md)时，`get_accessor` 方法的返回值必须与 set 访问器方法声明中的最后一个参数匹配。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C3815 错误。  
  
 下面的示例生成 C3815：  
  
```  
// C3815.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc class X  
{  
public:  
   __property char get_N()  
   // try the following line instead  
   // __property int get_N()  
   {  
      return m_val;  
   }  
  
   __property void set_N( int val)  
   {  
      m_val = val;  
   }  
  
private:  
   int m_val;  
};   // C3815  
```  
  
 下面的示例演示如何重载属性，以使 getter 的返回类型不与 setter 的最后一个参数匹配。  
  
```  
// C3815b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
public __gc class MyClass {  
public:  
// 1st property:  
   __property System::Int32 get_p1();  
   __property void set_p1(System::Int32 i);  
  
// 2nd property (only setter):  
   __property void set_p1(System::Int32* i);  
  
};  
```