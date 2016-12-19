---
title: "编译器错误 C2993 | Microsoft Docs"
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
  - "C2993"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2993"
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2993
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 非类型模板参数“parameter”的类型非法  
  
 不能使用结构参数或联合参数声明模板。  应使用指针将结构和联合作为模板参数来传递。  
  
 下面的示例生成 C2993：  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 也将由于在 Visual Studio .NET 2003 中进行的编译器一致性工作生成此错误：不再允许浮点非类型模板参数。  C\+\+ 标准不允许浮点非类型模板参数。  
  
 如果它是函数模板，则使用函数参数来传入浮点非类型模板参数（此代码将在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中有效）。  如果它是类模板，则没有简单的变通方法。  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```