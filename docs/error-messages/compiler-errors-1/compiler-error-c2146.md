---
title: "编译器错误 C2146 | Microsoft Docs"
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
  - "C2146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2146"
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 标识符“identifier”前缺少“token”  
  
 编译器需要的是 `token`，找到的却是 `identifier`。可能的原因：  
  
1.  拼写或大小写错误。  
  
2.  在该标识符的声明中缺少类型说明符。  
  
 排字错误可能引起该错误。  错误 [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) 通常在该错误之前发生。  
  
## 示例  
 下面的示例生成 C2146。  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## 示例  
 为 Visual Studio .NET 2003 执行的编译器一致性工作也可能导致此错误：缺少 `typename` 关键字。  
  
 下面的示例可以在 Visual Studio .NET 2002 中成功编译，但在 Visual Studio .NET 2003 中无法成功编译：  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## 示例  
 也可能由于为 Visual Studio .NET 2003 进行的编译器一致性工作显示此错误：显式专用化不再从主模板查找模板参数。  
  
 在显式专用化中不允许从主模板使用 `T`。  为使代码在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中有效，用显式指定的类型在专用化中替代模板参数的所有实例。  
  
 可以在 Visual Studio .NET 中成功编译下面的示例，但在 Visual Studio .NET 2003 中则无法成功编译：  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```