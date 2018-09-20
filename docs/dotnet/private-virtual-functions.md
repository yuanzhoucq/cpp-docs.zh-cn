---
title: 私有虚函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0058d023268fa4d9ca5abe802ff45856e9855dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418068"
---
# <a name="private-virtual-functions"></a>私有虚函数

在派生类中处理私有虚函数的方式已从托管扩展中的 c + + 更改为 Visual c + +。

在托管扩展中，虚函数的访问级别不会不会限制其派生类中被重写的能力。 在新语法中，虚函数不能重写它无法访问的基类虚函数。 例如：

```
__gc class MyBaseClass {
   // inaccessible to a derived class
   virtual void g();
};

__gc class MyDerivedClass : public MyBaseClass {
public:
   // okay in Managed Extensions; g() overrides MyBaseClass::g()
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible
   void g();
};
```

没有实际映射到新的语法上设计此类。 只需必须使基类成员可访问-即，非私有内容。 继承的方法不需要具有相同的访问。 在此示例中，最低侵入性的更改是将 MyBaseClass 成员`protected`。 这种方式仍禁止对通过 MyBaseClass 方法的常规程序的访问。

```
ref class MyBaseClass {
protected:
   virtual void g();
};

ref class MyDerivedClass : MyBaseClass {
public:
   virtual void g() override;
};
```

请注意，缺少明确的`virtual`关键字在基的类中，在新语法中，会生成一条警告消息。

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
