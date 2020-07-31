---
title: 编译器错误 C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: fdc129be94fce3f97eca988d8080e9d01fd48248
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221089"
---
# <a name="compiler-error-c3384"></a>编译器错误 C3384

“type_parameter”: 值约束与 ref 约束互相排斥

不能将泛型类型约束为 **`value class`** 和 **`ref class`** 。

有关详细信息，请参阅[泛型类型参数的约束（c + +/cli）](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 。

## <a name="example"></a>示例

下面的示例生成 C3384。

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```
