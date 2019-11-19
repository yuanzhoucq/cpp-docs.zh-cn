---
title: 编译器警告（等级1） C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 3139d321bca64b9938badebdabccd3ca1eb96d11
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966263"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级1） C4530

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