---
title: 接口成员的显式重写 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 811112d2721edccede6c7b4a278189fdec874523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110432"
---
# <a name="explicit-override-of-an-interface-member"></a>接口成员的显式重写
声明一个类中接口成员的显式重写的语法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 你通常想要提供两个接口成员的类中实现的接口的一个时通过接口句柄，操作类对象时使用，使用时将使用类对象是通过类接口的一个实例。 例如：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 在托管扩展中执行此操作通过用接口的名称限定的方法的名称与提供的接口方法的显式声明。 特定于类的实例是不合格的。 这消除了向下转换需求的返回值`Clone`，在此示例中，通过的实例的显式调用时`R`。  
  
 在新语法中，常规的重写机制引入了替换的托管扩展语法。 我们的示例将被重写，如下所示：  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 此修订版本，需要显式重写的接口成员指定类中唯一的名称。 在这里，我已提供的繁琐名称`InterfaceClone`。 行为都是一样的-通过调用`ICloneable`接口调用重命名`InterfaceClone`，而通过类型的对象的调用`R`调用第二个`Clone`实例。  
  
## <a name="see-also"></a>请参阅  
 [在类或接口中的成员声明 (C + + /cli CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [显式重写](../windows/explicit-overrides-cpp-component-extensions.md)