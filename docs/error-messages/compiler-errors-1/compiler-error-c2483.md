---
title: 编译器错误 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205109"
---
# <a name="compiler-error-c2483"></a>编译器错误 C2483

>"*identifier*"：包含构造函数或析构函数的对象不能声明为 "thread"

在 Visual Studio 2015 及更高版本中，此错误消息已过时。 在以前的版本中，无法使用构造函数或需要运行时计算的其他表达式初始化使用 `thread` 特性声明的变量。 初始化 `thread` 数据需要静态表达式。

## <a name="example"></a>示例

下面的示例在 Visual Studio 2013 及更早版本中生成 C2483。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>另请参阅

[thread](../../cpp/thread.md)
