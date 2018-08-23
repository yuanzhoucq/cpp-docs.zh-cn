---
title: 编译器错误 C3901 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3901
dev_langs:
- C++
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f35893eddea6aa37dbd11b84b14ea69aa9affbcb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269417"
---
# <a name="compiler-error-c3901"></a>编译器错误 C3901
accessor_function： 必须具有返回类型 type  
  
 至少一个 get 方法的返回类型必须匹配的属性类型。 有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。  
  
 下面的示例生成 C3901:  
  
```  
// C3901.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String^ Name {  
      void get();   // C3901  
      // try the following line instead  
      // String^ get();  
   };  
};  
  
ref class Y {  
   property double values[int, int] {  
      int get(int, int);   // C3901  
      // try the following line instead  
      // double get(int, int);  
   };  
};  
```