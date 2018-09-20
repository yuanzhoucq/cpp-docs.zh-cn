---
title: 密封虚函数 |Microsoft Docs
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
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385178"
---
# <a name="sealing-a-virtual-function"></a>密封虚函数

密封虚函数的语法已从托管扩展中的 c + + 更改为 Visual c + +。

`__sealed`关键字用于托管扩展中，来修改为引用类型，不允许后续派生 (请参阅[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md))，或修改虚拟函数，不允许后续重写的派生类中的方法。 例如：

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

在此示例中，`derived::f()`重写`base::f()`实例基于完全匹配的函数原型。 `__sealed`关键字表示从派生类继承的后续类不能提供的重写`derived::f()`。

在新语法中，`sealed`后该签名，而不是允许显示实际函数原型中，之前的任意位置 （这在以前是允许放置。 此外，使用`sealed`需要显式使用`virtual`以及关键字。 它是正确的转换`derived`、 更高版本，如下所示：

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

如果没有`virtual`此实例中的关键字会导致出现错误。 在新的语法中，上下文关键字`abstract`可用来代替`=0`以指示纯虚拟函数。 托管扩展中不支持这样做。 例如：

```
__gc class base { public: virtual void f()=0; };
```

可以重写为

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)