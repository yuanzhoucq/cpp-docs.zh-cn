---
title: override 说明符
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188475"
---
# <a name="override-specifier"></a>override 说明符

您可以使用**override**关键字来指定在基类中重写虚函数的成员函数。

## <a name="syntax"></a>语法

```
function-declaration override;
```

## <a name="remarks"></a>备注

**重写**是上下文相关的，只有在成员函数声明后使用时才具有特殊意义;否则，它不是保留的关键字。

## <a name="example"></a>示例

使用**override**有助于防止代码中出现意外的继承行为。 下面的示例演示在不使用**重写**的情况下，可能尚未设计派生类的成员函数行为。 编译器不会发出此代码的任何错误。

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

使用**override**时，编译器会生成错误，而不是以无提示方式创建新的成员函数。

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

若要指定不能重写函数以及无法继承类，请使用[final](../cpp/final-specifier.md)关键字。

## <a name="see-also"></a>另请参阅

[final 说明符](../cpp/final-specifier.md)<br/>
[关键字](../cpp/keywords-cpp.md)
