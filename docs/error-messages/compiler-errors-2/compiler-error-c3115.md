---
title: 编译器错误 C3115
ms.date: 11/04/2016
f1_keywords:
- C3115
helpviewer_keywords:
- C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
ms.openlocfilehash: c03361f08ffd54396d307ed8c075a327c576d49b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760734"
---
# <a name="compiler-error-c3115"></a>编译器错误 C3115

"attribute"：在 "构造" 上不允许使用此特性

已将特性应用于不打算用于的构造。  有关详细信息，请参阅[属性的用法](../../windows/attributes/attributes-by-usage.md)。

## <a name="example"></a>示例

下面的示例生成 C3115。

```cpp
// C3115.cpp
// compile with: /c
#include <unknwn.h>
[module(name="xx")];

[object, helpstringdll(xx.dll), uuid("00000000-0000-0000-0000-000000000001")]   // C3115
// try the following line instead
// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI {
   HRESULT xx();
};
```
