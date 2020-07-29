---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 62e8a2026babbfea3cd1583def05a03b4bc4a229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223507"
---
# <a name="typename"></a>typename

在模板定义中，向编译器提供未知标识符为类型的提示。 在模板参数列表中，用于指定一个类型参数。

## <a name="syntax"></a>语法

```
typename identifier;
```

## <a name="remarks"></a>备注

如果模板定义中的名称是依赖于模板参数的限定名，则必须使用此关键字;如果限定名不是依赖项，则此项是可选的。 有关详细信息，请参阅[模板和名称解析](../cpp/templates-and-name-resolution.md)。

**`typename`** 可由模板声明或定义中任意位置的任何类型使用。 不允许在基类列表中使用该关键字，除非将它用作模板基类的模板自变量。

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**`typename`** 关键字还可以用于替代 **`class`** 模板参数列表中的。 例如，下面的语句在语义上是等效的：

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>示例

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>另请参阅

[模板](../cpp/templates-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
