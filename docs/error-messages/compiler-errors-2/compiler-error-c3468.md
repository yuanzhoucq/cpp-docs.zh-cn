---
title: 编译器错误 C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e3870fa21e2b4a932937edd49091980406a5ff0d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777227"
---
# <a name="compiler-error-c3468"></a>编译器错误 C3468

“type”: 只能将类型转发到程序集:

“`file`”不是程序集

只能转发程序集中的类型。

有关详细信息，请参阅[类型转发 (C + + CLI)](../../extensions/type-forwarding-cpp-cli.md)。

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