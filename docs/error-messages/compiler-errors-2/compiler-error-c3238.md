---
title: 编译器错误 C3238 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3238
dev_langs:
- C++
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8fa0daec5e799e0ea661aa56d1a84604114ec7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090381"
---
# <a name="compiler-error-c3238"></a>编译器错误 C3238

“type”：已将某个同名类型转发到程序集“assembly”

通过在引用的程序集中类型转发语法，已在客户端应用程序中定义的类型也被定义了。 两种类型均不能在应用程序的范围内定义。

请参阅[类型转发 (C + + CLI)](../../windows/type-forwarding-cpp-cli.md)有关详细信息。

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