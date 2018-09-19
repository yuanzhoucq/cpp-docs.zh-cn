---
title: 编译器错误 C2469 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2469
dev_langs:
- C++
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7f9a8a8a25190163432d5f0dd7826840e7ef7c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076900"
---
# <a name="compiler-error-c2469"></a>编译器错误 C2469

“operator”: 无法分配“type”对象

向运算符传递了一个无效类型。

下面的示例生成 C2469：

```
// C2469.cpp
int main() {
   int *i = new void;   // C2469
   int *i = new int;   // OK
}
```