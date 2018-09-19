---
title: 编译器警告 （等级 C4634 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4634
dev_langs:
- C++
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fe89eaffda80ab40efedc4facf75929d07a7537
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034910"
---
# <a name="compiler-warning-level-4-c4634"></a>编译器警告（等级 4）C4634

XML 文档注释：不能应用：原因

XML 文档标记不能应用于所有 C++ 构造。  例如，无法将文档注释添加到命名空间或模板中。

有关更多信息，请参见 [XML Documentation](../../ide/xml-documentation-visual-cpp.md)。

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