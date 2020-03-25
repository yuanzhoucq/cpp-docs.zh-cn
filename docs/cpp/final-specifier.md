---
title: final 说明符
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 93e8d9b0b445d1120ec15911eb763ae1d7d2d359
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188647"
---
# <a name="final-specifier"></a>final 说明符

您可以使用**final**关键字来指定不能在派生类中重写的虚函数。 您还可以使用它指定无法继承的类。

## <a name="syntax"></a>语法

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>备注

**final**是上下文相关的，只有在函数声明或类名后使用时才具有特殊意义;否则，它不是保留的关键字。

当在类声明中使用**final**时，`base-classes` 是声明的可选部分。

## <a name="example"></a>示例

下面的示例使用**final**关键字指定无法重写虚函数。

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

有关如何指定可以重写成员函数的信息，请参阅[Override 说明符](../cpp/override-specifier.md)。

下一个示例使用**final**关键字指定无法继承类。

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[override 说明符](../cpp/override-specifier.md)
