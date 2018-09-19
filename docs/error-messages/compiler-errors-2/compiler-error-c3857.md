---
title: 编译器错误 C3857 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3857
dev_langs:
- C++
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279ed343b57380df9db9180aa475e4d77ddf5ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097596"
---
# <a name="compiler-error-c3857"></a>编译器错误 C3857

type： 不允许多个类型参数列表

为相同的类型，这不允许指定多个模板或泛型。

下面的示例生成 C3857:

```
// C3857.cpp
template <class T, class TT>
template <class T2>    // C3857
struct B {};
```

可能的解决方法：

```
// C3857b.cpp
// compile with: /c
template <class T, class TT, class T2>
struct B {};
```

使用泛型时，也可能发生 C3857:

```
// C3857c.cpp
// compile with: /clr
generic <typename T>
generic <typename U>
ref class GC;   // C3857
```

可能的解决方法：

```
// C3857d.cpp
// compile with: /clr /c
generic <typename U>
ref class GC;
```