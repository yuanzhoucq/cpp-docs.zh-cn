---
title: 编译器错误 C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 185bd35bb732f592c75912fe69d4491252fe9d0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476110"
---
# <a name="compiler-error-c3468"></a>编译器错误 C3468

“type”: 只能将类型转发到程序集:

“`file`”不是程序集

只能转发程序集中的类型。

有关详细信息，请参阅[类型转发 (C + + CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例创建一个模块。

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>示例

下面的示例生成 C3468。

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```