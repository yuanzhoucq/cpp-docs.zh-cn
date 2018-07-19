---
title: 编译器错误 C2993 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e25e70a9d16ee166772cf03ea1837afaf14cae29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242310"
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