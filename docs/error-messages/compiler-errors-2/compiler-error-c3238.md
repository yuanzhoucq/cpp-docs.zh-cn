---
title: 编译器错误 C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 6f60a9abbc5702c1a0d14d0f894c9b1684378c3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759355"
---
# <a name="compiler-error-c3238"></a>编译器错误 C3238

“type”：已将某个同名类型转发到程序集“assembly”

通过在引用的程序集中类型转发语法，已在客户端应用程序中定义的类型也被定义了。 两种类型均不能在应用程序的范围内定义。

有关详细信息，请参阅[类型转发（C++/cli）](../../extensions/type-forwarding-cpp-cli.md) 。

## <a name="example"></a>示例

下面的示例创建了一个包含从另一个程序集已转发的类型的程序集。

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>示例

下面的示例创建用来包含该类型定义的程序集，但不仅仅包含类型转发语法。

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>示例

以下示例生成 C3238。

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
