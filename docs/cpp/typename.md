---
title: 类型名称 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77e3cc6f9691cf071a420ee2659c713f9e28036f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061586"
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