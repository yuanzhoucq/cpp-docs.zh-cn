---
title: 编译器警告（等级 1）C4530
description: Microsoft C++编译器警告 C4530 的参考指南。
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369782"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530

> C++使用异常处理程序，但未启用展开语义。 指定 /EHsc

代码使用C++异常处理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)不包括在编译器选项中。

## <a name="remarks"></a>备注

编译器需要**`/EHsc`** C++代码生成遵循C++异常处理标准的代码的选项。 标准C++*展开语义*指定必须在引发异常的位置和捕获异常的位置之间构造的对象和堆栈帧，并恢复其资源。 此过程称为*展开堆栈*。

该**`/EHsc`** 选项告诉编译器生成代码，当异常通过包含堆栈帧时，在自动存储对象上调用析构函数。 *自动存储*对象是在堆栈上分配的对象，如局部变量。 它被称为自动存储，因为它在调用函数时自动分配，并在返回时自动释放。 *堆栈帧*是调用函数时放置在堆栈上的数据及其自动存储。

引发异常时，它可能会在捕获之前通过多个堆栈帧。 当异常以反向调用顺序通过它们时，必须解开这些堆栈帧。 必须销毁每个堆栈帧中的自动存储对象，以便干净地恢复其资源。 当函数正常返回时，它会自动发生相同的销毁和恢复过程。

未启用**`/EHsc`** 该选项时，在引发函数和捕获异常的函数之间的堆栈帧中的自动存储对象不会被销毁。 只有**尝试**或**捕获**块中创建的自动存储对象才会被销毁，这可能导致严重的资源泄漏和其他意外行为。

如果无法在可执行文件中引发异常，则可以安全地忽略此警告。 某些代码可能需要其他异常处理选项。 有关详细信息，请参阅[/EH](../../build/reference/eh-exception-handling-model.md)。

## <a name="example"></a>示例

以下示例生成 C4530：

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

使用 编译示例**`/EHsc`** 以解决警告。
