---
title: 密封虚函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85f4775025d3661fdfbf8967b310fb733f452b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164591"
---
# <a name="sealing-a-virtual-function"></a>密封虚函数
密封虚函数的语法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 `__sealed`关键字使用托管扩展中，来修改任一引用类型，不允许从它的后续派生 (请参阅[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md))，或修改虚拟函数，不允许后续重写的派生类中的方法。 例如：  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 在此示例中，`derived::f()`重写`base::f()`实例基于函数原型为完全匹配。 `__sealed`关键字表示从派生类继承的后续类不能提供的重写`derived::f()`。  
  
 在新语法中，`sealed`放置后面签名，而不是出现在实际函数原型之前, 的任意位置 （这在以前是允许在被允许。 此外，使用`sealed`要求的显式使用`virtual`以及关键字。 正确转换，即`derived`、 更高版本，如下所述：  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 缺少`virtual`此实例中的关键字会导致出现错误。 在新的语法中，上下文关键字`abstract`可代替了`=0`以指示一个纯虚拟函数。 托管扩展中不支持这样做。 例如：  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 可以重写为  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>请参阅  
 [在类或接口中的成员声明 (C + + /cli CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)