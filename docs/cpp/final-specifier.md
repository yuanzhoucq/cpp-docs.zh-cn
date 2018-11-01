---
title: final 说明符
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588079"
---
# <a name="final-specifier"></a>final 说明符

可以使用**最终**关键字来指定不能在派生类中重写的虚函数。 您还可以使用它指定无法继承的类。

## <a name="syntax"></a>语法

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>备注

**最终**是上下文相关和具有特殊含义，仅当用于函数声明后或类名称; 否则为而不是保留的关键字。

当**最终**在类声明中使用`base-classes`是声明的可选部分。

## <a name="example"></a>示例

下面的示例使用**最终**关键字来指定，不能重写虚函数。

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

有关如何指定可以重写成员函数的信息，请参阅[重写说明符](../cpp/override-specifier.md)。

下面的示例使用**最终**关键字指定无法继承类。

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[override 说明符](../cpp/override-specifier.md)