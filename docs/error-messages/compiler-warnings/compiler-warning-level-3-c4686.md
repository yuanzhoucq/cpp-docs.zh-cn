---
title: "编译器警告（等级 3）C4686 | Microsoft Docs"
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
  - "C4686"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4686"
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4686
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**“**   
 ***用户定义的类型* ”: 行为可能有更改，UDT 中的更改返回调用约定**  
  
 在返回类型中使用类模板专用化之前未定义它。  实例化该类的任何对象都将解决此 C4686 警告；也可以选择声明一个实例或访问一个成员 \(C\<int\>::anything\)。  
  
 此警告是为使 Visual C\+\+ .NET 2003 编译器符合 ISO C\+\+ 标准而生成的。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 代之以试用以下内容  
  
```  
// C4686.cpp  
// compile with: /W3  
#pragma warning (default : 4686)  
template <class T>  
class C;  
  
template <class T>  
C<T> f(T);  
  
template <class T>  
class C {};  
  
int main() {  
   f(1);   // C4686  
}  
  
template <class T>  
C<T> f(T) {  
   return C<int>();  
}  
```