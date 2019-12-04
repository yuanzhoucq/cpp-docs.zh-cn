---
title: 编译器错误 C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: f3ce849113b0fc21a192f748bc46fc35be48880d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749628"
---
# <a name="compiler-error-c3076"></a>编译器错误 C3076

"instance"：不能在本机类型中嵌入引用类型 "type" 的实例

本机类型不能包含 CLR 类型的实例。

有关详细信息，请参阅[ C++引用类型的堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>示例

下面的示例生成 C3076。

```cpp
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```
