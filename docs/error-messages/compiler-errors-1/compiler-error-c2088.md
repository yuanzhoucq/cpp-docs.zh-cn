---
title: 编译器错误 C2088 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2088
dev_langs:
- C++
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75281567b0e4419303607bf90a479ff628e8abf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096868"
---
# <a name="compiler-error-c2088"></a>编译器错误 C2088

operator： 非法的 class-key

没有为结构或联合定义运算符。 此错误仅是有效的 C 代码。

下面的示例生成 C2088 三次：

```
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```