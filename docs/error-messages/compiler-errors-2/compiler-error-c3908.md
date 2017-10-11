---
title: "编译器错误 C3908 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 05b4f772c5c1acf8da9247f27fa92a947a0ffc5b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3908"></a>编译器错误 C3908
访问级别限制性比 construct  
  
 属性访问器方法 （get 或 set） 不能具有限制性较弱访问权限要比属性本身上指定的访问权限。  同样，对于事件访问器方法。  
  
 有关详细信息，请参阅[属性](../../windows/property-cpp-component-extensions.md)和[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下面的示例生成 C3908:  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```
