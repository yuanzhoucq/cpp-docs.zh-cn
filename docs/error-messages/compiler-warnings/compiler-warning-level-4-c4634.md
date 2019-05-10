---
title: 编译器警告（等级 4）C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 7d0e2af13128a201d96aa905d85621e14441a673
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408200"
---
# <a name="compiler-warning-level-4-c4634"></a>编译器警告（等级 4）C4634

XML 文档注释：不能应用：原因

XML 文档标记不能应用于所有 C++ 构造。  例如，无法将文档注释添加到命名空间或模板中。

有关更多信息，请参见 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4634。

```
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>示例

下面的示例生成 C4634。

```
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```