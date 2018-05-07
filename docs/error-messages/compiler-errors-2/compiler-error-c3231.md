---
title: 编译器错误 C3231 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4925055caac0f3d26922eebf6a043ad51c83efa2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3231"></a>编译器错误 C3231
arg： 模板类型参数不能使用泛型类型参数  
  
 模板在编译时实例化，而泛型在运行时实例化。 因此，不能生成可调用模板的泛型代码，因为当泛型类型在最后才已知时，模板不能在运行时实例化。  
  
 下面的示例生成 C3231:  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```