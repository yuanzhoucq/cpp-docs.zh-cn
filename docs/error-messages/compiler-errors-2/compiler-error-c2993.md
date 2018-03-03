---
title: "编译器错误 C2993 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3715e2183c8194fe7bcf2613cbee3a0052588385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2993"></a>编译器错误 C2993
identifier： 非类型模板参数 parameter 的非法类型  
  
 不能声明具有结构或联合的自变量的模板。 使用指针作为模板参数传递结构和联合。  
  
 下面的示例生成 C2993:  
  
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
  
 此错误还将导致在 Visual Studio.NET 2003年中完成的编译器一致性工作： 浮点不再允许非类型模板参数。 C + + 标准不允许浮点非类型模板参数。  
  
 如果它是函数模板，使用要在浮点中传递函数自变量将点 （此代码将在 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中有效） 的非类型模板参数。 如果它是类模板，则没有简单的解决方法。  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```