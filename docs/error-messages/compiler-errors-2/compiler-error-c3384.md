---
title: 编译器错误 C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 059518462bd7a0463fd03fec6434acbbda7ee60a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756430"
---
# <a name="compiler-error-c3384"></a>编译器错误 C3384

“type_parameter”: 值约束与 ref 约束互相排斥

无法将泛型类型约束为 `value class` 和 `ref class`。

有关详细信息，请参阅[泛型C++类型参数（/Cli）的约束](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

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
