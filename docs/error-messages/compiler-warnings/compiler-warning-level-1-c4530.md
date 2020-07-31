---
title: 编译器警告（等级 1）C4530
description: Microsoft c + + 编译器警告 C4530 的参考指南。
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: fe0a2b4c8eb881327f3e59d66e7e6941f0a2cad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230657"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530

> 使用了 c + + 异常处理程序，但未启用展开语义。 指定/EHsc

此代码使用 c + + 异常处理[，但不](../../build/reference/eh-exception-handling-model.md)包括在编译器选项中。

## <a name="remarks"></a>备注

编译器需要 **`/EHsc`** 选项来构建遵循 c + + 标准的 c + + 代码，以便进行异常处理。 标准 c + +*展开语义*指定在引发异常的位置和捕获异常的位置之间构造的对象和堆栈帧必须销毁，并恢复其资源。 此过程称为*展开堆栈*。

**`/EHsc`** 选项指示编译器生成代码，该代码在异常通过包含堆栈帧时对自动存储对象调用析构函数。 *自动存储*对象是在堆栈上分配的对象，例如局部变量。 它称为自动存储，因为它是在调用函数时自动分配的，并在返回时自动释放。 *堆栈帧*是调用函数时放置在堆栈上的数据及其自动存储。

当引发异常时，它可能会在捕获到多个堆栈帧后经历。 必须展开这些堆栈帧，因为异常通过反向调用顺序传递它们。 必须销毁每个堆栈帧中的自动存储对象，以完全恢复其资源。 它是在函数正常返回时自动发生的相同析构和恢复过程。

如果 **`/EHsc`** 未启用该选项，则引发函数与捕获异常的函数之间的堆栈帧中的自动存储对象不会被销毁。 仅在或块中创建的自动存储对象 **`try`** **`catch`** 被销毁，这可能会导致重大的资源泄漏和其他意外行为。

如果可执行文件中不可能引发异常，则可以安全地忽略此警告。 某些代码可能需要其他异常处理选项。 有关详细信息，请参阅[/EH](../../build/reference/eh-exception-handling-model.md)。

## <a name="example"></a>示例

下面的示例生成 C4530：

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

编译示例 **`/EHsc`** 以解决此警告。
