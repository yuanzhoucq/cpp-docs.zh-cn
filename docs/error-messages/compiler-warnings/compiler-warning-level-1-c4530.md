---
title: 编译器警告（等级 1）C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 69ca60e2cba338bf1bd1ac3470e583739e72a68e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186447"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530

C++使用了异常处理程序，但未启用展开语义。 指定/EHsc

C++使用了异常处理，但未选择[/ehsc](../../build/reference/eh-exception-handling-model.md) 。

如果尚未启用/EHsc 选项，则不会销毁帧中具有自动存储的对象、执行引发的函数和捕获引发的函数。 但会销毁在**try**或**catch**块中创建的自动存储的对象。

下面的示例生成 C4530：

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

用/EHsc 编译示例以解决此警告。
