---
title: 编译器错误 C2655 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2655
dev_langs:
- C++
helpviewer_keywords:
- C2655
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 456fd31e6d618774bff13c9800d6a44ffd3deb73
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078681"
---
# <a name="compiler-error-c2655"></a>编译器错误 C2655

identifier： 定义或在当前作用域中的非法重新声明

可以仅在全局范围内重新声明标识符。

下面的示例生成 C2655:

```
// C2655.cpp
class A {};
class B {
public:
   static int i;
};

int B::i;  // OK

int main() {
   A B::i;  // C2655
}
```