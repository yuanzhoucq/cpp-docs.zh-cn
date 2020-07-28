---
title: 编译器警告（等级4） C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: d6d0a802f9f628145fbc5910aca805a5b01b94d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214368"
---
# <a name="compiler-warning-level-4-c4459"></a>编译器警告（等级4） C4459

> "*identifier*" 的声明隐藏了全局声明

局部范围内的*标识符*声明隐藏全局范围内具有相同名称的*标识符*的声明。 此警告使你知道，此范围内的*标识符*引用解析为本地声明的版本，而不是全局版本，这可能是你的意图，也可能不是。 通常，我们建议将全局变量的使用降到最低。 为了最大限度地减少全局命名空间的污染，我们建议为全局变量使用命名命名空间。

在 Microsoft c + + 编译器版本18.00 中，Visual Studio 2015 中新增了此警告。 若要在迁移代码时禁止显示编译器或更高版本的警告，请使用[/Wv： 18](../../build/reference/compiler-option-warning-level.md)编译器选项。

## <a name="example"></a>示例

下面的示例生成 C4459：

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

解决此问题的一种方法是为全局创建命名空间，但不使用 **`using`** 指令将命名空间引入作用域，因此所有引用都必须使用明确限定名称：

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
