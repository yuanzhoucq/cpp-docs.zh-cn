---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 7dbe4381465036bdd102b3be753a18451886a3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166251"
---
# <a name="typename"></a>typename

模板定义中提供给编译器的提示无法识别的标识符是一种类型。 在模板参数列表，用于指定类型参数。

## <a name="syntax"></a>语法

```
typename identifier;
```

## <a name="remarks"></a>备注

如果在模板定义中的名称是依赖于模板自变量; 一个限定的名称，必须使用此关键字如果限定的名称不是依赖，是可选的。 有关详细信息，请参阅[模板和名称解析](../cpp/templates-and-name-resolution.md)。

**typename**可由任意位置中的模板声明或定义的任何类型。 不允许在基类列表中使用该关键字，除非将它用作模板基类的模板自变量。

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**Typename**关键字也可用来代替**类**模板参数列表。 例如，以下语句在语义上等效:

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

## <a name="see-also"></a>请参阅

[模板](../cpp/templates-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)