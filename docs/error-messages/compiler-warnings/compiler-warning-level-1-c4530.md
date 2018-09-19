---
title: 编译器警告 （等级 1） C4530 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbfbc67377dd48eeb692bdd4cac1f113fbdf7f6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110453"
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530

C + + 异常处理程序使用，但展开语义未启用。 指定 /EHsc

使用 c + + 异常处理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)未选中。

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