---
title: 接口成员的显式重写 |Microsoft Docs
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
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409020"
---
# <a name="explicit-override-of-an-interface-member"></a>接口成员的显式重写

声明类中接口成员的显式重写的语法已从托管扩展中的 c + + 更改为 Visual c + +。

你通常想要提供两个接口成员的类中实现接口的一个时通过接口句柄，操作类对象时使用，通过类接口中使用时将使用类对象的一个实例。 例如：

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

在托管扩展中为此，我们提供的方法的名称限定的接口名称与接口方法的显式声明。 特定于类的实例是不合格。 这不需要向下转换的返回值`Clone`，在此示例中，通过的实例显式调用时`R`。

在新语法中，重写的通用机制引入了替换的托管扩展语法。 我们的示例将重新编写，如下所示：

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

此修订版本要求显式重写该接口成员为给定的类中的唯一名称。 在这里，我提供了有些笨拙的名称`InterfaceClone`。 行为仍然是相同 – 通过调用`ICloneable`接口调用已重命名`InterfaceClone`，而类型的对象通过调用`R`调用第二个`Clone`实例。

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)