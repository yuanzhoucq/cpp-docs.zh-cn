---
title: 编译器警告（等级 1）C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160713"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530

C++异常处理程序使用，但展开语义未启用。 指定 /EHsc

C++使用异常处理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)未选中。

如果尚未启用 /EHsc 选项，将不会销毁具有自动存储在框架中，执行引发函数捕捉引发，与函数之间的对象。 但是，在创建具有自动存储区对象**尝试**或**捕获**块将被销毁。

下面的示例生成 C4530:

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

编译该示例使用 /EHsc 要解决此警告。