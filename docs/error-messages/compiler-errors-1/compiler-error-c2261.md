---
title: 编译器错误 C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758770"
---
# <a name="compiler-error-c2261"></a>编译器错误 C2261

"string"：程序集引用无效且无法解析

值无效。

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 用于指定友元程序集。 例如，如果 .dll 要将 b. 指定为友元程序集，则需要指定（在 .dll 中）： InternalsVisibleTo （"b"）。 然后，运行时允许使用 .dll 访问 .dll 中的所有内容（私有类型除外）。

有关指定友元程序集时的正确语法的详细信息，请参阅[友元程序集C++（）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C2261。

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
