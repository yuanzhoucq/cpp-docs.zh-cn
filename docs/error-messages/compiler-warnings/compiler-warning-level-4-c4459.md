---
title: 编译器警告 （等级 C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: 0cbab7c7cca1fc88bb99210262be45c56b6be7a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391421"
---
# <a name="compiler-warning-level-4-c4459"></a>编译器警告 （等级 C4459

> 声明*标识符*隐藏了全局声明

声明*标识符*在本地作用域中隐藏了相同名称的声明*标识符*全局作用域中。 此警告，可以了解到引用*标识符*在此范围内解析为本地声明的版本中，不是全局版本，可能会也可能不是你的意图。 通常情况下，我们建议你尽量减少使用的全局变量作为良好工程做法。 为了尽量减少污染全局命名空间，我们建议使用已命名的命名空间的全局变量。

此警告是 Visual Studio 2015 中，在视觉对象中的新增功能C++编译器版本 18.00。 若要禁止显示警告从该版本的编译器或更高版本时迁移你的代码，请使用[/wv:18](../../build/reference/compiler-option-warning-level.md)编译器选项。

## <a name="example"></a>示例

下面的示例生成 C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

若要解决此问题的一种方法是创建用于在全局命名空间，但不是使用`using`指令将该命名空间引入作用域，因此必须使用明确的所有引用限定的名称：

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
