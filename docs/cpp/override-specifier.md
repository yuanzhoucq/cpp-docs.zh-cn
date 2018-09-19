---
title: 重写说明符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 596580bdd4cb7c5610e7cb68341fba4a3da981ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106137"
---
# <a name="override-specifier"></a>override 说明符

可以使用**重写**关键字来指定重写基类中的虚函数的函数的成员。

## <a name="syntax"></a>语法

```
function-declaration override;
```

## <a name="remarks"></a>备注

**重写**是上下文相关和具有特殊含义仅当成员函数声明后使用它; 否则，而不是保留的关键字。

## <a name="example"></a>示例

使用**重写**以帮助防止在代码中的意外的继承行为。 下面的示例演示的位置，而无需使用**重写**，派生类的成员函数的行为可能不适用。 编译器不会发出此代码的任何错误。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

当你使用**重写**，编译器将生成错误而不是以无提示方式创建新的成员函数。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

若要指定函数不能重写和不能继承的类，请使用[最终](../cpp/final-specifier.md)关键字。

## <a name="see-also"></a>请参阅

[final 说明符](../cpp/final-specifier.md)<br/>
[关键字](../cpp/keywords-cpp.md)