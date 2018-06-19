---
title: 编译器错误 C3902 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3902
dev_langs:
- C++
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0430ab95ae4884c420a3f7153fbbbbc4f7931675
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278192"
---
# <a name="compiler-error-c3902"></a>编译器错误 C3902
accessor： 最后一个参数类型必须是 type  
  
 至少一个 set 方法的最后一个参数的类型必须匹配的属性类型。 有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。  
  
 下面的示例生成 C3902:  
  
```  
// C3902.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String ^Name {  
      void set(int);   // C3902  
      // try the following line instead  
      // void set(String^){}  
   }  
  
   property double values[int,int] {  
      void set(int, int, float);   // C3902  
      // try the following line instead  
      // void set(int, int, double){}  
   }  
};  
```