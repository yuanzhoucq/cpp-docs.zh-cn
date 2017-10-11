---
title: "编译器错误 C3902 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3902
dev_langs:
- C++
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ae92650865b4f62fc92c845764bcbfc81db714d1
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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
