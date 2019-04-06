---
title: 编译器错误 C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d70bb6dac7cb43701b57f3821872e02ab31426dc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775617"
---
# <a name="compiler-error-c3238"></a>编译器错误 C3238

“type”：已将某个同名类型转发到程序集“assembly”

通过在引用的程序集中类型转发语法，已在客户端应用程序中定义的类型也被定义了。 两种类型均不能在应用程序的范围内定义。

请参阅[类型转发 (C + + CLI)](../../extensions/type-forwarding-cpp-cli.md)有关详细信息。

## <a name="example"></a>示例

下面的示例创建了一个包含从另一个程序集已转发的类型的程序集。

```
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>示例

下面的示例创建用来包含该类型定义的程序集，但不仅仅包含类型转发语法。

```
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>示例

以下示例生成 C3238。

```
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```