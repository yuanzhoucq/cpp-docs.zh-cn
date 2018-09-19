---
title: 编译器警告 （等级等级 4)c4740 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4740
dev_langs:
- C++
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6353ac464d95e8805a9c9e55488a355f71372508
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056141"
---
# <a name="compiler-warning-level-4-c4740"></a>编译器警告（等级 4）C4740

工作流中或出内联 asm 代码会取消全局优化

当在跳转或向外`asm`块中，该函数禁用全局优化。

下面的示例生成 C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```