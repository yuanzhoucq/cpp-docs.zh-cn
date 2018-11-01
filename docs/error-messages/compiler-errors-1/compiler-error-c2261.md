---
title: 编译器错误 C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535741"
---
# <a name="compiler-error-c2261"></a>编译器错误 C2261

字符串： 程序集引用无效，无法解析

值不是有效的。

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 用于指定友元程序集。 例如，如果 a.dll 想要指定为友元程序集的 b.dll，则会指定 （在 a.dll): InternalsVisibleTo("b")。 然后，运行时允许 b.dll 访问 a.dll （除私有类型） 中的所有内容。

有关指定友元程序集时的正确语法的详细信息，请参阅[友元程序集 （c + +）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C2261。

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```