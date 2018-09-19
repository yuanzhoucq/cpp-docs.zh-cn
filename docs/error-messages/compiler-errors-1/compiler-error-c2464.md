---
title: 编译器错误 C2464 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff74085364d6638772ab2376aace93fea741056b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103134"
---
# <a name="compiler-error-c2464"></a>编译器错误 C2464

identifier： 不能使用 new 分配引用

引用标识符已分配与`new`运算符。 引用不是内存对象，因此`new`无法返回一个指针指向它们。 使用标准的变量声明语法声明的引用。

下面的示例生成 C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```